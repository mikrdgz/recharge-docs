# Subscriptions
## What is a Subscription?
Subscriptions represent individual items a shopper receives on a recurring basis. Subscriptions are the core resources of the ReCharge API, as . A subscription record is comprised of a product added to an address. 

You can update the start date that a customer will first charged and the frequency of each charge, the date of the month when an order is created, and the product's shipping frequency using the Subscriptions resource.

A customer can only have one subscription of the same product on one address. Customers can have multiple subscriptions of the same product but only if those subscriptions are attached to a different [Address](https://developer.rechargepayments.com/?shell#update-an-address).

### Scopes
|Scope|Description|
|-|-|
|`write_subscription`| Required to write to the subscriptions record.|
|`read_subscriptions`| Required to read subscriptions record.|

## Updating a Subscription

If you are making changes to any of the following parameters, you must update all of them because they are tied to one another.

- `order_interval_unit`
- `order_interval_frequency`
- `charge_interval_frequency`

## Shopify and multi-product Subscriptions

A store owner can bundle multiple products as one subscription with one address. To do this, [create a product in Shopify](https://shopify.dev/docs/admin-api/rest/reference/products/product#create-2020-10)
that consists of multiple variants e.g. a box of multiple types of vegetables or a 3-pack of t-shirts. The Shopify variants will appear on the store as one product that can be sold in a single subscription to one or more addresses.

<!-- theme: info -->
> Previously, products needed to be attached to a ruleset, but we're in the process of deprecating [rulesets](https://support.rechargepayments.com/hc/en-us/articles/360008830873-Creating-subscription-rulesets).

## Resources
- [Subscriptions reference](https://developer.rechargepayments.com/?php#subscriptions)
- [Shopify API Product reference](https://shopify.dev/docs/admin-api/rest/reference/products/product)
