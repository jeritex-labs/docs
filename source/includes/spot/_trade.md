# Spot Trade

<aside class="notice">
Spot is private endpoint and requires authentication. Please refer to the <a href='#authentication'>Authentication</a> section for more information.
</aside>

## Test connectivity trade API

```shell
curl --location --request POST 'https://api.jeritex.io/api/v1/trade/ping?timestamp=1657874098080&signature={signature}' \
--header 'X-JRT-APIKEY: {your-api-key}'
```

```python
import requests

url = "https://api.jeritex.io/api/v1/trade/ping?timestamp=1657874098080&signature={signature}"

payload={}
headers = {
  'X-JRT-APIKEY': 'your-api-key'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

Test connectivity to the Trade API.

GET
`/trade/ping (HMAC SHA256)`

### Parameters

| Name       | Type   | Required | Description           |
| ---------- | ------ | -------- | --------------------- |
| recvWindow | Long   | false    |                       |
| timestamp  | Long   | true     | timestamp             |
| signature  | string | true     | HMAC SHA256 signature |

> Response example

```json
{
  "code": 200,
  "data": "pong!",
  "success": true
}
```

## Create Order

```shell
curl -X 'POST' \
  'https://api.jeritex.io/api/v1/trade/order?symbol=JRIT%2FUSDT&side=BUY&type=MARKET&quantity=1000&price=1&timestamp=1657874098080&signature={signature}' \
  -H 'accept: application/json' \
  -H 'X-JRT-APIKEY: your-api-key' \
  -d ''
```

```python
import requests

url = "https://api.jeritex.io/api/v1/trade/order?symbol=JRIT%2FUSDT&side=BUY&type=MARKET&quantity=1000&price=1&timestamp=1657874098080&signature={signature}"

payload={}
headers = {
  'X-JRT-APIKEY': 'your-api-key'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

Create a new order

POST `/trade/order (HMAC SHA256)`

### Parameters

| Name       | Type   | Required | Description                          |
| ---------- | ------ | -------- | ------------------------------------ |
| symbol     | String | true     |                                      |
| side       | Enum   | true     | [Order side](#side-side)             |
| type       | Enum   | true     | [Order type](#order-type-order_type) |
| quantity   | Long   | true     |                                      |
| price      | Long   | false    |                                      |
| recvWindow | Long   | false    |                                      |
| timestamp  | Long   | true     | timestamp                            |
| signature  | String | true     | HMAC SHA256 signature                |

> Response example

```json
{
  "code": 0,
  "message": "string",
  "data": {
    "order_id": "string",
    "member_id": "string",
    "type": "MARKET",
    "amount": 0,
    "symbol": "string",
    "traded_amount": 0,
    "turnover": 0,
    "base_currency": "string",
    "quote_currency": "string",
    "status": "TRADING",
    "direction": "BUY",
    "price": 0,
    "time": 0,
    "completed_time": 0,
    "canceled_time": 0,
    "use_discount": true,
    "order_source": "",
    "detail": [
      {
        "order_id": "string",
        "price": 0,
        "amount": 0,
        "turnover": 0,
        "fee": 0,
        "timestamp": 0
      }
    ],
    "completed": true
  },
  "success": true
}
```

## Cancel all Open Orders on a Symbol

```shell
curl -X 'POST' \
  'https://api.jeritex.io/api/v1/trade/cancel?symbol=JRIT%2FUSDT&timestamp=1657874098080&signature={signature}' \
  -H 'accept: application/json' \
  -H 'X-JRT-APIKEY: your-api-key' \
  -d ''
```

```python
import requests

url = "https://api.jeritex.io/api/v1/trade/cancel?symbol=JRIT%2FUSDT&timestamp=1657874098080&signature={signature}"

payload={}
headers = {
  'X-JRT-APIKEY': 'your-api-key'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

Cancels all active orders on a symbol.

POST `/trade/cancel (HMAC SHA256)`

### Parameters

| Name       | Type   | Required | Description           |
| ---------- | ------ | -------- | --------------------- |
| symbol     | String | true     |                       |
| recvWindow | Long   | false    |                       |
| timestamp  | Long   | true     | timestamp             |
| signature  | String | true     | HMAC SHA256 signature |

> Response example

```json
{
  "code": 0,
  "message": "string",
  "data": "string",
  "success": true
}
```

## Cancel an order

```shell
curl -X 'POST' \
  curl -X 'POST' \
  'https://api.jeritex.io/api/v1/trade/cancel/423523?timestamp=1657874098080&signature={signaure}' \
  -H 'accept: application/json' \
  -H 'X-JRT-APIKEY: your-api-key' \
  -d ''
```

```python
import requests

url = "https://api.jeritex.io/api/v1/trade/cancel/423523?timestamp=1657874098080&signature={signaure}"

payload={}
headers = {
  'X-JRT-APIKEY': 'your-api-key'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

Cancel order by `orderId`

POST `/trade/cancel/{orderId} (HMAC SHA256)`

### Parameters

| Name       | Type   | Required | Description           |
| ---------- | ------ | -------- | --------------------- |
| orderId    | String | true     |                       |
| recvWindow | Long   | false    |                       |
| timestamp  | Long   | true     | timestamp             |
| signature  | String | true     | HMAC SHA256 signature |

> Response example

```json
{
  "code": 0,
  "message": "string",
  "data": "string",
  "success": true
}
```

## Trade history

```shell
curl -X 'POST' \
  curl -X 'GET' \
  'https://api.jeritex.io/api/v1/trade/history?symbol=JRIT/USDT&pageNo=0&pageSize=20&timestamp=1657874098080&signature={signature}' \
  -H 'accept: application/json' \
  -H 'X-JRT-APIKEY: your-api-key'
```

```python
import requests

url = "https://api.jeritex.io/api/v1/trade/history?symbol=JRIT/USDT&pageNo=0&pageSize=20&timestamp=1657874098080&signature={signature}"

payload={}
headers = {
  'X-JRT-APIKEY': 'your-api-key'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

Get trading history for a symbol.

GET `/trade/history (HMAC SHA256)`

### Parameters

| Name       | Type    | Required | Description           |
| ---------- | ------- | -------- | --------------------- |
| symbol     | String  | true     |                       |
| pageNo     | Integer | false    | default is 0          |
| pageSize   | Integer | false    | default is 20         |
| recvWindow | Long    | false    |                       |
| timestamp  | Long    | true     | timestamp             |
| signature  | String  | true     | HMAC SHA256 signature |

> Response example

```json
{
  "code": 200,
  "data": {
    "content": [
      {
        "amount": 0,
        "base_currency": "string",
        "canceled_time": 0,
        "completed": true,
        "completed_time": 0,
        "detail": [
          {
            "amount": 0,
            "fee": 0,
            "order_id": "string",
            "price": 0,
            "timestamp": 0,
            "turnover": 0
          }
        ],
        "direction": "BUY",
        "member_id": "string",
        "order_id": "string",
        "order_source": "string",
        "price": 0,
        "quote_currency": "string",
        "status": "TRADING",
        "symbol": "string",
        "time": 0,
        "traded_amount": 0,
        "turnover": 0,
        "type": "MARKET",
        "use_discount": true
      }
    ],
    "empty": true,
    "first": true,
    "last": true,
    "number": 0,
    "number_of_elements": 0,
    "pageable": {
      "offset": 0,
      "page_number": 0,
      "page_size": 20,
      "paged": true,
      "sort": {
        "empty": false,
        "sorted": true,
        "unsorted": false
      },
      "unpaged": false
    },
    "size": 20,
    "sort": {
      "empty": false,
      "sorted": true,
      "unsorted": false
    },
    "total_elements": 0,
    "total_pages": 0
  },
  "success": true
}
```

## Order detail

```shell
  curl -X 'GET' \
  'https://api.jeritex.io/api/v1/trade/detail/54223435?timestamp=1657874098080&signature={signature}' \
  -H 'accept: application/json' \
  -H 'X-JRT-APIKEY: your-api-key'
```

```python
import requests

url = "https://api.jeritex.io/api/v1/trade/detail/54223435?timestamp=1657874098080&signature={signature}"

payload={}
headers = {
  'X-JRT-APIKEY': 'your-api-key'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

Get order detail by `orderId`.

GET `/trade/detail/{orderId} (HMAC SHA256)`

### Parameters

| Name       | Type   | Required | Description           |
| ---------- | ------ | -------- | --------------------- |
| orderId    | String | true     |                       |
| recvWindow | Long   | false    |                       |
| timestamp  | Long   | true     | timestamp             |
| signature  | String | true     | HMAC SHA256 signature |

> Response example

```json
{
  "code": 0,
  "message": "success",
  "data": [
    {
      "order_id": "54223435",
      "price": 1,
      "amount": 1000,
      "turnover": 0,
      "fee": 0,
      "timestamp": 1657874098080
    }
  ],
  "success": true
}
```

## Current Open Orders

```shell
curl -X 'GET' \
  'https://api.jeritex.io/api/v1/trade/current?symbol=JRIT/USDT&pageNo=0&pageSize=20&timestamp=1657874098080&signature={signature}' \
  -H 'accept: application/json' \
  -H 'X-JRT-APIKEY: your-api-key'
```

```python
import requests

url = "https://api.jeritex.io/api/v1/trade/current?symbol=JRIT/USDT&pageNo=0&pageSize=20&timestamp=1657874098080&signature={signature}"

payload={}
headers = {
  'X-JRT-APIKEY': 'your-api-key'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

Get current open orders for a symbol.

GET `/trade/current (HMAC SHA256)`

### Parameters

| Name       | Type    | Required | Description           |
| ---------- | ------- | -------- | --------------------- |
| symbol     | String  | true     |                       |
| pageNo     | Integer | false    | default is 0          |
| pageSize   | Integer | false    | default is 20         |
| recvWindow | Long    | false    |                       |
| timestamp  | Long    | true     | timestamp             |
| signature  | String  | true     | HMAC SHA256 signature |

> Response example

```json
{
  "code": 200,
  "data": {
    "content": [
      {
        "amount": 0,
        "base_currency": "string",
        "canceled_time": 0,
        "completed": true,
        "completed_time": 0,
        "detail": [
          {
            "amount": 0,
            "fee": 0,
            "order_id": "string",
            "price": 0,
            "timestamp": 0,
            "turnover": 0
          }
        ],
        "direction": "BUY",
        "member_id": "string",
        "order_id": "string",
        "order_source": "string",
        "price": 0,
        "quote_currency": "string",
        "status": "TRADING",
        "symbol": "string",
        "time": 0,
        "traded_amount": 0,
        "turnover": 0,
        "type": "MARKET",
        "use_discount": true
      }
    ],
    "empty": true,
    "first": true,
    "last": true,
    "number": 0,
    "number_of_elements": 0,
    "pageable": {
      "offset": 0,
      "page_number": 0,
      "page_size": 20,
      "paged": true,
      "sort": {
        "empty": false,
        "sorted": true,
        "unsorted": false
      },
      "unpaged": false
    },
    "size": 20,
    "sort": {
      "empty": false,
      "sorted": true,
      "unsorted": false
    },
    "total_elements": 0,
    "total_pages": 0
  },
  "success": true
}
```
