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
 Astra represents a trade through `Trade` on a specific market on an exchange.

|Name|Type|Required|Description|
|---|---|---|---|---|
|exchange_market|[[Exchange Market](#exchange-market)]|True|Contains exchange and market which was traded|
|price|Float (f64)|True|Price of trade units of quote asset|
|quantity| Float (f64)|True|Quantity of trade in units of base asset|
|side|String|True|Direction of taker|

### Exchange Market
|Name|Type|Required|Description|
|---|---|---|---|---|
|exchange|[[Exchange](#exchange)]]|True|Exchange to fetch data from.|
|price|Float (f64)|True|Price of trade units of quote asset|