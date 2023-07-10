## Place Order

`POST /orders`

<aside class="warning">
Support for Place Order is a work in progress.
</aside>

> Sample Request

```json
{
    "exchange": "BINANCE",
    "baseAsset": "BNB",
    "quoteAsset": "BTC",
    "side": "BUY",
    "price": "0.0075",
    "quantity": "1"
}
```
### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|exchange|[Exchange](#exchange)|True|Exchange to fetch data for|
|baseAsset|[Asset](#asset)|True|Base asset of market|
|quoteAsset|[Abstract Spot Asset](#abstract-spot-asset)|True|Quote asset of market|
|price|Float (f64)|True|Price of order (in units of quoteAsset)|
|quantity|Float (f64)|True|Quantity of order (in units of baseAsset)|
|side|[Side](#side)|True|Side of order|
|timeInForce|[Time In Force](#time-in-force)|False|Time in force for order|
|miscOptions|object|False|Miscellaneous params to send to the exchange|

### Side 

|Value|Description|
|---|---|
|SELL|Taker is selling the asset|
|BUY|Taker is buying the asset|

### Time in Force

|Value|Description|
|---|---|
|GTC|Good 'til Cancelled order|
|IOC|Immediate or Cancel Order|
|FOK|Fill or Kill Order|

> Successful Sample Response

```json
[
  "123456789"
]
```

### Response

|Name|Type|Required|Description|
|---|---|---|---|---|
|-|Integer (i32)|True|ID of an order on an exchange|