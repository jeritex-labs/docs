# Market Data Endpoints

## Test Connectivity

```shell
curl -X 'GET' 'https://api-v2.jeritex.io/api/v1/public/ping'
```

```python
import requests

url = "https://api-v2.jeritex.io/api/v1/public/ping"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Test connectivity to the Rest API.

GET
<code>/public/ping</code>

### Parameters

No parameters

> Response example

```json
{
  "code": 200,
  "data": "success",
  "success": true
}
```

## Check Server Time

```shell
curl -X 'GET' 'https://api-v2.jeritex.io/api/v1/public/time'
```

```python
import requests

url = "https://api-v2.jeritex.io/api/v1/public/time"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Test connectivity to the Rest API and get the current server time.

GET
<code>/public/time</code>

### Parameters

No parameters

> Response example

```json
{
  "code": 200,
  "data": {
    "server-time": 1657727196288
  },
  "success": true
}
```

## Market Summary

```shell
curl -X 'GET' 'https://api-v2.jeritex.io/api/v1/public/summary'
```

```python
import requests

url = "https://api-v2.jeritex.io/api/v1/public/summary"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Market summary.

GET
<code>/public/summary</code>

### Parameters

No parameters

> Response example

```json

  "code": 200,
  "data": [
    {
      "trading_pairs": "BTC/USDT",
      "ticker_id": "BTC/USDT",
      "base": "BTC",
      "target": "USDT",
      "last_price": 17187.92000000,
      "lowest_ask": 30000.00000000,
      "highest_bid": 0,
      "base_volume": 354.9114,
      "quote_volume": 6103615.7950,
      "price_change_percent_24h": -0.0027,
      "highest_price_24h": 17243.36000000,
      "lowest_price_24h": 17185.04000000
    },
    ...
  ],
  "success": true
```

## All Market Tickers

```shell
curl -X 'GET' 'https://api-v2.jeritex.io/api/v1/public/tickers'
```

```python
import requests

url = "https://api-v2.jeritex.io/api/v1/public/tickers"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

All market tickers with statistics in 24 hours.

GET
<code>/public/tickers</code>

### Parameters

No parameters

> Response example

```json
{
    "code": 200,
    "data": {
      "DOGE_USDT": {
        "ticker_id": "DOGE/USDT",
        "base_currency": "DOGE",
        "target_currency": "USDT",
        "last_price": 0.074750,
        "base_volume": 8830133.0000,
        "quote_volume": 663044.4657,
        "ask": 0.074760,
        "bid": 0.074740,
        "open": 0.07524000,
        "high": 0.07563000,
        "low": 0.07473000,
        "close": 0.074750,
        "chg": -0.0066,
        "change": -0.00049000,
        "last_day_close": 0,
        "usd_rate": 0.074750,
        "base_usd_rate": 1
      },
      "SFT_USDT": {
        "ticker_id": "SFT/USDT",
        "base_currency": "SFT",
        "target_currency": "USDT",
        "last_price": 0,
        "base_volume": 0.0000,
        "quote_volume": 0,
        "ask": 0,
        "bid": 0,
        "open": 0,
        "high": 0,
        "low": 0,
        "close": 0,
        "chg": 0.00,
        "change": 0,
        "last_day_close": 0,
        "usd_rate": 0,
        "base_usd_rate": 1
      },
        ...
    },
    "success": true
}
```

## Specific Market Ticker

```shell
curl -X 'GET' 'https://api-v2.jeritex.io/api/v1/public/ticker?ticker_id=BTC/USDT'
```

```python
import requests

url = "https://api-v2.jeritex.io/api/v1/public/ticker?ticker_id=BTC/USDT"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Latest statistics for a symbol.

GET
<code>/public/ticker</code>

### Parameters

| Parameter | Type   | Required | Description |
| --------- | ------ | -------- | ----------- |
| ticker_id | string | Yes      | Symbol      |

> Response example

```json
{
  "code": 200,
  "data": {
    "ticker_id": "BTC/USDT",
    "base_currency": "BTC",
    "target_currency": "USDT",
    "last_price": 17190.08,
    "base_volume": 323.038,
    "quote_volume": 5555797.7228,
    "ask": null,
    "bid": null,
    "open": 17233.44,
    "high": 17243.36,
    "low": 17185.04,
    "close": 17190.08,
    "chg": -0.0026,
    "change": -43.36,
    "last_day_close": 0,
    "usd_rate": 17190.08,
    "base_usd_rate": 1
  },
  "success": true
}
```

## Order Book

```shell
curl -X 'GET' 'https://api-v2.jeritex.io/api/v1/public/orderbook?ticker_id=BTC/USDT'
```

```python
import requests

url = "https://api-v2.jeritex.io/api/v1/public/orderbook?ticker_id=BTC/USDT"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Order book of specific symbol

GET
<code>/public/orderbook/L2</code>

### Parameters

| Parameter | Type   | Required | Description                                                       |
| --------- | ------ | -------- | ----------------------------------------------------------------- |
| ticker_id | string | Yes      | Symbol                                                            |
| depth     | int    | No       | 0 returns full depth. Depth = 100 means 50 for each bid/ask side. |

> Response example

```json
{
  "code": 200,
  "data": {
    "ticker_id": "BTC/USDT",
    "timestamp": 1673237050158,
    "asks": [
      {
        "price": 19974.29,
        "amount": 0.5946
      },
      {
        "price": 19974.97,
        "amount": 0.0003
      },
      ...
    ],
    "bids": [
      {
        "price": 19974.28,
        "amount": 0.5741
      },
      {
        "price": 19972.8,
        "amount": 0.1502
      },
      ...
    ]
  },
  "success": true
}
```

## Kline/Candlestick Data

```shell
curl -X 'GET' 'https://api-v2.jeritex.io/api/v1/public/kline?ticker_id=BTC/USDT&interval=1min&from=0&to=0&limit=500'
```

```python
import requests

url = "https://api-v2.jeritex.io/api/v1/public/kline?ticker_id=BTC/USDT&interval=1min&from=0&to=0&limit=500"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Kline/candlestick bars for a symbol.

Klines are uniquely identified by their open time.

GET
<code>/public/kline</code>

### Parameters

| Parameter | Type    | Required | Description                                                                                            |
| --------- | ------- | -------- | ------------------------------------------------------------------------------------------------------ |
| ticker_id | string  | Yes      | Symbol                                                                                                 |
| interval  | string  | Yes      | Interval of Kline data. Valid values: 1min, 5min, 15min, 30min, 1hour, 4hour, 1day, 1mon, 1week, 1year |
| from      | $int64  | No       | start time                                                                                             |
| to        | $int64  | No       | end time                                                                                               |
| limit     | integer | No       | Limit the number of returned Klines. Default is 500.                                                   |

<aside class="notice">
    If <code>from</code> and <code>to</code> are not sent, the most recent klines are returned.
</aside>

> Response example

```json
{
  "code": 200,
  "data": [
    [
      1638103320000,
      54410.77,
      54410.77,
      54410.76,
      54410.76,
      0.000822999932917692
    ],
    [
      1638103380000,
      54410.77,
      54440.16,
      54410.75,
      54410.75,
      3.6218707025782133
    ],
    ...
  ],
  "success": true
}
```
