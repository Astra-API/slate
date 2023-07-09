## Place Order

`POST /orders`

Places an order on the exchange.

> Sample Request

```json
{
    "exchange": "BINANCE",
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
|exchange|[[Exchange](#exchange)]]|True|Exchange to fetch data for|
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
|*anonymous*|Integer (i32)|true|ID of an order on an exchange|