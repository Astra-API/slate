# Schema

Astra's strength is consolidating data from (eventually) numerous exchanges into a singular, easily distributable unified data format. Below is a list of these formats which help define how developers can interact with data sent to and received from Astra.

## Market

> Sample Data

```json
 {
    "baseAsset": {
        "type": "SPOT",
        "asset": "BTC"
    },
    "quoteAsset": "USDT"
  }
```

Astra represent asset pairs across every exchange through `Markets`. It is made up of two elements, `baseAsset` and `quoteAsset` which fully represent a particular market. For usage, refer to 'Public HTTP API' > 'Get Markets'.

|Name|Type|Required|Description|
|---|---|---|---|---|
|baseAsset|[[Base Asset](#base-asset)]|True|Describes the type and name of asset|
|quoteAsset|[[Quote Asset](#quote-asset)]|True|Asset which price is in units of.|

## Base Asset

Astra represents `baseAsset` as a struct of `type` and `asset`. Currently, Astra provides
support for SPOT and PERPETUALS.

The implementation of Asset can change depending on the type of Asset you are trying to fetch data on. Below are the specific formats for SPOT, 

### SPOT Asset

> Sample SPOT

```json
{
    "type": "SPOT",
    "asset": "BTC"
}
```

Astra represents SPOT through a `baseAsset`implementation holding `type` and `asset`.

|Name|Type|Required|Description|
|---|---|---|---|---|
|type|String|True|Type of asset: SPOT|
|asset|String|True|Name of asset|

### PERPETUAL Asset

> Sample PERPETUAL

```json
{
    "type": "PERPETUAL",
    "underlying": "BTC"
}
```

Astra represents PERPETUAL through a `baseAsset` implementation holding `type` and `underlying`.

|Name|Type|Required|Description|
|---|---|---|---|---|
|type|String|True|Type of asset: PERPETUAL|
|underlying|String|True|Name of asset|

<aside class="notice">
PERPETUAL assets supported for Binance only. Rollout of PERPETUAL for other exchanges (OKX, COINBASE, HUOBI) to arrive within a couple days.
</aside>

### DATED FUTURE Asset

<aside class="notice">
Astra currently supports SPOT and PERPETUAL assets. Support for DATED FUTURES and OPTIONS is currently a work in progress.
</aside>

> Sample DATED FUTURE

```json
{
    "type": "DATED_FUTURE",
    "underlying": "BTC",
    "expiry": "DATE"  // format for date TBD
}
```

Astra represents PERPETUAL through a `baseAsset` implementation holding `type`, `underlying`, and `expiry`.

|Name|Type|Required|Description|
|---|---|---|---|---|
|type|String|True|Type of asset: PERPETUAL|
|underlying|String|True|Name of asset|
|expiry|TBD|True|When the contract expires|

### OPTION Asset

<aside class="notice">
Astra currently supports SPOT and PERPETUAL assets. Support for DATED FUTURES and OPTIONS is currently a work in progress.
</aside>

> Sample OPTION

```json
{
    "type": "DATED_FUTURE",
    "underlying": "BTC",
    "strike": 350000,
    "expiry": "DATE", // format for date TBD
    "duration_type": "Monthly"  // format for date TBD
}
```

Astra represents PERPETUAL through a `baseAsset` implementation holding `type`, `underlying`, `strike`, `expiry`, and `duration_type`.


|Name|Type|Required|Description|
|---|---|---|---|---|
|type|String|True|Type of asset: PERPETUAL|
|underlying|String|True|Name of asset|
|strike|Unisigned Integer (u32)|True|Strike price of the option|
|expiry|TBD|True|When the contract expires|
|duration_type|String|True|Duration type of the option|

<aside class="notice">
Possible values for <code>duration_type</code> are Daily, Weekly, Monthly, Quarterly.
</aside>

## Quote Asset

> Sample data

```json
{
    "quoteAsset": "USDT"
}
```

Astra represents `quoteAsset` as a String. The quote asset is the units of price for which the base asset is quoted for.



## Bid

> Sample Data

```json
//  This is a sample Bid in relation to the 
//  BTC USDT Market example above.
{
    "price": 27879.5,
    "quantity": 1.5,
}
```

Astra represents bids across every exchange through this `Bid` which is a struct of `price` and `quantity`. `price` is represented in units of the quote asset (`Market`'s quoteAsset). `quantity` is represented in units of the base asset (`Market`'s baseAsset). For usage, refer to 'Public HTTP API' > 'Get BBO'. 

|Name|Type|Required|Description|
|---|---|---|---|---|
|price|Float|True|Price of the bid (in units of quoteAsset)|
|quantity|Float|True|Quantity of the bid (in units of baseAsset)|

## Ask

> Sample Data

```json
//  This is a sample Ask in relation to the 
//  BTC USDT Market example above.
{
    "price": 27500.00,
    "quantity": 1,
}
```


Astra represents bids across every exchange through this `Ask` which is a struct of `price` and `quantity`. `price` is represented in units of the quote asset (`Market`'s quoteAsset). `quantity` is represented in units of the base asset (`Market`'s baseAsset). For usage, refer to 'Public HTTP API' > 'Get BBO'. 

|Name|Type|Required|Description|
|---|---|---|---|---|
|price|number|True|Price of the ask (in units of quoteAsset)|
|quantity|number|True|Quantity of the ask (in units of baseAsset)|


## Subscription

> Sample Data

```json
{
    "exchange": "BINANCE",
    "market": {
        "baseAsset": "BTC",
        "quoteAsset": "USDT"
    },
    "dataType": "ORDERBOOK"
}
```

Subscription messages are the unified data format Astra requires from developers to communicate to all supported exchange websocket endpoints. Astra defines
a `subcription` as a struct of an `exchange`, `market`, and `dataType`.


|Name|Type|Required|Description|
|---|---|---|---|---|
|exchange|String|True|Exchange to fetch data from.|
|market|[[Market](#market)]|True|Market details. See Schema > #Market.|
|dataType|String|True|Type of market updates.|

<aside class="notice">
Possible values for <code>dataType</code> are TRADE and ORDERBOOK. 
</aside>

## Trade 

> Sample Data

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

Astra represents all trades across all platforms through this `trade` which holds information about the `exchange`, what `market` was traded and relevant details: `price`, `quantity`, and `side` of taker. 

|Name|Type|Required|Description|
|---|---|---|---|---|
|exchange_market|[[Exchange Market](#exchange-market)]|True|Contains exchange and market which was traded|
|price|Float (f64)|True|Price of trade units of quote asset|
|quantity| Float (f64)|True|Quantity of trade in units of base asset|
|side|String|True|Direction of taker|

### Exchange Market
|Name|Type|Required|Description|
|---|---|---|---|---|
|exchange|String|True|Exchange to fetch data from.|
|price|Float (f64)|True|Price of trade units of quote asset|


## Order

> Sample Data

```json
{
    "id": "123456789",
    "baseAsset": {
      "type": "SPOT",
      "asset": "BTC"
    }, 
    "quoteAsset": "USD",
    "price": 20000.00,
    "quantity": 1.2,
    "side": "buy"
  }
```

Astra represents all orders you've initiated in this `order` similar to a `trade` object, in addition to including the specific order `id` tied to the order.

<aside class="success">
Similarity in order and trade objects is intuitive! <code>trade</code> updates recieved from Astra are <code>order</code> from other traders.
</aside>

|Name|Type|Required|Description|
|---|---|---|---|---|
|id|String|True|ID of the order on the exchange|
|baseAsset|[[Base Asset](#base-asset)]|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|
|price|number|True|Price of the order (in units of quoteAsset)|
|quantity|number|True|Quantity of the order (in units of baseAsset)|
|side|String|True|Buy or sell order|