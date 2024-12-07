# OTC

## Request quote

> Sample Request

```bash
POST /request-quote
```

```json
# Body
{
    "accountId": "a0743434-66c8-49b7-aca2-46c910a54cf1",
    "fromAsset": "BTC",
    "toAsset": "USD",
    "fromAmount": 1.25
}
```

> Sample Response

```json
{
    "quote": {
        "accountId": "a0743434-66c8-49b7-aca2-46c910a54cf1",
        "fromAsset": "BTC",
        "toAsset": "USD",
        "fromAssetQuantity": 1.25,
        "toAssetQuantity": 81436.0875,
        "expiryTime": 1733561867046245,
        "signature": "6932874cf486617239c7d27100e911903ccbee05c8b07fe3f4299e047f46553a"
    },
}
```

`GET /request-quote`

Generates an OTC trade quote for the specific asset pair and amount. Exactly one of `fromAmount` or `toAmount` must be specified in the request. 'fromAmount' is in units of the 'fromAsset' and 'toAmount' is in units of the 'toAsset'.

The response will include the expiry time of the quote, as well as a signature that will need to be sent while accepting a quote in order to successfully complete the trade.

### Request

| Parameter | Type               | Required | Description                                   |
|-----------|--------------------|----------|-----------------------------------------------|
| accountId | string             | True     | Account ID to generate quote for              |
| fromAsset | string             | True     | Asset to buy                                 |
| toAsset   | string             | True     | Asset to sell                                |
| fromAmount | number             | False     | Amount of 'fromAsset' to buy                  |
| toAmount   | number             | False     | Amount of 'toAsset' to sell                   |

### Response

| Name | Type               | Required | Description                                   |
|------|--------------------|----------|-----------------------------------------------|
| quote | [Quote](#quote) | True     | Quote for the trade  |

### Quote

| Name | Type | Required | Description |
|------|------|----------|-------------|
| accountId | string | True | Account ID the quote was generated for |
| fromAsset | string | True | Asset to buy |
| toAsset | string | True | Asset to sell |
| fromAssetQuantity | number | True | Amount of fromAsset to buy |
| toAssetQuantity | number | True | Amount of toAsset to sell |
| expiryTime | number | True | Unix timestamp in microseconds when quote expires |
| signature | string | True | Signature required to execute trade with this quote |


## Accept quote

> Sample Request

```bash
POST /accept-quote
```

```json
# Body
{
    "quote": {
        "accountId": "a0743434-66c8-49b7-aca2-46c910a54cf1",
        "fromAsset": "BTC",
        "toAsset": "USD",
        "fromAssetQuantity": 1.25,
        "toAssetQuantity": 81436.0875,
        "expiryTime": 1733561867046245,
        "signature": "6932874cf486617239c7d27100e911903ccbee05c8b07fe3f4299e047f46553a"
    }
}
```

> Sample Response

```json
{}
```

`POST /accept-quote`

Accepts an OTC trade quote and completes the trade.

### Request


| Parameter | Type               | Required | Description                                   |
|-----------|--------------------|----------|-----------------------------------------------|
| quote | [Quote](#quote) | True     | Quote to accept for the trade  |

### Response

If successful, returns a 200 response with an empty JSON in the response body. 
Otherwise, returns an error message.