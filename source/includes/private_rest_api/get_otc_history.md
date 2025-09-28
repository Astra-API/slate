## Get OTC History

`GET /converts/{account_id}`

Fetches the OTC trade history for a specific account. We also use the term "convert" or "swap" to refer to an OTC trade in some places.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|account_id|UUID|True|The account ID to fetch OTC history for|

> Sample Response

```json
[
  {
    "displayId": "550e8400-e29b-41d4-a716-446655440000",
    "id": 123,
    "takerAccountId": "550e8400-e29b-41d4-a716-446655440000",
    "makerAccountId": "550e8400-e29b-41d4-a716-446655440001",
    "buyInstrumentId": "550e8400-e29b-41d4-a716-446655440002",
    "buyQuantity": "1.5",
    "buyTxnId": 456,
    "sellInstrumentId": "550e8400-e29b-41d4-a716-446655440003",
    "sellQuantity": "0.001",
    "sellTxnId": 457,
    "category": "otc",
    "notes": null,
    "createdAt": "2024-01-15T10:30:00Z",
    "updatedAt": "2024-01-15T10:30:00Z",
    "buySymbol": "ETH",
    "sellSymbol": "BTC"
  }
]
```

### Response

The response is a JSON array of OTC trade objects, ordered by creation date (most recent first).

|Name|Type|Description|
|---|---|---|
|displayId|String|Unique display identifier for the trade (UUID)|
|id|Integer|Internal trade ID|
|takerAccountId|String|Account ID of the trade taker (the requesting account)|
|makerAccountId|String|Account ID of the trade maker (counterparty)|
|buyInstrumentId|String|Instrument ID for the asset being bought|
|buyQuantity|String|Quantity of the asset being bought (as decimal string)|
|buyTxnId|Integer or null|Transaction ID for the buy side|
|sellInstrumentId|String|Instrument ID for the asset being sold|
|sellQuantity|String|Quantity of the asset being sold (as decimal string)|
|sellTxnId|Integer or null|Transaction ID for the sell side|
|category|String or null|Trade category (e.g., "otc")|
|notes|String or null|Additional notes about the trade|
|createdAt|String|ISO 8601 timestamp when the trade was created|
|updatedAt|String|ISO 8601 timestamp when the trade was last updated|
|buySymbol|String|Symbol of the asset being bought (e.g., "ETH", "BTC")|
|sellSymbol|String|Symbol of the asset being sold (e.g., "ETH", "BTC")|
