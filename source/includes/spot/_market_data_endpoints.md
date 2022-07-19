# Market Data Endpoints

## Test Connectivity

```shell
curl -X 'GET' 'https://api-v2.jeritexeu.com/api/v1/public/ping'
```

```python
import requests

url = "https://api-v2.jeritexeu.com/api/v1/public/ping"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Test connectivity to the Rest API.

GET
<code>/public/ping</code>

### Parameters

No parameters

>Response example

```json
{
    "code": 200,
    "data": "success",
    "success": true
}
```

## Check Server Time

```shell
curl -X 'GET' 'https://api-v2.jeritexeu.com/api/v1/public/time'
```

```python
import requests

url = "https://api-v2.jeritexeu.com/api/v1/public/time"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Test connectivity to the Rest API and get the current server time.

GET
<code>/public/time</code>

### Parameters

No parameters

>Response example

```json
{
  "code": 200,
  "data": {
    "serverTime": 1657727196288
  },
  "success": true
}
```

## All Market Tickers

```shell
curl -X 'GET' 'https://api-v2.jeritexeu.com/api/v1/public/tickers'
```

```python
import requests

url = "https://api-v2.jeritexeu.com/api/v1/public/tickers"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

All market tickers with statistics in 24 hours.

GET
<code>/public/tickers</code>

### Parameters

No parameters

>Response example

```json
{
    "code": 200,
    "data": [
        {
            "symbol": "BTC/USDT",
            "open": 19467.44,
            "high": 20420.99,
            "low": 19250.48,
            "close": 20030.3,
            "chg": 0.0293,
            "change": 562.86,
            "volume": 1722.7730,
            "lastDayClose": 19467.44,
            "usdRate": 20030.3,
            "baseUsdRate": 1,
            "quoteVolume": 324695303.32295424621914948654
        },
        {
            "symbol": "SFT/USDT",
            "open": 0.00120001,
            "high": 0.00125100,
            "low": 0.00119010,
            "close": 0.00124000,
            "chg": 0.0337,
            "change": 0.00003999,
            "volume": 31185153.1086,
            "lastDayClose": 0.00120125,
            "usdRate": 0.00124000,
            "baseUsdRate": 1,
            "quoteVolume": 410167.082020309946
        },
        ...
    ],
    "success": true
}
```

## Specific Market Ticker

```shell
curl -X 'GET' 'https://api-v2.jeritexeu.com/api/v1/public/ticker?symbol=BTC/USDT'
```

```python
import requests

url = "https://api-v2.jeritexeu.com/api/v1/public/ticker?symbol=BTC/USDT"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Latest statistics for a symbol.

GET
<code>/public/ticker</code>

### Parameters

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| symbol | string | Yes | Symbol |

>Response example

```json
{
    "code": 200,
    "data": {
        "symbol": "BTC/USDT",
        "open": 19467.44,
        "high": 20420.99,
        "low": 19250.48,
        "close": 19966.36,
        "chg": 0.0260,
        "change": 498.92,
        "volume": 1722.9729,
        "lastDayClose": 19467.44,
        "usdRate": 19966.36,
        "baseUsdRate": 1,
        "quoteVolume": 324872799.77115424621914948654
    },
    "success": true
}
```

## Order Book

```shell
curl -X 'GET' 'https://api-v2.jeritexeu.com/api/v1/public/orderbook/L2?symbol=BTC/USDT'
```

```python
import requests

url = "https://api-v2.jeritexeu.com/api/v1/public/orderbook/L2?symbol=BTC/USDT"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Order book of specific symbol

GET
<code>/public/orderbook/L2</code>

### Parameters

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| symbol | string | Yes | Symbol |

>Response example

```json
{
  "code": 200,
  "data": {
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
curl -X 'GET' 'https://api-v2.jeritexeu.com/api/v1/public/kline?symbol=BTC/USDT&interval=1min&from=0&to=0&limit=500'
```

```python
import requests

url = "https://api-v2.jeritexeu.com/api/v1/public/kline?symbol=BTC/USDT&interval=1min&from=0&to=0&limit=500"

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)
```

Kline/candlestick bars for a symbol.

Klines are uniquely identified by their open time.

GET
<code>/public/kline</code>

### Parameters

| Parameter | Type | Required | Description |
| --------- | ---- | -------- | ----------- |
| symbol | string | Yes | Symbol |
| interval | string | Yes | Interval of Kline data. Valid values: 1min, 5min, 15min, 30min, 1hour, 4hour, 1day, 1mon, 1week, 1year |
| from | $int64 | No | start time|
| to | $int64 | No | end time|
| limit | integer | No | Limit the number of returned Klines. Default is 500. |

<aside class="notice">
    If <code>from</code> and <code>to</code> are not sent, the most recent klines are returned.
</aside>

>Response example

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
