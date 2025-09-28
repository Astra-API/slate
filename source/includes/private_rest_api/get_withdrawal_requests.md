## Get Withdrawal Requests

`GET /withdrawal-request/{account_id}/all`

Fetches all withdrawal requests for a specific account. Returns a list of withdrawal requests with their current status, amounts, and transaction details.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|account_id|UUID|True|The account ID to fetch withdrawal requests for|

> Sample Response

```json
[
  {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "createdAt": "2024-01-15T10:30:00Z",
    "symbol": "BTC",
    "amount": "0.5",
    "transferType": "withdrawal",
    "status": "completed",
    "metadata": null,
    "updatedAt": "2024-01-15T10:35:00Z",
    "network": "bitcoin",
    "address": "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa",
    "error": null,
    "networkTxId": "0x1234567890abcdef1234567890abcdef12345678"
  },
  {
    "id": "550e8400-e29b-41d4-a716-446655440001",
    "createdAt": "2024-01-14T15:20:00Z",
    "symbol": "ETH",
    "amount": "2.0",
    "transferType": "withdrawal",
    "status": "processing",
    "metadata": null,
    "updatedAt": "2024-01-14T15:25:00Z",
    "network": "ethereum",
    "address": "0x742d35Cc6634C0532925a3b8D4C9db96C4b4d8b6",
    "error": null,
    "networkTxId": null
  }
]
```

### Response

The response is a JSON array of withdrawal request objects, ordered by creation date (most recent first).

|Name|Type|Description|
|---|---|---|
|id|String|Unique identifier for the withdrawal request (UUID)|
|createdAt|String|ISO 8601 timestamp when the withdrawal request was created|
|symbol|String|The asset symbol being withdrawn (e.g., "BTC", "ETH", "USDC")|
|amount|String|The amount to be withdrawn (as decimal string)|
|transferType|String|Always "withdrawal" for withdrawal requests|
|status|String|Current status of the withdrawal request|
|metadata|Object or null|Additional metadata associated with the withdrawal|
|updatedAt|String|ISO 8601 timestamp when the withdrawal request was last updated|
|network|String|The blockchain network for the withdrawal (e.g., "bitcoin", "ethereum")|
|address|String|The destination address for the withdrawal|
|error|String or null|Error message if the withdrawal failed|
|networkTxId|String or null|The blockchain transaction ID (prefixed with "0x" for Ethereum)|

### Withdrawal Status Values

|Status|Description|
|---|---|
|pending|Withdrawal request is pending approval|
|processing|Withdrawal is being processed|
|sent|Withdrawal has been sent to the blockchain|
|completed|Withdrawal has been confirmed on the blockchain|
|failed|Withdrawal failed due to an error|
