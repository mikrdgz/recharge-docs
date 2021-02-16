# Subscriptions
## What is a Subscription?
Subscriptions represent individual items a customer receives on a recurring basis. Subscriptions are the core resources of the ReCharge API. A subscription record is comprised of a product added to an address. 

You can update the start date that a customer will first charged and the frequency of each charge, the date of the month when an order is created, and the product's shipping frequency using the Subscriptions resource.

A customer can only have one subscription of the same product on one address. Customers can have multiple subscriptions of the same product but only if those subscriptions are attached to a different [Address](https://developer.rechargepayments.com/?shell#update-an-address).

<!-- theme: info -->
> In the past products needed to be attached to a ruleset to be added to subscriptions, but we are in the process of deprecating [rulesets](https://support.rechargepayments.com/hc/en-us/articles/360008830873-Creating-subscription-rulesets).

### Scopes
|Scope|Description|
|-|-|
|`read_subscriptions`| Required to read subscriptions record.|
|`write_subscription`| Required to write to the subscriptions record.|

## Updating a Subscription
If you want to change any of the following attributes, you must update all of them because they are tied to one another:

- `order_interval_unit`
- `order_interval_frequency`
- `charge_interval_frequency`

To change the `next_charge_date`, we recommend changing the attributes in the list above. Making changes to these, or the `frequency` attribute will prompt our algorithm to recalculate the `next_charge_date`. 

<!--theme: info-->
> When updating subscription `status` attribute from “CANCELLED” to “ACTIVE”, the following attributes will be set to `null`: `cancelled_at`, `cancellation_reason` and `cancellation_reason_comments`

### Request limit

When updating Subscriotions in bulk, there is a limit of 20 subscriptions per request.

## Deleting a Subscription
If a user deletes a subscription via the ReCharge UI, you will still be able to retrieve it using the Subscriptions API. Deleting a Subscription via API is the only way to completely remove a subscription record from the database. 

## Shopify and Subscriptions

A store owner can bundle multiple products as one subscription with one address. To do this, [create a product in Shopify](https://shopify.dev/docs/admin-api/rest/reference/products/product#create-2020-10)
that consists of multiple variants e.g. a box of multiple types of vegetables or a 3-pack of t-shirts. The Shopify variants will appear on the store as one product that can be sold in a single subscription to one or more addresses.

When swapping a Shopify product in a Subscription with the `shopify_variant_id` attribute, you must include `price`, `sku`
,`variant_title`, `product_title` as they are not automatically overriden by the new item's data. Set the `use_shopify_variant_defaults` value to `true` if you want to update these attributes with the corresponding values from the Shopify product.

<!-- theme: info-->
> A swapped Subscription cannot have a different order interval different than the associated charge (pre-payment) nor a Onetime.

## Delay a Charge regeneration
You can now delay subscription charge regenerations.

Each subscription update triggers a charge regeneration. This can be time consuming if your application is performing multiple updates in sequence. Use `commit_update: false` in the body of your Subscriptions `PUT` request to perform this action more quickly. Doing so will delay charge regeneration by 5 seconds. This allows you to run multiple calls to perform changes much faster because your application does not need to wait for every charge regeneration to complete between requests and responses. 

<!-- theme: info-->
> - For extra safety, we make sure that if a charge is processed before we the regeneration resolves, we will auto-trigger the regeneration before processing.
> - If you want to trigger the regeneration yourself, simply exclude the `commit_update` parameter and it will default to `true`. You may also include it and set it to `true`.

## Resources
- [Subscriptions reference](https://developer.rechargepayments.com/?php#subscriptions)
- [Shopify API Product reference](https://shopify.dev/docs/admin-api/rest/reference/products/product)
