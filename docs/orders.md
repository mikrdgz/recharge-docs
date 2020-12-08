# Orders

## What is an Order?
An order is created in ReCharge after a [Charge](https://developer.rechargepayments.com/#charges) is successfully processed. Orders contain information about the product ordered such as the SKU, the corresponding ReCharge subscription ID for the order, and IDs for a corresponding order on external ecommerce platforms. 

The orders resource contains some information about the shopper. However, see [Addresses](https://developer.rechargepayments.com/#addresses) and [Customers](https://developer.rechargepayments.com/#customers) for detailed billing information.

An order contains all the same JSON data as the charge. In case of a prepaid order creation, the order will be queued for a particular date and submitted on that date to the external ecommerce platform.

## Scopes

|Scope|Description|
|-|-|
|`write_orders`| Required to write to the customer record.|
|`read_orders`| Required to read customer record.|


## Line Items
You ccan update `line_item` properties on Prepaid Queued Orders. To change Queued Charges, you must change the parent subscription(s) or address.

When updating `line_items` you must provide the entire JSON that was in line_items before, as the data provied overrides the entire block and only new parameters will remain.

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