## Get Transfer History

`GET /transfers/{account_id}`

Fetches all transfers (deposits and withdrawals) for a specific account. Returns a list of transfers with their amounts, types, and transaction details.

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|account_id|UUID|True|The account ID to fetch transfers for|

> Sample Response

```json
[
  {
    "id": "226",
    "createdAt": "2024-01-15T10:30:00Z",
    "symbol": "BTC",
    "amount": "0.001",
    "transferType": "deposit",
    "metadata": null,
    "updatedAt": "2024-01-15T10:30:00Z"
  },
  {
    "id": "225",
    "createdAt": "2024-01-14T15:20:00Z",
    "symbol": "ETH",
    "amount": "1.5",
    "transferType": "withdrawal",
    "metadata": {
      "type": "withdrawal",
      "address": "0x1234567890abcdef1234567890abcdef12345678",
      "network": "ethereum",
      "withdrawal_id": "550e8400-e29b-41d4-a716-446655440000"
    },
    "updatedAt": "2024-01-14T15:20:00Z"
  }
]
```

### Response

The response is a JSON array of transfer objects, ordered by creation date (most recent first).

|Name|Type|Description|
|---|---|---|
|id|String|Unique identifier for the transfer (integer as string)|
|createdAt|String|ISO 8601 timestamp when the transfer was created|
|symbol|String|The asset symbol being transferred (e.g., "BTC", "ETH", "USDC")|
|amount|String|The amount transferred (as decimal string)|
|transferType|String|Type of transfer: "deposit" or "withdrawal"|
|metadata|Object or null|Additional metadata associated with the transfer. For withdrawals: contains type, address, network, and withdrawal_id. For deposits: may contain transaction details (tx object with hex, txid, vout) or be null|
|updatedAt|String|ISO 8601 timestamp when the transfer was last updated|

### Transfer Types

|Type|Description|
|---|---|
|deposit|Incoming transfer that credits the account|
|withdrawal|Outgoing transfer that debits the account|
