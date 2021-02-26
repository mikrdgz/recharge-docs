# Product Resource

The [Products resource](products.md) is where subscription rules for items are stored. This information includes the delivery frequency offered for that product, any discounts tied to the item and the intervals at which customers can receive the item (weekly, monthly, etc.).

You can set more complex rules for subscriptions, such as the number of charges until a subscription expires and more using the Products endpoint. For a comprehensive overview, see [Products](products.md)

**Example of the Product object**

```json
{
  "product": {
    "id": 1327844,
    "collection_id": null,
    "created_at": "2019-11-07T11:36:19",
    "discount_amount": 10.0,
    "discount_type": "percentage",
    "handle": null,
    "images": {
      "large": "https://cdn.shopify.com/s/files/1/0683/1951/products/t_shirt_large.jpg",
      "medium": "https://cdn.shopify.com/s/files/1/0683/1951/products/t_shirt_medium.jpg",
      "original": "https://cdn.shopify.com/s/files/1/0683/1951/products/t_shirt.jpg",
      "small": "https://cdn.shopify.com/s/files/1/0683/1951/products/t_shirt_small.jpg"
    },
    "product_id": 4354268856408,
    "shopify_product_id": 4354268856408, // In the future, this parameter will have a non-platform-specific name
    "subscription_defaults": {
      "charge_interval_frequency": 1,
      "cutoff_day_of_month": null,
      "cutoff_day_of_week": null,
      "expire_after_specific_number_of_charges": null,
      "modifiable_properties": [
        "name",
        "quantity",
        "size",
        "color"
      ],
      "number_charges_until_expiration": null,
      "order_day_of_month": null,
      "order_day_of_week": null,
      "order_interval_frequency_options": [
        "1",
        "6",
        "12"
      ],
      "order_interval_unit": "month",
      "storefront_purchase_options": "subscription_only"
    },
    "title": "T-shirt",
    "updated_at": "2019-11-07T11:36:19"
  }
}
```

### Resources

- [Products API reference](https://developer.rechargepayments.com/#products)