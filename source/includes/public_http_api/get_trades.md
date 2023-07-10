
## Get Trades

`GET /trades`

Returns trades for the specified market within the specified time window. 

The default pageSize is 50, and the default pageNumber is 0 (pages are 0-indexed).

If neither startTime or endTime is specified, the server will return the first page of the most recent trades. The client may choose to specify just a startTime, just an endTime, or both.

Trades are returned in increasing order of their timestamp.

> Sample Request

```json
{
  "exchange": "BINANCE",
  "baseAsset": {
    "type": "SPOT",
    "asset": "BTC"
  },
  "quoteAsset": "USDT"
}
```
<aside class="notice">
Support for specifiying <code>startTime</code>, <code>endTime</code>,<code>pageSize</code>,and <code>pageNumber</code> are currently a work in progress. 
</aside>

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|[Exchange](#exchange)|True|Exchange to fetch data from.|
|baseAsset|String|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|
|startTime|Float (f64)|False|Start time for fetching data (unix timestamp)|
|endTime|Float (f64)|False|End time for fetching data (unix timestamp)|
|pageSize|Integer (i32)|50|Page size for paginated responses|
|pageNumber|Integer (i32)|0|Page number for paginated responses|

> Successful Sample Response

```json
{
    "exchangeMarket": {
        "exchange": "BINANCE",
        "market": {
            "baseAsset": {
                "type": "SPOT",
                "asset": "BTC"
            },
            "quoteAsset": "USDT"
        }
    },
    "price": 30199.49,
    "quantity": 0.0032,
    "side": "Sell"
}
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|[[Trade](#trade)]|True|List of Trade objects. See Schema.|

<!-- |Name|Type|Required|Description|
|---|---|---|---|---|
|exchange_market|[Exchange Market(#trade)]|True|Contains exchange and market which was traded|
|price|Float (f64)|True|Price of trade units of quote asset|
|quantity| Float (f64)|True|Quantity of trade in units of base asset|
|side|String|True|Direction of taker| -->

<!-- ### Trade

|Name|Type|Required|Description|
|---|---|---|---|---|
|baseAsset|String|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|
|price|number|True|Price of the trade (in units of quoteAsset)|
|quantity|number|True|Quantity of the trade (in units of baseAsset)|
|side|[Side](#side)|True|Whether the taker bought or sold the baseAsset|
|timestamp|integer(int32)|True|Exchange timestamp for when the trade took place|

### Side

|Value|Description|
|---|---|
|» buy|Represents a buy order or trade|
|» sell|Represents a sell order or trade| -->