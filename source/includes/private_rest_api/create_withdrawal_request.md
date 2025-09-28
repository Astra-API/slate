## Create Withdrawal Request

`POST /withdrawal-request/{account_id}`

Creates a new withdrawal request for a specific account. The withdrawal will begin processing immediately. You can track the status using the [Get Withdrawal Requests](#get-withdrawal-requests) endpoint

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|account_id|UUID|True|The account ID to create the withdrawal request for|

### Request Body

|Field|Type|Required|Description|
|---|---|---|---|
|instrumentSymbol|String|True|The asset symbol to withdraw (e.g., "BTC", "ETH", "USDC")|
|amount|String|True|The amount to withdraw (as decimal string)|
|network|String|True|The blockchain network for the withdrawal (e.g., "bitcoin", "ethereum", "base")|
|address|String|True|The destination address for the withdrawal|

> Sample Request

```json
{
  "instrumentSymbol": "BTC",
  "amount": "0.001",
  "network": "bitcoin",
  "address": "bc1qexample1234567890abcdef1234567890"
}
```

> Sample Response

```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000"
}
```

### Response

|Name|Type|Description|
|---|---|---|
|id|String|Unique identifier for the withdrawal request (UUID)|
