# Creating buy one, get one promotions
## Overview

Buy one/get one promotions, or BOGO promotions as they are colloquially referred to, commonly entail adding a free item to the cart in tandem with a subscription purchase. These are usually offered to encourage customers to try other items they might not have yet, as well as to entice the customer to sign up for recurring orders.

We will outline two popular methods to incorporate BOGO into your store:

• Add BOGO item to cart during checkout
• Add BOGO item during subscription renewal

In this example, we show how to automatically pass a BOGO item to the cart along with a subscription product, after it is added by the customer. 

> Note
> This feature is only available for Shopify merchants who installed ReCharge before November 2nd, 2020, and are using the [ReCharge Checkout](https://support.rechargepayments.com/hc/en-us/articles/360008681834-Identifying-which-checkout-is-in-use).

## Add BOGO item to cart during checkout 

The main focus of this section is how to leverage jQuery/AJAX to add a hidden free item to the cart in tandem with a subscription product.

### Before you start
- This implementation will require advanced Javascript, HTML, Shopify Liquid, and API knowledge. This is not part of ReCharge's turnkey solution. If you are a merchant looking to implement a BOGO offering on your ReCharge store, we recommend reaching out to a [ReCharge Expert](https://recharge.partnerpage.io/). 
- This is an example implementation using the Shopify Minimal Theme. While many themes are similar, the exact file names and location of code blocks could differ depending on your chosen theme.
- This guide details the most basic implementation of BOGO approaches. Any further customizations will require the advice of a [ReCharge Expert](https://recharge.partnerpage.io/). 

## Step 1: Set up products in Shopify
Create all of the products involved in the BOGO use case. This means both the items available for subscription purchase, as well as the qualifying BOGO items to be added in tandem with them. 

## Step 2: Edit the product template file
Adding to the built in “add-to-cart-button” code is necessary to ensure that the items are both added at once. With that, we are going to open the “sections/product-template.liquid” file, and add the following AJAX code block that will layer on top of the existing add to cart button functionality. It is important to locate the add to cart button code and paste the logic directly below it. For the purposes of this demonstration, you can find it on line 218 in the above listed file.

### Create a function to handle automatically adding the BOGO item to the cart 
The function takes two arguments so that the cart data is updated with the required variant ID and quantity. These two are paramount to the logic as otherwise, the code block wouldn’t know what to add upon click. In this example, we are passing the Shopify Variant ID of the BOGO item. If you need assistance locating a Shopify Variant ID, they have a great guide here: Find a Shopify Variant ID

After the data is defined, we issue a POST call to append the data to the cart and finally send a success response based on the cart URL. 

### Call the add to cart function
Once you have your add to cart function, you will need to create one more to ensure that the function is initiated. In order to do this, we need two pieces - the first is to make sure that the entire page is loaded before the code can fire and the second is to add an jQuery listener to the add to cart button, so that once it is selected by the user, the logic we added to append the extra data will trigger. 

The most important piece with this code section is to make sure you add the listener to the add to cart button HTML ID. In this example’s case, it is “add-to-cart-button”. All IDs are called with the hash symbol appended to the front as well. Right after, we’ll also look for the original Shopify product ID to ensure the BOGO item is only added if the qualifying item in the catalog is added first.

### Full code
<script> 
$(document ).ready(function (){
  $(document ).on( "click", "#add-to-cart-button",function(){
  if ({{ product.id }} == <ORIGINAL_SHOPIFY_PRODUCT_ID>){
     addItemToCart(<BOGO_ITEM_VARIANT_ID>, 1);
  }
  });
});
</script>
<script>          
  function addItemToCart(variant_id, qty) {
    data = {
      "id": variant_id,
      "quantity": qty,
    }
    jQuery.ajax({
      type: 'POST',
      url: '/cart/add.js',
      data: data,
      success: function() { 
        window.location.href = '/cart'; 
      }
  }
</script> 

## Add BOGO item during subscription renewal
The main focus of this section is how to leverage ReCharge’s API to add a hidden free item to the second order in a recurring schedule. We implemented our functions via Node as a Google Cloud Platform serverless function. You will need to adapt the code to fit whatever platform or service you are using to consume the webhooks we create. We also use the request-promise package to handle the calls to the ReCharge API.

## Step 1: Create a ReCharge API token
Once ReCharge is installed, you will want to create an API token to be used when you make calls to the ReCharge API. Please refer to API Token Creation on how to create your ReCharge token.

When generating the token, you will need to set permissions to specific ReCharge objects. We recommend setting all of the permissions to Read/Write access aside from "Store Information" which can currently only be set to Read access 

## Step 2: Create a function to handle adding the one-time item to the second overall future charge

This function will trigger off of a ReCharge webhook response, and you will pass the address ID and next charge date as arguments. The reason these need to be passed is that in order to add a one-time item to a future order, the request call requires the address ID and next charge date of the existing subscription. 

First, we are going to define the next charge date value so that we can restrict the received string to 10 characters. The reason this is necessary is that the create one time endpoint accepts a different value than is generated in the webhook response. Next, make a POST call to the ReCharge API along with an address ID variable which we are going to define in the next function. and next charge date values that you will grab from the webhook response.

The last part of this function is to dictate the body. Because we are using javaScript for this API logic, we will be using the dependency ‘body’ as opposed to ‘data’ we normally see with Python. Because the content is passing the body dependency, we also need to be sure to turn the JSON passed into a string so that the API can read the request. 

In the body object, we are going to be passing the next charge date variable we defined right after opening up the function, the product title, price, quantity, Shopify Variant ID of the BOGO item, and properties if applicable. 

### Step 3: Create the main function to execute the code and register the webhook as received

This function defines the required parameters and initiates the creation of the one-time item by calling its respective function as well. We’ll call this one "main" since it will drive the logic for the end goal of adding the item to a future charge. 

First we’ll open the function up and pass the request and result as arguments. Next, we’ll define the body of the request so that we can more easily define and call the required parameters. Once we define the request body, we’ll also define the Shopify Variant ID. In this case, it should be the Shopify Variant ID of the qualifying recurring item that was purchased via the checkout. 

Next we’ll look for the Shopify Variant ID via an if statement so that if the item wasn’t purchased, we do not create a one time item in the future charge. If the qualifying item fits the Shopify Variant ID value, we’ll then define the address ID, next charge date, and result values. We’ll close the if portion of the conditional statement by calling the result to the console. Contrastingly, the else statement will then simply log that there was no qualifying item in the console, if the Shopify Variant ID isn’t part of the request return. 

Finally, exit the function and return a `200` response to the webhook.

```js
require('request');
var request = require('request-promise');

//ReCharge API Token
var rechargeApiToken = "<ReCharge API Token>",

//create one time bogo on future order
function  createOneTimeBogo (addressID, nextChargeDate){
  var oneTimeCharge = nextChargeDate.substring(0,10);
  return request ({
    "method": "POST",
    "uri":  "https://api.rechargeapps.com/onetimes/address/" + addressID,
    "headers": {
      "X-Recharge-Access-Token": rechargeApiToken,
      "Accept":"application/json",
      "Content-Type":"application/json"
    },
    "body": JSON.stringify({
          "next_charge_scheduled_at": oneTimeCharge,
          "product_title":"Standard Bogo",
          "price":0,
          "quantity":1,
          "Shopify_variant_id":"<BOGO-VARIANT-ID>”,
          "properties": []
    }),
  });
};
exports.main = (req, res) => {

    var sub = req.body.subscription;

    var ShopifyVariantID = sub.shopify_variant_id || null;

    if (ShopifyVariantID == "<RECURRING-ITEM-VARIANT-ID>) {
      var addressID = sub.address_id;
      var nextChargeDate = sub.next_charge_scheduled_at;
      var result = createOneTimeBogo(addressID, nextChargeDate);
      console.log(result);
    }
    else {
      console.log("No qualifying recurring item");
    }
    res.status(200).send("Webhook Received");
  };
```

## Step 4 - Register your webhook
Now that you have your function to add the one-time item to a future charge, you will need to register the webhooks that will trigger the function. This implementation requires a registration to the ‘subscription/created’ webhook, as it is only triggered off of checkout and/or direct API created subscriptions. Refer to the ReCharge API Documentation for a description of these webhooks, if needed. You can use the provided JavaScript script below as a template to create these webhooks, but please use your own internal guidelines for registering webhooks.

```js
require('request');
var request = require('request-promise');
var rechargeApiToken = "<ReCharge API Token>",

request ({
    "method": "POST",
    "uri":  "https://api.rechargeapps.com/webhooks",
    "headers": {
      "X-Recharge-Access-Token": rechargeApiToken,
      "Accept":"application/json",
      "Content-Type":"application/json"
    },
    "body": JSON.stringify({
          "address": "insert trigger address",
          "topic": "webhook looking to connect to"
    }),
  });
  ```

## Summary
If you have followed the guide step-by-step, you will have created:

- A front-end that can add a one-time BOGO item to the cart in tandem with a recurring item and automatically/behind the scenes.
- A back-end that can add one-time items to future charges based on a specific Shopify Variant ID. 