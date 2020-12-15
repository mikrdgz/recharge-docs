# Add a one-time gift to an existing subscription
This document will walk you through the steps you application should take to add a one-time item to a subscription. One use case for this is adding a free gift as part of a subscription.

1. Create a [product in Shopify](https://shopify.dev/docs/admin-api/rest/reference/products) and set its price and weight to 0.
2. Create a one-time product by making a `POST` call to our [Onetimes resource](https://developer.rechargepayments.com/?ruby#the-onetime-object).
3. Sset the `next_charge_scheduled_at` and `address_id` as they are in the subscription on which you want to add a one-time gift.

The one-time item is now added to the next charge of the subscription.
