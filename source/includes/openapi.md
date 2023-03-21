
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

## Get markets

> Code samples

`GET /markets`

Returns all markets listed by the specified exchange

### Parameter

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|exchange|query|string|true|Exchange to fetch data for|

> Example responses

> 200 Response

```json
[
  {
    "baseAsset": "BTC",
    "quoteAsset": "USD"
  },
  {
    "baseAsset": "ETH",
    "quoteAsset": "USD"
  },
  {
    "baseAsset": "SOL",
    "quoteAsset": "USD"
  }
]
```

### Response

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[Error](#schemaerror)|

### Response Schema

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Market](#schemamarket)]|false|none|[A single market on an exchange]|
|» baseAsset|string|true|none|Base asset of the market|
|» quoteAsset|string|true|none|Quote asset of the market|

<aside class="success">
This operation does not require authentication
</aside>

## getPrice

> Code samples

`GET /price`

*Fetch current price*

Returns the current price of the specified market

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|exchange|query|string|true|Exchange to fetch data for|
|baseAsset|query|string|true|Base asset of market|
|quoteAsset|query|string|true|Quote asset of market|

> Example responses

> 200 Response

```json
27879.5
```

### Response

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[Price](#schemaprice)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[Error](#schemaerror)|

<aside class="success">
This operation does not require authentication
</aside>

## getBbo

> Code samples

`GET /bbo`

*Fetch current BBO*

Returns the current BBO of the specified market

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|exchange|query|string|true|Exchange to fetch data for|
|baseAsset|query|string|true|Base asset of market|
|quoteAsset|query|string|true|Quote asset of market|

> Example responses

> 200 Response

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

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[Bbo](#schemabbo)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[Error](#schemaerror)|

<aside class="success">
This operation does not require authentication
</aside>

## getOrderbook

> Code samples

`GET /orderbook`

*Fetch current orderbook*

Returns a snapshot of the current L2 orderbook for the specified market. Bids are sorted in descending order, and asks are sorted in ascending order. Because it is an L2 snapshot, bids and asks are aggregated by price level.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|exchange|query|string|true|Exchange to fetch data for|
|baseAsset|query|string|true|Base asset of market|
|quoteAsset|query|string|true|Quote asset of market|

> Example responses

> 404 Response

```json
{
  "message": "The specified market was not found"
}
```

### Response

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[Error](#schemaerror)|

### Response Schema

<aside class="success">
This operation does not require authentication
</aside>

## getTrades

> Code samples

`GET /trades`

*Fetch last trades*

Returns trades for the specified market within the specified time window. 
The default pageSize is 50, and the default pageNumber is 0 (pages are 0-indexed).
If neither startTime or endTime is specified, the server will return the first page of the most recent trades. The client may choose to specify just a startTime, just an endTime, or both.
Trades are returned in increasing order of their timestamp.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|exchange|query|string|true|Exchange to fetch data for|
|baseAsset|query|string|true|Base asset of market|
|quoteAsset|query|string|true|Quote asset of market|
|startTime|query|string(date-time)|false|Start time for fetching data|
|endTime|query|string(date-time)|false|End time for fetching data|
|pageSize|query|integer(int32)|false|Page size for paginated responses|
|pageNumber|query|integer(int32)|false|Page number for paginated responses|

> Example responses

> 200 Response

```json
[]
```

### Response

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[Error](#schemaerror)|

### Response Schema

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» *anonymous*|any|false|none|none|

<aside class="success">
This operation does not require authentication
</aside>

## getBalances

> Code samples

`GET /balances`

*Fetch balances*

Fetches the balances of all assets for the specified account on the exchange. This includes deposits, collateral and open positions.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|exchange|query|string|true|Exchange to fetch data for|

> Example responses

> 200 Response

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

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[Error](#schemaerror)|

### Response Schema

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Balance](#schemabalance)]|false|none|[Balance of an asset on an exchange]|
|» asset|number|true|none|Asset symbol|
|» amount|number|true|none|Size of balance (in units of the asset)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ExchangeApiKeyAuth, DexPrivateKeyAuth
</aside>

## placeOrder

> Code samples

`POST /placeOrder`

*Place order*

Places an order on the exchange.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|exchange|query|string|true|Exchange to fetch data for|
|baseAsset|query|string|true|Base asset of market|
|quoteAsset|query|string|true|Quote asset of market|
|price|query|number(float)|true|Price of order (in units of quoteAsset)|
|size|query|number(float)|true|Size of order (in units of baseAsset)|
|side|query|string|true|Side of order|
|timeInForce|query|string|false|Time in force for order|
|miscOptions|query|object|false|Miscellaneous params to send to the exchange|

#### Enumerated Values

|Parameter|Value|
|---|---|
|side|buy|
|side|sell|
|timeInForce|GTC|
|timeInForce|IOC|
|timeInForce|FOK|

> Example responses

> 200 Response

```json
[
  "123456789"
]
```

### Response

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[Error](#schemaerror)|

### Response Schema

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[OrderId](#schemaorderid)]|false|none|[ID of an order on an exchange]|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ExchangeApiKeyAuth, DexPrivateKeyAuth
</aside>

## cancelOrder

> Code samples

`DELETE /cancelOrder`

*Cancel order*

Cancels an order on the exchange.

### Parameters

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|exchange|query|string|true|Exchange to fetch data for|
|orderId|query|string|true|ID of an order on an exchange|

> Example responses

> 404 Response

```json
{
  "message": "The specified market was not found"
}
```

### Response

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|None|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not found|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
ExchangeApiKeyAuth, DexPrivateKeyAuth
</aside>

# Schemas

<h2 id="tocS_Market">Market</h2>

<a id="schemamarket"></a>
<a id="schema_Market"></a>
<a id="tocSmarket"></a>
<a id="tocsmarket"></a>

```json
{
  "baseAsset": "BTC",
  "quoteAsset": "USD"
}

```

A single market on an exchange

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|baseAsset|string|true|none|Base asset of the market|
|quoteAsset|string|true|none|Quote asset of the market|

<h2 id="tocS_Price">Price</h2>

<a id="schemaprice"></a>
<a id="schema_Price"></a>
<a id="tocSprice"></a>
<a id="tocsprice"></a>

```json
27879.5

```

Price of an asset

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|number(float)|false|none|Price of an asset|

<h2 id="tocS_Size">Size</h2>

<a id="schemasize"></a>
<a id="schema_Size"></a>
<a id="tocSsize"></a>
<a id="tocssize"></a>

```json
1.5

```

Quantity of an asset

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|number(float)|false|none|Quantity of an asset|

<h2 id="tocS_Side">Side</h2>

<a id="schemaside"></a>
<a id="schema_Side"></a>
<a id="tocSside"></a>
<a id="tocsside"></a>

```json
"buy"

```

Buy or sell

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|Buy or sell|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|buy|
|*anonymous*|sell|

<h2 id="tocS_Bbo">Bbo</h2>

<a id="schemabbo"></a>
<a id="schema_Bbo"></a>
<a id="tocSbbo"></a>
<a id="tocsbbo"></a>

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

Best bid and offer on the market

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bid|[Bid](#schemabid)|true|none|Buy order on an orderbook|
|ask|[Ask](#schemaask)|true|none|Sell order on an orderbook|

<h2 id="tocS_Bid">Bid</h2>

<a id="schemabid"></a>
<a id="schema_Bid"></a>
<a id="tocSbid"></a>
<a id="tocsbid"></a>

```json
{
  "price": 27879.5,
  "size": 1.5,
  "side": "buy"
}

```

Buy order on an orderbook

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|price|number|true|none|Price of the order (in units of quoteAsset)|
|size|number|true|none|Size of the order (in units of baseAsset)|
|side|[Side](#schemaside)|true|none|Buy or sell|

<h2 id="tocS_Ask">Ask</h2>

<a id="schemaask"></a>
<a id="schema_Ask"></a>
<a id="tocSask"></a>
<a id="tocsask"></a>

```json
{
  "price": 27879.5,
  "size": 1.5,
  "side": "sell"
}

```

Sell order on an orderbook

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|price|number|true|none|Price of the order (in units of quoteAsset)|
|size|number|true|none|Size of the order (in units of baseAsset)|
|side|[Side](#schemaside)|true|none|Buy or sell|

<h2 id="tocS_Order">Order</h2>

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

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|price|number|true|none|Price of the order (in units of quoteAsset)|
|size|number|true|none|Size of the order (in units of baseAsset)|
|side|[Side](#schemaside)|true|none|Buy or sell|

<h2 id="tocS_Orderbook">Orderbook</h2>

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

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|bids|[[Bid](#schemabid)]|true|none|[Buy order on an orderbook]|
|asks|[[Ask](#schemaask)]|true|none|[Sell order on an orderbook]|

<h2 id="tocS_OrderId">OrderId</h2>

<a id="schemaorderid"></a>
<a id="schema_OrderId"></a>
<a id="tocSorderid"></a>
<a id="tocsorderid"></a>

```json
"123456789"

```

ID of an order on an exchange

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|string|false|none|ID of an order on an exchange|

<h2 id="tocS_Balance">Balance</h2>

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

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|asset|number|true|none|Asset symbol|
|amount|number|true|none|Size of balance (in units of the asset)|

<h2 id="tocS_Trade">Trade</h2>

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

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|price|number|true|none|Price of the trade (in units of quoteAsset)|
|size|number|true|none|Size of the trade (in units of baseAsset)|
|side|[Side](#schemaside)|true|none|Whether the taker bought or sold the baseAsset|
|timestamp|[Timestamp](#schematimestamp)|false|none|Exchange timestamp for when the trade took place|

<h2 id="tocS_Timestamp">Timestamp</h2>

<a id="schematimestamp"></a>
<a id="schema_Timestamp"></a>
<a id="tocStimestamp"></a>
<a id="tocstimestamp"></a>

```json
0

```

Timestamp of an event on an exchange

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|integer(int32)|false|none|Timestamp of an event on an exchange|

<h2 id="tocS_Error">Error</h2>

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

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|message|string|true|none|Error message|

