## Bid

> Sample Data

```json
{
    "price": 27879.5,
    "quantity": 1.5,
}
```

Represents the aggregate of all buy orders on a particular market for a given price level.

| Name     | Type | Required | Description                                   |
|----------|------|----------|-----------------------------------------------|
| price    | f64  | True     | Price of the buy orders (in units of quoteAsset)     |
| quantity | f64  | True     | Aggregated quantity of the buy orders (in units of baseAsset)   |