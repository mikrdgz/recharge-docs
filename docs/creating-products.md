# Creating a Product

To sell products using ReCharge you must first create these items in our system. This guide outlines how to create products via API Integration. 

## Creating the Product Catalog entry

First, create an entry for the item in the Product Catalog. The product catalog is where information about the product, such as price, weight and SKU, is stored in ReCharge.

### Creating a product in the product catalog example

`POST` to `/catalog/products`

```json
{
    "id":999999, //The ID of the product in your system
    "title":"My Cool Product", //The title for display of the product
    "handle":"cool-product", //A shortened URL-safe slug for the product
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

## Creating Products via Merchant Portal
Once you've created the item in the Product Catalog, you can tie ReCharge subscription rules to the items. Do this by creating entries on the Products Resource.

You can create entries on the Products Resource manually via the [Merchant Portal](https://support.rechargepayments.com/hc/en-us/articles/360008830873-Creating-subscription-rulesets), if desired. This method reduces the steps your app will need to take to begin offering subscriptions.

## Creating Products via API
You can create a Product Resource entry programmatically if this method fits with your workflow. Use our Products API to accomplish this. See the example below for details.

### Creating a Products Resource entry

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