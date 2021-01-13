# JavaScript Interfaces

ReCharge exposes several JavaScript interfaces on the frontend to provide programmatic access to processes that power subscription functionality. The interfaces are accessible as a global variable which organizes all options:

**Global Variable:**
`RCAInterface`

BigCommerce stores with the ReCharge Subscriptions application installed have interfaces available with no additional setup needed.

## Available Interfaces


## Example Use
To use an interface ensure that the application script has loaded, then access any method described in the Interface specifications (see Available Interfaces above).

```js
$( document ).ready(function() {
  RCAInterface.checkout.performCheckout()
});
```
## Cart
|Name|Arguments|Returns|Description|
|-|-|-|-|
|`hasSubscription`|Object `cart_data` (optional) | Promise `boolean`|Checks whether the current BigCommerce cart has subscriptions in it.|
|`currentCart`|None|Promise `JSON`|(**Not Implemented**) Gets the current cart from the BigCommerce API and implements JSON.|
|`cartTotal`|None|Promise `number`|Returns the `total_price` field for the current cart.|
|`itemPrice`|String `line_id`|Promise `number`|Returns an item price for a cart line item with the subscription discount factored in.|

## Checkout Methods

|Name|Arguments|Returns|Description|
|-|-|-|-|
|`performCheckout`|None|Promise `boolean`| Performs a ReCharge checkout. Creates payload and navigates browser to checkout page.|
|`createPayload`|Object bc_cart_data, Object subscription_data|Object|Creates a ReCharge checkout payload from BigCommerce cart data and adapter subscription data.|
|`submitCheckout`|Object checkout_payload|None|**Not Implemented**|

### Example

**Full Checkout On-Click**

```js
// Method 1
RCAInterface.cart.hasSubscription().then(response => response ? RCAInterface.checkout.performCheckout() : window.location.assign('/checkout.php'))

//Method 2
$('#checkout_button').on('click', function(event) {
    RCAInterface.cart.hasSubscription().then(response => {
        if (response) {
            event.preventDefault();
            RCAInterface.checkout.performCheckout()
        }
    })
});
```

## Subscription Methods
|Name|Arguments|Returns|Description|
|-|-|-|-|
|`addSubscription`|Object subscription_data|Promise `boolean`|Saves a subscription for a BigCommerce cart line.|
|`removeSubscription`|String cart_id, String line_id|Promise `boolean`| Removes a subscription for a BigCommerce cart line.|
|`updateSubscription`|Object subscription_data|Promise `boolean`| Updates an existing subscription for a BigCommerce cart line.|
|`getSubscriptions`|String cart_id (optional), String line_id (optional)|Object|Returns subscription data filtered by `cart_id` and `line_id`. If neither argument is provided, returns subscriptions for the current cart.|

## Object Data Structure

### Subscription Data
`subscription_data`

### Description/Format

```json {
  cartid: String,             // BigCommerce Cart id
  line_item: String,          // BigCommerce Cart line_id
  shipping_unit: String,      // ReCharge Product order_interval_unit
  shipping_frequency: Number, // ReCharge Product order_interval_frequency
  charge_frequency: Number,   // ReCharge Product charge_interval_frequency
  discount_type: String,      // ReCharge Product discount_type ("percentage")
  discount_amount: Number,    // ReCharge Product discount_amount
}
```
### Cart Data
`cart_data`

### BigCommerce Cart Data
`bc_card_data`

### Checkout Payload
`checkout_payload`

