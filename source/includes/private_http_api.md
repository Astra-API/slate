# Private HTTP API

<aside class="warning">
Support for Private HTTP API is not yet released.
</aside>

## Get Orders

`GET /orders`

Fetches the user's open orders for the specified market.

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
|baseAsset|String|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|

<aside class="notice">
  <code>exchange</code> parameter is lowercase, Ex: 'binance', 'coinbase'. Update for <code>exchange</code> to become UPPERCASE will rollout. 
</aside>

> Successful Sample Response

```json
[
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
  },
  {
    "id": "2345678910",
    "baseAsset": {
      "type": "SPOT",
      "asset": "ETH"
    }, 
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
|-|[[Order]](#order)|True|List of open orders|


## Get Balances

`GET /balances`

Fetches the user's balances of all assets on the exchange. This includes deposits, collateral and open positions.

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

<aside class="notice">
  <code>exchange</code> parameter is lowercase, Ex: 'binance', 'coinbase'. Update for <code>exchange</code> to become UPPERCASE will rollout. 
</aside>

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

## Place Order

`POST /orders`

Places an order on the exchange.

> Sample Request

```json
{
    "exchange": "binance",
    "base_asset": "BNB",
    "quote_asset": "BTC",
    "side": "BUY",
    "price": "0.0075",
    "quantity": "1"
}
```
### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|String|True|Exchange to fetch data for|
|baseAsset|String|True|Base asset of market|
|quoteAsset|String|True|Quote asset of market|
|price|number(float)|True|Price of order (in units of quoteAsset)|
|quantity|number(float)|True|Quantity of order (in units of baseAsset)|
|side|String|True|Side of order|
|timeInForce|String|false|Time in force for order|
|miscOptions|object|false|Miscellaneous params to send to the exchange|

#### Enumerated Values

|Parameter|Value|
|---|---|
|side|buy|
|side|sell|
|timeInForce|GTC|
|timeInForce|IOC|
|timeInForce|FOK|

> Successful Sample Response

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
|exchange|String|True|Exchange to fetch data for|
|orderId|String|True|ID of an order on an exchange|

> 404 Response

```json
{
  "message": "The specified market was not found"
}
```

### Response

