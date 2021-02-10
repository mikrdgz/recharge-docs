# Managing Products

## Overview
Products are the core of ReCharge subscriptions. All catalog data is stored within the [Products Resource](docs/products.md) and is where we you will find information about subscriptions offered for an item including its price, variants and images. ReCharge automatically syncs and maintains product catalog data between Shopify and BigCommerce via our direct integrations. This article provides guidance on maintaining product data between your own catalog and the ReCharge product catalog using your own API integration.

## Uses

The product catalog is used throughout the ReCharge application to provide product data for the following areas:

- Product widget
- Checkout
- Merchant Portal
- Customer Portal

## The "Product cache" versus "Products endpoint"

The ReCharge product cache is where data about each item in your external catalog is stored within our system. As a part of our turnkey integration, ReCharge pulls information such as price, variant, SKU etc. from either Shopify or BigCommerce into our product cache at the time a user creates a Product in the Control Panel.

When using the API Integration, these are the steps you should take to manually create products via the API

1. Create the product in the ReCharge product cache using the `/catalog/` endpoint
2. Then create the product the using our Products API, at which point defining subcription rules for that item.

### Creating a product in the product cache example

`POST` to `https://api.rechargeapps.com/catalog/products`

```json
{
    "id":999999, //The ID of the product in your system
    "title":"My Cool Product", //The title for display of the product
    "handle":"cool-product", //A shortened URL safe slug for the product
    "image":{
       "src":"https://url.for/image.png"
    },
    "images":[{
       "src":"https://url.for/image.png"
    }],
    "options": [],
    "variants":[{
        "id":999999, //The ID of the product in your system
        "price":11.99, //The list price of the product (before subscription discount)
        "product_id":999999, //The ID of the product in your system
        "sku":"testsku", //The SKU of the product in your system
        "taxable":true, //N/A if not using taxes
        "requires_shipping":true, //N/A if not using shipping
        "title":""
    }],
    "vendor":"Test",
    "published_at":"2020-01-01T00:00:00" // Required - anytime in the past is fine
}
```
> ### Note about /catalog/ endpoint
> The `/catalog/` endpoint is currently in beta. If you encounter an issue while using this resource, please contact ReCharge.

## Maintaining products in ReCharge using middleware

ReCharge stores all important information about a product's subscription options on the product resource. If you want to offer a subcription for a product, **you must create that product in ReCharge's catalog**. 

In a headless environment, you are responsible for syncing your external product catalog data into ReCharge. The best way to do this is by taking advantage of webhooks available on your existing platform and building a middlware controller that can receive webhooks payloads and then make appropriate changes to your catalog in ReCharge.

### Creating products manually
You can create products manually via the [Control Panel](https://support.rechargepayments.com/hc/en-us/articles/360008830873-Creating-subscription-rulesets), if preferred. Doing so will reduce the steps your app will need to take to begin offering ReCharge subscriptions via API.

## Maintaing products in ReCharge with a cron job
For custom ecommerce platforms or instances when your platform does not support webhooks, you will build an internal service  directly polls ReCharge's Product API for changes. This could be a cron job that runs at an interval to pull product data from your platform and sync it to ReCharge. The ideal outcome is your platform's product catalog is asynchronously synced with ReCharge's in near real-time. 

<!--!theme: warning -->

> ### Syncing products infrequently could cause unwanted results
> Customers may purchase or subscribe to outdated products if you do not push changes from your platform to ReCharge in a timely manner.

## Deleting products
There are several tasks the ReCharge platform performs automatically when store owners delete a product. If you're handling product deletions in your external app, consider the following:
- You will need to audit the [Subscriptions](https://developer.rechargepayments.com/#the-subscription-object) resource before deleting a product to ensure that the item isn't tied to active customer subscriptions. If the product you're deleting is part of a subscription, you should swap the item for another product, or cancel the customer's subscription. Migrate a different product to the cancelled subscription in case the customer chooses to reactivate.
- Audit upcoming [Orders](https://developer.rechargepayments.com/#orders) when deleting [Onetime](https://developer.rechargepayments.com/#onetimes) products to ensure none of the orders contain that item. You can swap the item or remove it from orders.

## Resources
[Products API Reference](https://developer.rechargepayments.com/#products)


