## Get Balances

`GET /balances`

Fetches the user's balances of all assets on the exchange. This includes deposits, collateral and open positions.

> Sample Request

```json
{
  "exchange": "BINANCE"
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|[[Exchange](#exchange)]|True|Exchange to fetch data from|

> Successful Sample Response

```json
{
  "BTC": 1.21,
  "ETH": 5.67,
  "SOL": 10.11
}
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|asset symbol|number|false|Quantity of balance (in units of the asset)|