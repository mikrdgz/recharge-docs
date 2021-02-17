# Checkouts
|Scope|Description|
|-|-|
|`read_checkouts`| Required to retrieve a checkout.|
|`write_checkouts`| Required to modify or update checkout.|

## What is a Checkout?
You can use the Checkouts resource when creating subscription orders via our [API Integration](headless-overview.md) to compile and send an order to ReCharge for processing. Using this resource, you can also process a checkout via your own application only using the Checkouts resource to finalize payment. Normally, each of the separate API resources are updated as a customer goes through the out-of-the-box ReCharge checkiut workflow (customers, addresses, subcriptions, etc), but you can use the Checkouts resource to send all of this data to ReCharge in one call.

## Use cases
<!--
type: tab
title: Creating a Checkout
-->
`POST` to `/checkouts`

```json
'{
  "line_items": [
    {
      "charge_interval_frequency": 5,
      "cutoff_day_of_month": None,
      "cutoff_day_of_week": None,
      "expire_after_specific_number_of_charges": None,
      "fulfillment_service": "manual",
      "order_day_of_month": None,
      "order_day_of_week": None,
      "order_interval_frequency": 5,
      "order_interval_unit": "day",
      "product_id": <product_id>,
      "quantity": 6,
      "requires_shipping": True,
      "taxable": True,
      "variant_id": <variant_id>,
    }
  ],
}'
```

<!--
type: tab
title: Finalize processing checkout
-->

`POST` to `checkouts/:id/charge`

```json
{
  "payment_processor": "stripe",
  "payment_token": "<payment_token>",
  "payment_type": "CREDIT_CARD"
}
```

<!-- type: tab-end -->

## Resources
- [Checkouts reference](https://developer.rechargepayments.com/#checkouts)
- [ReCharge hosted checkout](recharge-hosted-checkout.md)