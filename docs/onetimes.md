# Onetimes

## What are Onetimes?

With Onetimes, customers can add on a single item to their purchase, in addition to ongoing subscriptions. This resource allows creation of a one time product “upsells” onto the Customers resource. Customers are only charged once for a onetime.

### Scopes
|Scope|Description|
|-|-|
|`read_subscriptions`|Required to read the onetimes resource.|
|`write_subscriptions`|Required write to onetimes resource.|


<!--
type: tab
title: Create a onetime
-->
`POST` to `/addresses/:address_id/onetimes`

```json
{
  "next_charge_scheduled_at": "2018-12-17",
  "price": 9,
  "product_title": "SuperKiwi ONETIME",
  "properties": [
    {
      "name": "grind",
      "value": "drip"
    },
    {..}
  ],  
  "quantity": 1,
  "shopify_variant_id": 3844892483
}
```

<!--
type: tab
title: Create a onetime
-->

<!-- type: tab-end -->

## Resources
[Onetimes reference](https://developer.rechargepayments.com/#onetimes)