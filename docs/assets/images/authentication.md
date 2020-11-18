# Authentication

ReCharge uses API keys to allow access to our APIs. To obtain API access, **[contact our support team](https://support.rechargepayments.com/hc/en-us/requests/new)**.

The API key is required for all API requests to the server. 

>### Header
>`X-Recharge-Access-Token: your_api_token`

We only accept API requests over HTTPS.

## Example Requests

<!--
type: tab
title: cURL
-->

### Request

```curl
curl -i -H 'X-Recharge-Access-Token: your_api_token' \
-X GET https://api.rechargeapps.com
```

### Response 

```json
{
    "store": {
        "country": "US",
        "currency": "USD",
        "email": "example_mail@gmail.com",
        "iana_timezone": "America/New_York",
        "province": "California",
        "shop_owner": "Mike Flynn",
        "store_id": 112,
        "store_name": "example_store",
        "store_timezone": "(GMT-08:00) America/Los_Angeles",
        "store_url": "example_store.myshopify.com"
    }
}
```
<!--
type: tab
title: Python
-->

### Request

```python
import requests

headers = {"X-Recharge-Access-Token": "your_api_token"}
url = "https://api.rechargeapps.com"

result = requests.get(url, headers=headers)
```

### Response

```json
{
    "store": {
        "country": "US",
        "currency": "USD",
        "email": "example_mail@gmail.com",
        "iana_timezone": "America/New_York",
        "province": "California",
        "shop_owner": "Mike Flynn",
        "store_id": 112,
        "store_name": "example_store",
        "store_timezone": "(GMT-08:00) America/Los_Angeles",
        "store_url": "example_store.myshopify.com"
    }
}
```


<!--
type: tab
title: PHP
-->

### Request

```php
<?php

$request = new HttpRequest();
$request->setUrl('https://api.rechargeapps.com/');
$request->setMethod(HTTP_METH_GET);

$request->setHeaders(array(
  'content-type' => 'application/json',
  'x-recharge-access-token' => 'your_api_token'
));

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
    "store": {
        "country": "US",
        "currency": "USD",
        "email": "example_mail@gmail.com",
        "iana_timezone": "America/New_York",
        "province": "California",
        "shop_owner": "Mike Flynn",
        "store_id": 112,
        "store_name": "example_store",
        "store_timezone": "(GMT-08:00) America/Los_Angeles",
        "store_url": "example_store.myshopify.com"
    }
}
```

<!--
type: tab
title: Ruby
-->

### Request

```ruby
require 'uri'
require 'net/http'
require 'openssl'


url = URI("https://api.rechargeapps.com/")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Get.new(url)
request["x-recharge-access-token"] = 'your_api_token'
request["content-type"] = 'application/json'


response = http.request(request)
puts response.read_body
```

### Response
```json
{
    "store": {
        "country": "US",
        "currency": "USD",
        "email": "example_mail@gmail.com",
        "iana_timezone": "America/New_York",
        "province": "California",
        "shop_owner": "Mike Flynn",
        "store_id": 112,
        "store_name": "example_store",
        "store_timezone": "(GMT-08:00) America/Los_Angeles",
        "store_url": "example_store.myshopify.com"
    }
}
```

<!-- type: tab-end -->

