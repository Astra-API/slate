# OTC

## Authentication

Endpoint: `https://prod.astra-api.dev/v2`

You can generate an API key at <https://terminal.astra-api.dev/settings/apikey>. Set the header `x-astra-api-key` to the value of your API key.

Some endpoints may require you to provide your account ID. You can find this at <https://terminal.astra-api.dev/settings/profile>

## Stream quotes

> Sample Request

```bash
/ws/stream-otc-quotes/{account_id}?from=BTC&to=USD&fromQty=1.25
```

> Sample Response

```json
{
    "quote": {
        "quoteId": "a0743434-66c8-49b7-aca2-46c910a54cf1",
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

`/ws/stream-otc-quotes/{account_id}`

This is a WebSocket endpoint that continuously streams quotes to the client at a periodic interval.

Each generated quote is for the specific asset pair and amount. The `fromQty` and `toQty` parameters specify the amount of the 'fromAsset' or 'toAsset' to trade. Exactly one of `fromQty` or `toQty` must be specified.

Each quote sent will include the expiry time of the quote, as well as a signature that will need to be sent while accepting a quote in order to successfully complete the trade.

### Request

| Parameter | Type               | Required | Description                                   |
|-----------|--------------------|----------|-----------------------------------------------|
| account_id | string             | True     | Account ID in the URL path                    |
| from | string             | True     | Asset to buy (query parameter)                |
| to   | string             | True     | Asset to sell (query parameter)               |
| fromQty | number             | True     | Amount of 'fromAsset' to buy (query parameter) |

### Response

| Name | Type               | Required | Description                                   |
|------|--------------------|----------|-----------------------------------------------|
| quote | [Quote](#quote) | True     | Quote for the trade  |

### Quote

| Name | Type | Required | Description |
|------|------|----------|-------------|
| quoteId | string | True | Unique identifier for the quote |
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
POST /otc/accept-quote/{account_id}
```

```json
# Body
{
    "quote": {
        "quoteId": "a0743434-66c8-49b7-aca2-46c910a54cf1",
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

`POST /otc/accept-quote/{account_id}`

Accepts an OTC trade quote and completes the trade.

### Request

| Parameter | Type               | Required | Description                                   |
|-----------|--------------------|----------|-----------------------------------------------|
| account_id | string             | True     | Account ID in the URL path                    |
| quote | [Quote](#quote) | True     | Quote to accept for the trade  |

### Response

If successful, returns a 200 response with an empty JSON in the response body. 
Otherwise, returns an error message.