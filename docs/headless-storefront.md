# Storefront

You will create the ReCharge subscription widget customers interact with when you integrate with ReCharge using our API. This is the storefront component. This article will cover high-level considerations for integrating ReCharge subscriptions with your own custom frontend. 

## CDN

We provide you with a CDN URL that lets you retrieve all ReCharge product data client-side. This is a powerful tool and can speed up your development process eliminating the need to create a data layer to interact with product information as customers interact with your storefront.

### Setup

Add the CDN script to needed pages. If you're using a frontend templating engine, adding it to the base HTML file is a good idea. We will provide you with a unique store hash you will add to the script URL.

`<script src="https://platform-data-prod.rechargeadapter.com/<STORE_HASH>/<STORE_HASH>-data.js"></script>`


## ReCharge data object

Once you've made the CDN URL available on desired pages you will have access to the `RCA_DATA` object that contains three child objects:

- `RCA_FILE_DATA`
- `RCA_STORE_DATA`
- `RCA_PRODUCT_DATA`

The `RCA_FILE_DATA` and `RCA_STORE_DATA` objects contain meta information about the script itself and your store. You'll mainly target the `RCA_PRODUCT_DATA` array which contains information about products in the store. You can surface this information on the storefront in ways you see fit. See [Frontend functionality](fe-functionality.md) for guidance on styling ReCharge CSS elements.

### Example `RCA_DATA` object

```json
{
  "RCA_FILE_DATA": {
    "updated_at": 1611704163,
    "version": 1
  },
  "RCA_STORE_DATA": {
    "rc_domain": "<store_domain>",
    "hash": "<store_hash>",
    "weight_units": ""
  },
  "RCA_PRODUCT_DATA": [
    {
      "id": 0,
      "weight": null,
      "variants": [],
      "discounts": [],
      "subscriptions": [
        {
          "discount_amount": 5,
          "discount_type": "percentage",
          "charge_interval_frequency": 1,
          "order_interval_unit": "month",
          "storefront_purchase_options": "subscription_and_onetime",
          "expire_after_specific_number_of_charges": null,
          "order_interval_frequency_options": [
            "1",
            "2",
            "3",
            "4"
          ]
        }
      ],
      "tax_code": null
    }
  ]
}
```

