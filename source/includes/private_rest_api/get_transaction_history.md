## Get Transaction History

`GET /transactions/{account_id}`

Fetches the full raw transaction history for a specific account. Any operation that credits or debits this account is considered a "transaction". So deposits, withdrawals, and fees will all show up as transactions, OTC trades will show up as two transactions (one for each asset involved in the trade). This endpoint is usually only used for things like reporting, balance reconciliation, etc. To get more detailed info about specific types of transactions, see the following endpoints:

- [Get OTC History](#get-otc-history),
- [Get Transfer History](#get-transfer-history)
- [Get Withdrawal Requests](#get-withdrawal-requests)

### Request

|Parameter|Type|Required|Description|
|---|---|---|---|
|account_id|UUID|True|The account ID to fetch transaction history for|

> Sample Response

```json
[
  {
    "displayId": "550e8400-e29b-41d4-a716-446655440000",
    "instrumentId": "550e8400-e29b-41d4-a716-446655440001",
    "symbol": "BTC",
    "amount": "0.001",
    "debitFrom": "550e8400-e29b-41d4-a716-446655440002",
    "creditTo": "550e8400-e29b-41d4-a716-446655440000",
    "notes": "Deposit",
    "createdAt": "2024-01-15T10:30:00Z",
    "idemKey": "deposit_123",
    "type": "deposit",
    "tradeDisplayId": null
  },
  {
    "displayId": "550e8400-e29b-41d4-a716-446655440003",
    "instrumentId": "550e8400-e29b-41d4-a716-446655440004",
    "symbol": "ETH",
    "amount": "1.5",
    "debitFrom": "550e8400-e29b-41d4-a716-446655440000",
    "creditTo": "550e8400-e29b-41d4-a716-446655440005",
    "notes": "OTC Trade",
    "createdAt": "2024-01-14T15:20:00Z",
    "idemKey": "trade_456",
    "type": "trade",
    "tradeDisplayId": "550e8400-e29b-41d4-a716-446655440006"
  }
]
```

### Response

The response is a JSON array of transaction objects, ordered by creation date (most recent first).

|Name|Type|Description|
|---|---|---|
|displayId|String|Unique display identifier for the transaction (UUID)|
|instrumentId|String|Instrument ID for the asset involved in the transaction|
|symbol|String|Symbol of the asset (e.g., "BTC", "ETH", "USDC")|
|amount|String|Transaction amount (as decimal string)|
|debitFrom|String|Account ID that was debited (money taken from)|
|creditTo|String|Account ID that was credited (money given to)|
|notes|String or null|Additional notes about the transaction|
|createdAt|String|ISO 8601 timestamp when the transaction was created|
|idemKey|String or null|Idempotency key for the transaction|
|type|String or null|Transaction type: "deposit", "withdrawal", "trade", "fee", or null|
|tradeDisplayId|String or null|Display ID of the associated trade (if this transaction is part of a trade)|

### Transaction Types

|Type|Description|
|---|---|
|deposit|Incoming funds to the account|
|withdrawal|Outgoing funds from the account|
|trade|Transaction related to a trade (buy/sell)|
|fee|Fee charged for a service|
|null|Other transaction types or legacy transactions|
