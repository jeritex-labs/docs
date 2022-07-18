# Authentication

<aside class="notice">
<!-- TODO: fix link -->
Please visit <a href='https://jeritexeu.com/api-key'>this page</a> to generate an API key
</aside>

<aside class="notice">
All requests made to private endpoints must be authenticated. Requests made to public endpoints do not require additional authentication.
</aside>

## Parameters for Authenticated Endpoints

### API Key

* API-keys are passed into the Rest API via the `X-JRT-APIKEY` header.
* API-keys can be configured to only access certain types of secure endpoints. For example, one API-key could be used for TRADE only, while another API-key can access everything except for TRADE routes.
* By default, API-keys can access all secure routes.

<aside class="warning">
API-keys and secret-keys are case sensitive.
</aside>

### Parameters

The following parameters must be used for authentication:

* **timestamp**: UTC timestamp in milliseconds
* **signature**: Base64 encoded HMAC-SHA256 signature of the request body using the secret key.

We also provide `recvWindow` (unit in millisecond and default value is 5,000) to specify how Long an HTTP request is valid. It is also used to prevent replay attacks. Maximum allowed value is 60,000.

A smaller `recvWindow` is more secure, but your request may fail if the transmission time is greater than your `recvWindow`.

Please make sure that your timestamp is in sync with our server time. You can use the [Server Time endpoint](/#check-server-time).

<aside class="warning">
 Please make sure that the timestamp parameter adheres to the following rule: serverTime - recvWindow <= timestamp < serverTime + 1000; serverTime stands for Jeritex server time, which can be queried via the <a href='/#check-server-time'>Server Time endpoint.</a>
</aside>

## Create A Request

1. Concatenate all the public parameters in the query string format. This will be used to generate the `signature`.
2. Use the HMAC_SHA256 algorithm to sign the query string in step 1, and convert it to a hex string to obtain the signature parameter.
3. Append the sign parameter to the end of the parameters string, and send the HTTP request. Note that the message format for GET and POST requests is different. Please refer to the examples.

### SIGNED Endpoint Examples for GET /trade/history

Here is a step-by-step example of how to send a valid signed payload from the Linux command line using echo, openssl, and curl.

|key|value|
|---|---|
|apiKey|vmPUZE6mv9SD5VNHk4HlWFsOr6aKE2zvsw0MuIgwCIPy6utIco14y7Ju91duEh8A|
|secretKey|NhqPtmdSJYdKjVHjA7PZj4Mge3R5YNiP1e3UZjInClVN65XAbvqqM6A7H5fATj0j|

<aside class="warning">
Just example keys, please use your own keys.
</aside>

```shell
# HMAC SHA256 signature:
echo -n "symbol=BTC/USDT&pageNo=0&pageSize=20&timestamp=1657861196487&recvWindow=5000" |  openssl dgst -sha256 -hmac "NhqPtmdSJYdKjVHjA7PZj4Mge3R5YNiP1e3UZjInClVN65XAbvqqM6A7H5fATj0j"
(stdin)= 50e008a7c887eb3f1e3056bb07c4b9bcf4dec7506ce5539e9cade17a4de782de
```
  
  ```shell
  curl -H "X-JRT-APIKEY": vmPUZE6mv9SD5VNHk4HlWFsOr6aKE2zvsw0MuIgwCIPy6utIco14y7Ju91duEh8A" -X GET 'https://api-v2.jeritexeu.com/api/v1/trade/history?symbol=BTC%2FUSDT&pageNo=0&pageSize=20&timestamp=1657861196487&recvWindow=5000&signature=50e008a7c887eb3f1e3056bb07c4b9bcf4dec7506ce5539e9cade17a4de782de'
  ```

```python
import time
import hmac
import hashlib

from urllib.parse import urlencode


api_key = "g4BY0BA40t5qwD6OLrIpN9qbPx1PGbWD"
api_secret = "PSqKPLE52AR6iHsoYLffDsO8H9qEa92cNBdq6T5Ir0a1oLNekaWdwwmuGwLNeKSA"
base_url = "https://api-v2.jeritexeu.com/api/v1"


def timestamp():
    return int(time.time() * 1000)


def encoded_string(query):
    return urlencode(query, True)


def _get_sign(data):
    m = hmac.new(api_secret.encode("utf-8"), data.encode("utf-8"), hashlib.sha256)
    return m.hexdigest()

def signed_request(url_path, payload={}):
    query_string = urlencode(payload, True)
    if query_string:
        query_string = "{}&timestamp={}".format(query_string, timestamp())
    else:
        query_string = "timestamp={}".format(timestamp())

    url = (
        base_url + url_path + "?" + query_string + "&signature=" + _get_sign(query_string)
    )
    print(url)


payload = {
    "symbol": "BTC/USDT",
    "pageNo":  0,
    "pageSize": 20,
    "recvWindow":  60000
}
signed_request("/trade/history", payload)
```

|Parameter|Value|
|---|---|
|symbol|BTC/USDT|
|pageNo|0|
|pageSize|20|
|recvWindow|5000|
|timestamp|1657861196487|

* **queryString:**

`symbol=BTC/USDT&pageNo=0&pageSize=20&timestamp=1657861196487&recvWindow=5000`
