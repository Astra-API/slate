# Public HTTP API

## Get Markets

`GET /markets`

Returns all markets listed by the specified exchange.

> Sample Request

```json
{
  "exchange": "binance"
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|String|True|Exchange to fetch data from|

> Successful Sample Response

```json
[
  {
      "baseAsset": {
          "type": "SPOT",
          "asset": "ETH"
      },
      "quoteAsset": "BTC"
  },
  {
      "baseAsset": {
          "type": "SPOT",
          "asset": "LTC"
      },
      "quoteAsset": "BTC"
  },
]
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|[[Market](#market)]|True|List of all supported asset pairs|

<aside class="notice">
Returns SPOT asset pairs only.
</aside>
<!-- ### Market

|Name|Type|Required|Description|
|---|---|---|---|---|
|baseAsset|String|True|Base asset of the market|
|quoteAsset|String|True|Quote asset of the market| -->

## Get Price

`GET /price`

Returns the current price of the specified market.

> Sample Request

```json
{
  "exchange": "binance",
  "baseAsset": "BTC",
  "quoteAsset": "USDT",
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|String|True|Exchange to fetch data from|
|baseAsset|String|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|

<aside class="notice">
  <code>exchange</code> parameter is lowercase, Ex: 'binance', 'coinbase'. Update for <code>exchange</code> to become UPPERCASE will rollout. 
</aside>

> Successful Sample Response

```json
27879.5
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|Float (f64)|True|Price of the asset in units of quote asset|

## Get Best Bid/Offer

`GET /bbo`

Returns the current BBO of the specified market on the specified exchange.

> Sample Request

```json
{
  "exchange": "binance",
  "baseAsset": "BTC",
  "quoteAsset": "USDT",
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|String|True|Exchange to fetch data from|
|baseAsset|String|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|

<aside class="notice">
  <code>exchange</code> parameter is lowercase, Ex: 'binance', 'coinbase'. Update for <code>exchange</code> to become UPPERCASE will rollout. 
</aside>

> Successful Sample Response

```json
{
  "bid": {
    "price": 27879.5,
    "quantity": 1.5,
  },
  "ask": {
    "price": 27879.5,
    "quantity": 1.5,
  }
}
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|bid|[Bid](#bid)|True|Current best bid of the market|
|ask|[Ask](#ask)|True|Current best ask of the market|


## Get Orderbook

`GET /orderbook`

Returns a snapshot of the current L2 orderbook for the specified market. Bids are sorted in descending order, and asks are sorted in ascending order. Because it is an L2 snapshot, bids and asks are aggregated by price level.

> Sample Request

```json
{
	"exchange": "binance",
	"base_asset": "BTC",
	"quote_asset": "USDT"
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|String|True|Exchange to fetch data from|
|base_asset|String|True|Base asset of market|
|quote_asset|String|True|Quote asset of market|

<aside class="notice">
  <code>exchange</code> parameter is lowercase, Ex: 'binance', 'coinbase'. Update for <code>exchange</code> to become UPPERCASE will rollout. 
</aside>
 
> Successful Sample Response

```json
{
  "bids": [
    {                       //  Bid Data Type
      "price": 27000.00,
      "quantity": 1.5,
    },
    {
      "price": 26000.00,
      "quantity": 5.0,
    }
  ],
  "asks": [
    {                       //  Ask Data Type
      "price": 27500.00,
      "quantity": 1,
    },
    {
      "price": 29000.00,
      "quantity": 10.0,
    }
  ]
}

```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|bids|[[Bid](#bid)]|True|List of buy orders — Bid data type. See Schema.|
|asks|[[Ask](#ask)]|True|List of sell orders — Ask data type. See Schema.|

## Get Trades

`GET /trades`

Returns trades for the specified market within the specified time window. 

The default pageSize is 50, and the default pageNumber is 0 (pages are 0-indexed).

If neither startTime or endTime is specified, the server will return the first page of the most recent trades. The client may choose to specify just a startTime, just an endTime, or both.

Trades are returned in increasing order of their timestamp.

> Sample Request

```json
{
  "exchange": "binance",
  "baseAsset": "BTC",
  "quoteAsset": "USDT"
}
```
<aside class="notice">
Specifying <code>startTime</code>, <code>endTime</code>,<code>pageSize</code>,and <code>pageNumber</code> are currently a work in progress. Currently, this endpoint provides users with the most recent trade which occured.
</aside>

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|String|True|Exchange to fetch data from.|
|baseAsset|String|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|
|startTime|Float (f64)|null|Start time for fetching data (unix timestamp)|
|endTime|Float (f64)|null|End time for fetching data (unix timestamp)|
|pageSize|Integer (i32)|50|Page size for paginated responses|
|pageNumber|Integer (i32)|0|Page number for paginated responses|

<aside class="notice">
  <code>exchange</code> parameter is lowercase, Ex: 'binance', 'coinbase'. Update for <code>exchange</code> to become UPPERCASE will rollout. 
</aside>

> Successful Sample Response

```json
{
    "exchange_market": {
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