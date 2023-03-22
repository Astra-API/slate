
# Introduction

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

This is the reference documentation for Astra's unified crypto trading API. Each client will
be provided a binary to run on their own machines, which exposes the following API over localhost.
The API provides a common interface and data format to a wide variety of exchanges and DEXes.

NOTE: Astra's API is still in active development, so the information on this page will likely change
as we converge on our stable API interface. The Astra team will notify clients of all changes as they occur.

Base URLs:

* <a href="http://localhost:6789">http://localhost:6789</a>

# Authentication

* API Key (ExchangeApiKeyAuth)
    - Parameter Name: **X-EXCHANGE-API-KEY**, in: header. 

* API Key (DexPrivateKeyAuth)
    - Parameter Name: **X-DEX-PRIVATE-KEY**, in: header. 

# Public HTTP API

## Get Markets

`GET /markets`

Returns all markets listed by the specified exchange

> Example Request

```json
{
  "exchange": "binance"
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|string|true|Exchange to fetch data for|

> Example Response

```json
[
  {
    "baseAsset": "BTC",
    "quoteAsset": "USDT"
  },
  {
    "baseAsset": "ETH",
    "quoteAsset": "USDT"
  },
  {
    "baseAsset": "SOL",
    "quoteAsset": "USDT"
  }
]
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|[[Market](#market)]|true|List of markets|

### Market

|Name|Type|Required|Description|
|---|---|---|---|---|
|baseAsset|string|true|Base asset of the market|
|quoteAsset|string|true|Quote asset of the market|

## Get Price

`GET /price`

Returns the current price of the specified market

> Example Request

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
|exchange|string|true|Exchange to fetch data for|
|baseAsset|string|true|Base asset of market|
|quoteAsset|string|true|Quote asset of market|

> Example Response

```json
27879.5
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|number(float)|true|Price of the asset|

## Get BBO

`GET /bbo`

Returns the current BBO of the specified market

> Example Request

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
|exchange|string|true|Exchange to fetch data for|
|baseAsset|string|true|Base asset of market|
|quoteAsset|string|true|Quote asset of market|

> Example Response

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
|bid|[Bid](#bid)|true|Buy order on an orderbook|
|ask|[Ask](#ask)|true|Sell order on an orderbook|

### Bid

|Name|Type|Required|Description|
|---|---|---|---|---|
|price|number|true|Price of the bid (in units of quoteAsset)|
|quantity|number|true|Quantity of the bid (in units of baseAsset)|

### Ask

|Name|Type|Required|Description|
|---|---|---|---|---|
|price|number|true|Price of the ask (in units of quoteAsset)|
|quantity|number|true|Quantity of the ask (in units of baseAsset)|

## Get Orderbook

`GET /orderbook`

Returns a snapshot of the current L2 orderbook for the specified market. Bids are sorted in descending order, and asks are sorted in ascending order. Because it is an L2 snapshot, bids and asks are aggregated by price level.

> Example Request

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
|exchange|string|true|Exchange to fetch data for|
|baseAsset|string|true|Base asset of market|
|quoteAsset|string|true|Quote asset of market|

> Example Response

```json
{
  "bids": [
    {
      "price": 27000.00,
      "quantity": 1.5,
    },
    {
      "price": 26000.00,
      "quantity": 5.0,
    }
  ],
  "asks": [
    {
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
|bids|[[Bid](#bid)]|true|List of buy orders|
|asks|[[Ask](#ask)]|true|List of sell orders|

## Get Trades

`GET /trades`

Returns trades for the specified market within the specified time window. 

The default pageSize is 50, and the default pageNumber is 0 (pages are 0-indexed).

If neither startTime or endTime is specified, the server will return the first page of the most recent trades. The client may choose to specify just a startTime, just an endTime, or both.

Trades are returned in increasing order of their timestamp.

> Example Request

```json
{
  "exchange": "binance",
  "baseAsset": "BTC",
  "quoteAsset": "USDT",
  "startTime": 1679443991.61,
  "endTime": 1679444001.61,
  "pageSize": 50,
  "pageNumber": 0
}
```

### Request

|Parameter|Type|Default|Description|
|---|---|---|---|
|exchange|string|*required*|Exchange to fetch data for|
|baseAsset|string|*required*|Base asset of market|
|quoteAsset|string|*required*|Quote asset of market|
|startTime|integer(int32)|null|Start time for fetching data (unix timestamp)|
|endTime|integer(int32)|null|End time for fetching data (unix timestamp)|
|pageSize|integer(int32)|50|Page size for paginated responses|
|pageNumber|integer(int32)|0|Page number for paginated responses|

> Example Response

```json
[
  {
    "price": 0,
    "quantity": 0,
    "side": "buy",
    "timestamp": 0
  },
  {
    "price": 0,
    "quantity": 0,
    "side": "sell",
    "timestamp": 0
  }
]

```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|[[Trade]](#trade)|true|List of trades|

### Trade

|Name|Type|Required|Description|
|---|---|---|---|---|
|baseAsset|string|true|Base asset of market|
|quoteAsset|string|true|Quote asset of market|
|price|number|true|Price of the trade (in units of quoteAsset)|
|quantity|number|true|Quantity of the trade (in units of baseAsset)|
|side|[Side](#side)|true|Whether the taker bought or sold the baseAsset|
|timestamp|integer(int32)|true|Exchange timestamp for when the trade took place|

### Side

|Value|Description|
|---|---|
|» buy|Represents a buy order or trade|
|» sell|Represents a sell order or trade|

# Private HTTP API

## Get Orders

`GET /orders`

Fetches the user's open orders for the specified market.

> Example Request

```json
{
  "exchange": "binance",
  "baseAsset": "BTC",
  "quoteAsset": "USDT"
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|string|true|Exchange to fetch data for|
|baseAsset|string|true|Base asset of market|
|quoteAsset|string|true|Quote asset of market|

> Example Response

```json
[
  {
    "id": "123456789",
    "baseAsset": "BTC",
    "quoteAsset": "USD",
    "price": 20000.00,
    "quantity": 1.2,
    "side": "buy"
  },
  {
    "id": "2345678910",
    "baseAsset": "ETH",
    "quoteAsset": "USD",
    "price": 1200.00,
    "quantity": 2.4,
    "side": "sell"
  }
]
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|[[Order]](#order)|true|List of open orders|

### Order

|Name|Type|Required|Description|
|---|---|---|---|---|
|id|string|true|ID of the order on the exchange|
|baseAsset|string|true|Base asset of market|
|quoteAsset|string|true|Quote asset of market|
|price|number|true|Price of the order (in units of quoteAsset)|
|quantity|number|true|Quantity of the order (in units of baseAsset)|
|side|[Side](#side)|true|Buy or sell order|

## Get Balances

`GET /balances`

Fetches the user's balances of all assets on the exchange. This includes deposits, collateral and open positions.

> Example Request

```json
{
  "exchange": "binance"
}
```

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|string|true|Exchange to fetch data for|

> Example Response

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
|*asset symbol*|number|false|Quantity of balance (in units of the asset)|

## Place Order

`POST /orders`

Places an order on the exchange.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|string|true|Exchange to fetch data for|
|baseAsset|string|true|Base asset of market|
|quoteAsset|string|true|Quote asset of market|
|price|number(float)|true|Price of order (in units of quoteAsset)|
|quantity|number(float)|true|Quantity of order (in units of baseAsset)|
|side|string|true|Side of order|
|timeInForce|string|false|Time in force for order|
|miscOptions|object|false|Miscellaneous params to send to the exchange|

#### Enumerated Values

|Parameter|Value|
|---|---|
|side|buy|
|side|sell|
|timeInForce|GTC|
|timeInForce|IOC|
|timeInForce|FOK|

> Example Response

```json
[
  "123456789"
]
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|*anonymous*|[[OrderId](#orderid)]|false|[ID of an order on an exchange]|

## Cancel Order

`DELETE /orders`

Cancels an order on the exchange.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|string|true|Exchange to fetch data for|
|orderId|string|true|ID of an order on an exchange|

> 404 Response

```json
{
  "message": "The specified market was not found"
}
```

### Response

