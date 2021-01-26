# Update cart attributes
You can update the properties in a customer's cart using the following example.

`PUT` to `/addresses/:id`

<!--
type: tab
title: cURL
-->

```cURL
curl -i -H "X-Recharge-Access-Token: your_api_token" \
-H "Content-Type: application/json" \
-X PUT https://api.rechargeapps.com/addresses/8524391 \
--data '{
  "cart_attributes": [
    { "name": "Ford"},
    { "value": "HexaTrilion"}
  ]
}'
```

### Response

```json
{
  "address": {
    "address1": "6419 Ocean Front Walk",
    "address2": "asd",
    "cart_attributes": [
      {
        "name": "Ford"
      },
      {
        "value": "HexaTrilion"
      }
    ],
    "cart_note": null,
    "city": "Los Angeles",
    "company": "asd",
    "country": "United States",
    "created_at": "2020-05-12T12:05:28",
    "customer_id": 41842419,
    "discount_id": null,
    "first_name": "Nikola",
    "id": 46453225,
    "last_name": "Tesla",
    "note_attributes": [
      {
        "name": "Ford"
      },
      {
        "value": "HexaTrilion"
      }
    ],
    "original_shipping_lines": [],
    "phone": "asd",
    "province": "California",
    "shipping_lines_override": null,
    "updated_at": "2020-07-09T13:20:39",
    "zip": "90293"
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
  "Content-Type": "application/json"
}
url = "https://api.rechargeapps.com/addresses/8524391"
data = {
  "cart_attributes": [
    { "name": "Ford"},
    { "value": "HexaTrilion"}
  ]
}

result = requests.put(url, data=json.dumps(data), headers=headers)
```

### Response

```json
{
  "address": {
    "address1": "6419 Ocean Front Walk",
    "address2": "asd",
    "cart_attributes": [
      {
        "name": "Ford"
      },
      {
        "value": "HexaTrilion"
      }
    ],
    "cart_note": null,
    "city": "Los Angeles",
    "company": "asd",
    "country": "United States",
    "created_at": "2020-05-12T12:05:28",
    "customer_id": 41842419,
    "discount_id": null,
    "first_name": "Nikola",
    "id": 46453225,
    "last_name": "Tesla",
    "note_attributes": [
      {
        "name": "Ford"
      },
      {
        "value": "HexaTrilion"
      }
    ],
    "original_shipping_lines": [],
    "phone": "asd",
    "province": "California",
    "shipping_lines_override": null,
    "updated_at": "2020-07-09T13:20:39",
    "zip": "90293"
  }
}
```
<!--
type: tab
title: PHP
-->

```php
<?php

$request = new HttpRequest();
$request->setUrl('https://api.rechargeapps.com/addresses/8524391');
$request->setMethod(HTTP_METH_PUT);

$request->setHeaders(array(
  'content-type' => 'application/json',
  'X-Recharge-Access-Token' => 'your_api_token'
));

$request->setBody('{
  "cart_attributes": [
    { "name": "Ford"},
    { "value": "HexaTrilion"}
  ]
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
  "address": {
    "address1": "6419 Ocean Front Walk",
    "address2": "asd",
    "cart_attributes": [
      {
        "name": "Ford"
      },
      {
        "value": "HexaTrilion"
      }
    ],
    "cart_note": null,
    "city": "Los Angeles",
    "company": "asd",
    "country": "United States",
    "created_at": "2020-05-12T12:05:28",
    "customer_id": 41842419,
    "discount_id": null,
    "first_name": "Nikola",
    "id": 46453225,
    "last_name": "Tesla",
    "note_attributes": [
      {
        "name": "Ford"
      },
      {
        "value": "HexaTrilion"
      }
    ],
    "original_shipping_lines": [],
    "phone": "asd",
    "province": "California",
    "shipping_lines_override": null,
    "updated_at": "2020-07-09T13:20:39",
    "zip": "90293"
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

url = URI("https://api.rechargeapps.com/addresses/8524391")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Put.new(url)
request["X-Recharge-Access-Token"] = 'your_api_token'
request["content-type"] = 'application/json'
request.body = {
  "cart_attributes": [
    { "name": "Ford"},
    { "value": "HexaTrilion"}
  ]
}.to_json

response = http.request(request)
puts response.read_body
```

### Response
```json
{
  "address": {
    "address1": "6419 Ocean Front Walk",
    "address2": "asd",
    "cart_attributes": [
      {
        "name": "Ford"
      },
      {
        "value": "HexaTrilion"
      }
    ],
    "cart_note": null,
    "city": "Los Angeles",
    "company": "asd",
    "country": "United States",
    "created_at": "2020-05-12T12:05:28",
    "customer_id": 41842419,
    "discount_id": null,
    "first_name": "Nikola",
    "id": 46453225,
    "last_name": "Tesla",
    "note_attributes": [
      {
        "name": "Ford"
      },
      {
        "value": "HexaTrilion"
      }
    ],
    "original_shipping_lines": [],
    "phone": "asd",
    "province": "California",
    "shipping_lines_override": null,
    "updated_at": "2020-07-09T13:20:39",
    "zip": "90293"
  }
}
```
<!-- type: tab-end -->
