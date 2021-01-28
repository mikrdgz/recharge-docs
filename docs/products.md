# Products
## What is a Product?
Products are the items tied to a subcription in ReCharge. If using an external catalog such as Shopify or BigCommerce, the Product resource contains information about the item in remote catalog.

Within the product resource, you can set the charge frequency for that item, the day in a month that to charge a customer, and more.

## Subscriptions and products

In the ReCharge Control Panel you can create rulesets that contain the subscription settings for products.It is best practice to forego passing the `collection_id` and instead set the following fields when creating products via API, as rulesets will one day be deprecated. The following fields are required: `charge_interval_frequency`, `order_interval_frequency_options`, `order_interval_unit` and `storefront_purchase_options`.

|Property|Required|Value|Note|
|-|-|-|
|`charge_interval_frequency`|Required if item is prepaid|• Min value: 1 <br> • Max value: 999||
|`cutoff_day_of_month`|Optional|• Min value: 1<br>• Max value: 31|`shipping_interval_unit` must be equal to "month"|
|`cutoff_day_of_week`|Optional|• Min value: 0 (Monday)<br>• Max value: 6 (Sunday)|`order_interval_unit` must be equal to "week".|
|`discount_type`|Optional||Valid option is only "percentage"|
|`order_day_of_month`|Optional||No default. Only applicable when `order_interval_unit` = “month”.|
|`order_day_of_week`| Optional|Value of 0 equals Monday, 1 equals Tuesday, etc.|Only applicable when `order_interval_unit` = “week”.|
|`order_interval_frequency_options`|Required|Must be list of integers or integers that are individual strings|Each integer/string must be greater than 0 and less than 999|
|`order_interval_unit`|Required|Valid values are “day”, “week”, and “month||
|`shopify_product_id`|Required|||
|`storefront_purchase_options`|Required||Valid options are “subscription_only” or “subscription_and_onetime”.|