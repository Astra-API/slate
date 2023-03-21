
<h1 id="astra-api">Astra API v0.1.0</h1>

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

<h1 id="astra-api-default">Public HTTP API</h1>

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

*Fetch current price*

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

*Fetch current BBO*

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
    "size": 1.5,
    "side": "buy"
  },
  "ask": {
    "price": 27879.5,
    "size": 1.5,
    "side": "sell"
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
|price|number|true|Price of the order (in units of quoteAsset)|
|size|number|true|Size of the order (in units of baseAsset)|
|side|[Side](#side)|true|Buy or sell|

### Ask

|Name|Type|Required|Description|
|---|---|---|---|---|
|price|number|true|Price of the order (in units of quoteAsset)|
|size|number|true|Size of the order (in units of baseAsset)|
|side|[Side](#side)|true|Buy or sell|

## Get Orderbook

`GET /orderbook`

*Fetch current orderbook*

Returns a snapshot of the current L2 orderbook for the specified market. Bids are sorted in descending order, and asks are sorted in ascending order. Because it is an L2 snapshot, bids and asks are aggregated by price level.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|string|true|Exchange to fetch data for|
|baseAsset|string|true|Base asset of market|
|quoteAsset|string|true|Quote asset of market|

> 404 Response

```json
{
  "message": "The specified market was not found"
}
```

### Response

## Get Trades

`GET /trades`

*Fetch last trades*

Returns trades for the specified market within the specified time window. 
The default pageSize is 50, and the default pageNumber is 0 (pages are 0-indexed).
If neither startTime or endTime is specified, the server will return the first page of the most recent trades. The client may choose to specify just a startTime, just an endTime, or both.
Trades are returned in increasing order of their timestamp.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|string|true|Exchange to fetch data for|
|baseAsset|string|true|Base asset of market|
|quoteAsset|string|true|Quote asset of market|
|startTime|string(date-time)|false|Start time for fetching data|
|endTime|string(date-time)|false|End time for fetching data|
|pageSize|integer(int32)|false|Page size for paginated responses|
|pageNumber|integer(int32)|false|Page number for paginated responses|

> Example Response

```json
[]
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|» *anonymous*|any|false|none|

## Get Balances

`GET /balances`

*Fetch balances*

Fetches the balances of all assets for the specified account on the exchange. This includes deposits, collateral and open positions.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|string|true|Exchange to fetch data for|

> Example Response

```json
[
  {
    "asset": "BTC",
    "amount": 1.21
  },
  {
    "asset": "ETH",
    "amount": 5.67
  },
  {
    "asset": "SOL",
    "amount": 10.11
  }
]
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|*anonymous*|[[Balance](#balance)]|false|[Balance of an asset on an exchange]|
|» asset|number|true|Asset symbol|
|» amount|number|true|Size of balance (in units of the asset)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ExchangeApiKeyAuth, DexPrivateKeyAuth
</aside>

## Place Order

`POST /order`

*Place order*

Places an order on the exchange.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|string|true|Exchange to fetch data for|
|baseAsset|string|true|Base asset of market|
|quoteAsset|string|true|Quote asset of market|
|price|number(float)|true|Price of order (in units of quoteAsset)|
|size|number(float)|true|Size of order (in units of baseAsset)|
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

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ExchangeApiKeyAuth, DexPrivateKeyAuth
</aside>

## Cancel Order

`DELETE /order`

*Cancel order*

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

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ExchangeApiKeyAuth, DexPrivateKeyAuth
</aside>

# Schemas

## Size

<a id="schemasize"></a>
<a id="schema_Size"></a>
<a id="tocSsize"></a>
<a id="tocssize"></a>

```json
1.5

```

Quantity of an asset

### Properties

|Name|Type|Required|Description|
|---|---|---|---|---|
|*anonymous*|number(float)|false|Quantity of an asset|

## Side

<a id="schemaside"></a>
<a id="schema_Side"></a>
<a id="tocSside"></a>
<a id="tocsside"></a>

```json
"buy"

```

Buy or sell

### Properties

|Name|Type|Required|Description|
|---|---|---|---|---|
|*anonymous*|string|false|Buy or sell|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|buy|
|*anonymous*|sell|

## Order

<a id="schemaorder"></a>
<a id="schema_Order"></a>
<a id="tocSorder"></a>
<a id="tocsorder"></a>

```json
{
  "price": 27879.5,
  "size": 1.5,
  "side": "buy"
}

```

Order on an orderbook. Could represent the aggregate of multiple orders at a price level

### Properties

|Name|Type|Required|Description|
|---|---|---|---|---|
|price|number|true|Price of the order (in units of quoteAsset)|
|size|number|true|Size of the order (in units of baseAsset)|
|side|[Side](#side)|true|Buy or sell|

## Orderbook

<a id="schemaorderbook"></a>
<a id="schema_Orderbook"></a>
<a id="tocSorderbook"></a>
<a id="tocsorderbook"></a>

```json
{
  "bids": [
    {
      "price": 27879.5,
      "size": 1.5,
      "side": "buy"
    }
  ],
  "asks": [
    {
      "price": 27879.5,
      "size": 1.5,
      "side": "sell"
    }
  ]
}

```

Orderbook containing a list of bids and offers, aggregated by price level

### Properties

|Name|Type|Required|Description|
|---|---|---|---|---|
|bids|[[Bid](#bid)]|true|[Buy order on an orderbook]|
|asks|[[Ask](#ask)]|true|[Sell order on an orderbook]|

## OrderId

<a id="schemaorderid"></a>
<a id="schema_OrderId"></a>
<a id="tocSorderid"></a>
<a id="tocsorderid"></a>

```json
"123456789"

```

ID of an order on an exchange

### Properties

|Name|Type|Required|Description|
|---|---|---|---|---|
|*anonymous*|string|false|ID of an order on an exchange|

## Balance

<a id="schemabalance"></a>
<a id="schema_Balance"></a>
<a id="tocSbalance"></a>
<a id="tocsbalance"></a>

```json
{
  "asset": 0,
  "amount": 0
}

```

Balance of an asset on an exchange

### Properties

|Name|Type|Required|Description|
|---|---|---|---|---|
|asset|number|true|Asset symbol|
|amount|number|true|Size of balance (in units of the asset)|

## Trade

<a id="schematrade"></a>
<a id="schema_Trade"></a>
<a id="tocStrade"></a>
<a id="tocstrade"></a>

```json
{
  "price": 0,
  "size": 0,
  "side": "buy",
  "timestamp": 0
}

```

A trade that has occurred

### Properties

|Name|Type|Required|Description|
|---|---|---|---|---|
|price|number|true|Price of the trade (in units of quoteAsset)|
|size|number|true|Size of the trade (in units of baseAsset)|
|side|[Side](#side)|true|Whether the taker bought or sold the baseAsset|
|timestamp|[Timestamp](#timestamp)|false|Exchange timestamp for when the trade took place|

## Timestamp

<a id="schematimestamp"></a>
<a id="schema_Timestamp"></a>
<a id="tocStimestamp"></a>
<a id="tocstimestamp"></a>

```json
0

```

Timestamp of an event on an exchange

### Properties

|Name|Type|Required|Description|
|---|---|---|---|---|
|*anonymous*|integer(int32)|false|Timestamp of an event on an exchange|

## Error

<a id="schemaerror"></a>
<a id="schema_Error"></a>
<a id="tocSerror"></a>
<a id="tocserror"></a>

```json
{
  "message": "The specified market was not found"
}

```

An error message from the API server

### Properties

|Name|Type|Required|Description|
|---|---|---|---|---|
|message|string|true|Error message|

