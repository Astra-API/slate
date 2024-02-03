## Ask

> Sample Data

```json
{
    "price": 27500.00,
    "quantity": 1,
}
```

Represents the aggregate of all sell orders on a particular market for a given price level.

| Name     | Type        | Required | Description                                   |
|----------|-------------|----------|-----------------------------------------------|
| price    | f64 | True     | Price of the sell orders (in units of quoteAsset)     |
| quantity | f64 | True     | Aggregated quantity of the sell orders (in units of baseAsset)   |