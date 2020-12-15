# Auto-Expire Subscriptions
You can use the following code to auto-expire subscriptions.

`PUT` to  `/subscriptions/:id`

<!--
type: tab
title: cURL
-->

```cURL
curl -i -H "X-Recharge-Access-Token: your_api_token" \
-H "Accept: application/json" \
-H "Content-Type: application/json" \
-X PUT https://api.rechargeapps.com/subscriptions/<subscription_id> \
--data '{  "expire_after_specific_number_of_charges": 1}'
```

### Response

```json
{
  "subscription": {
    "address_id": 35079676,
    "cancellation_reason": null,
    "cancellation_reason_comments": null,
    "cancelled_at": null,
    "charge_interval_frequency": "12",
    "created_at": "2019-07-30T14:43:52",
    "customer_id": 31224521,
    "expire_after_specific_number_of_charges": 1,
    "has_queued_charges": 0,
    "id": 47529660,
    "is_skippable": null,
    "is_swappable": null,
    "max_retries_reached": 0,
    "next_charge_scheduled_at": null,
    "order_day_of_month": 0,
    "order_day_of_week": null,
    "order_interval_frequency": "12",
    "order_interval_unit": "month",
    "price": 5000,
    "product_title": "Test item  Auto renew",
    "properties": [
      {
        "name": "charge_interval_frequency",
        "value": "12"
      },
      {
        "name": "shipping_interval_frequency",
        "value": "12"
      },
      {
        "name": "shipping_interval_unit_type",
        "value": "Months"
      }
    ],
    "quantity": 1,
    "recharge_product_id": 1255996,
    "shopify_product_id": 2663712522325,
    "shopify_variant_id": 22958073806933,
    "sku": "",
    "sku_override": false,
    "status": "ACTIVE",
    "updated_at": "2019-07-31T08:04:00",
    "variant_title": ""
  }
}
```
<!--
type: tab
title: Python
-->

```python
import requests
import json

headers = {
  "X-Recharge-Access-Token": "your_api_token",
  "Accept": "application/json",
  "Content-Type": "application/json"
}
url = "https://api.rechargeapps.com/subscriptions/<subscription_id>"
data = {
  "expire_after_specific_number_of_charges": 1
}
```

### Response

```json
{
  "subscription": {
    "address_id": 35079676,
    "cancellation_reason": null,
    "cancellation_reason_comments": null,
    "cancelled_at": null,
    "charge_interval_frequency": "12",
    "created_at": "2019-07-30T14:43:52",
    "customer_id": 31224521,
    "expire_after_specific_number_of_charges": 1,
    "has_queued_charges": 0,
    "id": 47529660,
    "is_skippable": null,
    "is_swappable": null,
    "max_retries_reached": 0,
    "next_charge_scheduled_at": null,
    "order_day_of_month": 0,
    "order_day_of_week": null,
    "order_interval_frequency": "12",
    "order_interval_unit": "month",
    "price": 5000,
    "product_title": "Test item  Auto renew",
    "properties": [
      {
        "name": "charge_interval_frequency",
        "value": "12"
      },
      {
        "name": "shipping_interval_frequency",
        "value": "12"
      },
      {
        "name": "shipping_interval_unit_type",
        "value": "Months"
      }
    ],
    "quantity": 1,
    "recharge_product_id": 1255996,
    "shopify_product_id": 2663712522325,
    "shopify_variant_id": 22958073806933,
    "sku": "",
    "sku_override": false,
    "status": "ACTIVE",
    "updated_at": "2019-07-31T08:04:00",
    "variant_title": ""
  }
}
```
<!--
type: tab
title: Python
-->

```php
<?php

$request = new HTTP_Request();
$request->setUrl('https://api.rechargeapps.com/subscriptions/<subscription_id>');
$request->setMethod('HTTP_METH_PUT');

$request->setHeader(array(
  'content-type' => 'application/json',
  'X-Recharge-Access-Token' => 'your_api_token'
));

$request->setBody('{
  "expire_after_specific_number_of_charges": 1
}');

try {
  $response = $request->send();

  echo $response->getBody();
} catch (HttpException $ex) {
  echo $ex;
}
```
### Response

```json
{
  "subscription": {
    "address_id": 35079676,
    "cancellation_reason": null,
    "cancellation_reason_comments": null,
    "cancelled_at": null,
    "charge_interval_frequency": "12",
    "created_at": "2019-07-30T14:43:52",
    "customer_id": 31224521,
    "expire_after_specific_number_of_charges": 1,
    "has_queued_charges": 0,
    "id": 47529660,
    "is_skippable": null,
    "is_swappable": null,
    "max_retries_reached": 0,
    "next_charge_scheduled_at": null,
    "order_day_of_month": 0,
    "order_day_of_week": null,
    "order_interval_frequency": "12",
    "order_interval_unit": "month",
    "price": 5000,
    "product_title": "Test item  Auto renew",
    "properties": [
      {
        "name": "charge_interval_frequency",
        "value": "12"
      },
      {
        "name": "shipping_interval_frequency",
        "value": "12"
      },
      {
        "name": "shipping_interval_unit_type",
        "value": "Months"
      }
    ],
    "quantity": 1,
    "recharge_product_id": 1255996,
    "shopify_product_id": 2663712522325,
    "shopify_variant_id": 22958073806933,
    "sku": "",
    "sku_override": false,
    "status": "ACTIVE",
    "updated_at": "2019-07-31T08:04:00",
    "variant_title": ""
  }
}
```

<!--
type: tab
title: Ruby
-->

```ruby
require 'uri'
require 'net/http'
require 'openssl'
require 'rubygems'
require 'json'

url = URI("https://api.rechargeapps.com/subscriptions/<subscription_id>")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Put.new(url)
request["X-Recharge-Access-Token"] = 'your_api_token'
request["content-type"] = 'application/json'

request.body = {
  "expire_after_specific_number_of_charges": 1 
}.to_json

response = http.request(request)
puts response.read_body
```

### Response

```json
{
  "subscription": {
    "address_id": 35079676,
    "cancellation_reason": null,
    "cancellation_reason_comments": null,
    "cancelled_at": null,
    "charge_interval_frequency": "12",
    "created_at": "2019-07-30T14:43:52",
    "customer_id": 31224521,
    "expire_after_specific_number_of_charges": 1,
    "has_queued_charges": 0,
    "id": 47529660,
    "is_skippable": null,
    "is_swappable": null,
    "max_retries_reached": 0,
    "next_charge_scheduled_at": null,
    "order_day_of_month": 0,
    "order_day_of_week": null,
    "order_interval_frequency": "12",
    "order_interval_unit": "month",
    "price": 5000,
    "product_title": "Test item  Auto renew",
    "properties": [
      {
        "name": "charge_interval_frequency",
        "value": "12"
      },
      {
        "name": "shipping_interval_frequency",
        "value": "12"
      },
      {
        "name": "shipping_interval_unit_type",
        "value": "Months"
      }
    ],
    "quantity": 1,
    "recharge_product_id": 1255996,
    "shopify_product_id": 2663712522325,
    "shopify_variant_id": 22958073806933,
    "sku": "",
    "sku_override": false,
    "status": "ACTIVE",
    "updated_at": "2019-07-31T08:04:00",
    "variant_title": ""
  }
}
```
<!-- type: tab-end -->
