# Creating a Product

You can take the following steps to create products in ReCharge.

### Creating products manually
You can create products manually via the [Merchant Portal](https://support.rechargepayments.com/hc/en-us/articles/360008830873-Creating-subscription-rulesets), if preferred. Doing so will reduce the steps your app will need to take to begin offering ReCharge subscriptions via API.

### Creating products via API

1. Create the product in the ReCharge product catalog using the `/catalog/` endpoint.
2. Next, create subscription rules for the item using our Products API.

### Creating a product in the product catalog example

`POST` to `/catalog/products`

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
### Creating a Products resource entry

`POST` to `/products`

```json
{
  "discount_amount": 10.0,
  "discount_type": "percentage",
  "shopify_product_id": 4354268856408, // in the future, this property will have a non-platform-specific name
  "subscription_defaults": {
    "charge_interval_frequency": 1,
    "modifiable_properties": [
      "color"
      "name",
      "quantity",
      "size",
    ],
    "order_interval_frequency_options": [
      "1"
    ],
    "order_interval_unit": "month",
    "storefront_purchase_options": "subscription_only"
  }
}
```