# Subscriptions
## What is a Subscription?
Subscriptions represent individual items a shopper receives on a recurring basis. Subscriptions are the core resources of the ReCharge API, as . A subscription record is comprised of a product added to an address. 

You can update the date a customer will be charged, the date when an order is created, and how frequently a product will be shipping using the Subscriptions resource.

A customer can only have one subscription of the same product on one address. Customers can have multiple subscriptions of the same product but only if those subscriptions are attached to a different [Address](https://developer.rechargepayments.com/?shell#update-an-address).

## Scopes
|Scope|Description|
|-|-|
|`write_subscription`| Required to write to the subscriptions record.|
|`read_subscriptions`| Required to read subscriptions record.|


## Shopify and multi-product Subscriptions
If store owner wants to sell multiple products as one subscription on 1 address it can be done by creating a product in Shopify that consists of multiple products e.g. 3 types of vegetables in the box, set of different shirts, etc. This multiple products appear on the store as 1 product, therefore it can be sold in a single subscription to 1 or more addresses.



<!-- theme: info -->
> Previously products needed to be attached to a ruleset, but we've deprecated [rulesets](https://support.rechargepayments.com/hc/en-us/articles/360008830873-Creating-subscription-rulesets)