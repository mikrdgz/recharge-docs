# Orders

## What is an Order?
An order is created in ReCharge after a [Charge](https://developer.rechargepayments.com/#charges) is successfully processed. Orders contain information about the product ordered such as the SKU, the corresponding ReCharge subscription ID for the order, and IDs for a corresponding order if one is created on an external ecommerce platform. 

The orders resource contains some information about the shopper. See [Addresses](https://developer.rechargepayments.com/#addresses) and [Customers](https://developer.rechargepayments.com/#customers) for detailed billing information.

An order contains all the same JSON data as the charge. In case of a prepaid order creation, the order will be queued for a particular date and submitted on that date to the external ecommerce platform. 

## Scopes
|Scope|Description|
|-|-|
|`write_orders`| Required to write to the customer record.|
|`read_orders`| Required to read customer record.|


## Line Items
You can only update `line_item` properties directly on the Orders object if it is a [prepaid queued order](https://support.rechargepayments.com/hc/en-us/articles/360008682674-Converting-a-subscription-from-monthly-to-prepaid-). These items have been paid ahead of time by the customer but are set to be delivered on a recurring cycle.

To update an Order's `line_items`, you must update the corresponding [Subscription](https://developer.rechargepayments.com/?shell#subscriptions), which will then generate a new [Charge](https://developer.rechargepayments.com/?shell#charges). You must make changes to the Order `line_items` this way because the values of this property are inhereted from the Charge model.

<!-- theme: warning -->
> When updating `line_items` you must provide the entire JSON that was in `line_items` before, as the data provied overrides the entire block and only new parameters will remain.

## Use cases


<!-- theme: warning -->
> ### Deprecated fields
>These fields are deprecated, however they will not be removed from this API version:
>
>|Deprecated field|Alternative|
>|-|-|
>|`product_title`|`title`|
>|`shipping_date`|`scheduled_at`|
>|`shopify_id`|`shopify_order_id`|
>|`address_is_active`|Ignore, field not applicable|

## Resources
[Orders Reference](https://developer.rechargepayments.com/?shell#orders)