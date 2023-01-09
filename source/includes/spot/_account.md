# Accounts/Wallet APIs

## User Asset

```shell
curl -X 'GET' \
  'https://api-v2.jrit.io/api/v1/account?timestamp=1658030864658&signature={signature}' \
  -H 'accept: application/json' \
  -H 'X-JRT-APIKEY: your-api-key'
```

```python
import requests

url = "https://api-v2.jrit.io/api/v1/account?timestamp=1658030864658&signature={signature}"

payload={}
headers = {
  'X-JRT-APIKEY': 'your-api-key'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

Get all user assets.

GET `/account (HMAC SHA256)`

### Parameters

|Name|Type|Required|Description|
|---|---|---|---|
|recvWindow|Long|false||
|timestamp|Long|true|timestamp|
|signature|string|true|HMAC SHA256 signature|

>Response example

```json
{
    "code": 200,
    "data": {
        "spot": [
            {
                "asset": "ADA",
                "balance": 0,
                "frozen_balance": 0,
                "locked_balance": 0,
                "total_balance": 0,
                "locked": false
            },
            {
                "asset": "AXS",
                "balance": 0,
                "frozen_balance": 0,
                "locked_balance": 0,
                "total_balance": 0,
                "locked": false
            },
            {
                "asset": "BPLUS",
                "balance": 0,
                "frozen_balance": 0,
                "locked_balance": 0,
                "total_balance": 0,
                "locked": false
            },
            ...
        ]
    },
    "success": true
}
```

## Account Info

```shell
curl -X 'GET' \
  'https://api-v2.jrit.io/api/v1/account/apiKey?timestamp=1658030864658&signature=signature' \
  -H 'accept: application/json' \
  -H 'X-JRT-APIKEY: your-api-key'
```

```python
import requests

url = "https://api-v2.jrit.io/api/v1/account/apiKey?timestamp=1658030864658&signature=signature"

payload={}
headers = {
  'X-JRT-APIKEY': 'your-api-key'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

Get account information base on API Key.

GET `/account/apiKey (HMAC SHA256)`

### Parameters

|Name|Type|Required|Description|
|---|---|---|---|
|recvWindow|Long|false||
|timestamp|Long|true|timestamp|
|signature|string|true|HMAC SHA256 signature|

>Response example

```json
{
    "code": 200,
    "data": {
        "member_id": "xxxxxxxxx-9590-4f6c-b274-xxxxxxxxxxxx",
        "permissions": [
            "READ",
            "SPOT_TRADE"
        ],
        "bind_ip": null,
        "expire_time": "2022-12-15T02:12:01",
        "create_time": "2022-07-15T02:12:01"
    },
    "success": true
}
```
