## Asset

An asset represents a financial instrument that holds value and can be bought, sold, or exchanged. Astra represents assets with an `Asset`. There are four `Asset` types: SPOT, PERPETUAL, DATED FUTURE, OPTION.

<!-- Currently, Astra provides support for SPOT and PERPETUALS. -->

Example 1: 

Developers uses `Asset` to specify the type of base asset within a `Market`. For examples, refer to `Market` and `Subscription` messages. 

### SPOT Asset

> Sample SPOT

```json
{
    "type": "SPOT",
    "asset": "BTC"
}
```

A SPOT asset is an asset bought and sold for immediate delivery and settlement. Astra represents these through `SPOT`. 

<!-- Example 1:

Developers uses `SPOT`, a type of `Asset`, to specify the type of base asset within a `Market`. For examples, refer to `Market` and `Subscription` messages.  -->


|Name|Type|Required|Description|
|---|---|---|---|---|
|type|String|True|Type of asset: SPOT|
|asset|[[Abstract Spot Asset](#abstract-spot-asset)]|True|Name of asset|

### PERPETUAL Asset

> Sample PERPETUAL

```json
{
    "type": "PERPETUAL",
    "underlying": "BTC"
}
```

A perpetual is derivative financial instrument that tracks the price of an underlying asset, allowing traders to speculate on its value without an expiration date or the need for physical delivery. Astra represents perpetuals through `PERPETUAL`.

|Name|Type|Required|Description|
|---|---|---|---|---|
|type|String|True|Type of asset: PERPETUAL|
|underlying|[[Abstract Spot Asset](#abstract-spot-asset)]|True|Name of asset|

### DATED FUTURE Asset

A dated future is a derivative financial contract, specifying the purchase or sale of an asset at a predetermined price, with settlement occurring on a specific future date. Astra represents dated futures through `DATED_FUTURE`.

> Sample DATED FUTURE

```json
{
    "type": "DATED_FUTURE",
    "underlying": "BTC",
    "expiry": "DATE"  // format for date TBD
}
```

|Name|Type|Required|Description|
|---|---|---|---|---|
|type|String|True|Type of asset: PERPETUAL|
|underlying|[[Abstract Spot Asset](#abstract-spot-asset)]|True|Name of asset|
|expiry|TBD|True|When the contract expires|

### OPTION Asset

> Sample OPTION

```json
{
    "type": "OPTION",
    "underlying": "BTC",
    "strike": 350000,
    "expiry": "DATE", // format for date TBD
    "durationType": "MONTHLY"  // format for date TBD
}
```

Astra represents PERPETUAL through a `baseAsset` implementation holding `type`, `underlying`, `strike`, `expiry`, and `duration_type`.


|Name|Type|Required|Description|
|---|---|---|---|---|
|type|String|True|Type of asset: PERPETUAL|
|underlying|[[Abstract Spot Asset](#abstract-spot-asset)]|True|Name of asset|
|strike|Unisigned Integer (u32)|True|Strike price of the option|
|expiry|TBD|True|When the contract expires|
|duration_type|String|True|Duration type of the option|

<aside class="notice">
Possible values for <code>duration_type</code> are Daily, Weekly, Monthly, Quarterly.
</aside>


## Abstract Spot Asset

Represents an abstract spot asset such as BTC, ETH, USD, USDT, etc.
The assets are "abstract" in the sense that they doesn't necessarily
correspond to a single fungible token - there is variation with regard to
network, custody, etc.

For example, USDC could refer to USDC on any network: Ethereum, Solana, etc.
These are all technically distinct assets, which we think of as equivalent
due to the creation/redemption mechanism maintained by Circle across all
networks.

Similarly, BTC could refer to Bitcoin custodied on Binance,
Coinbase, self-custody, etc. When you custody an asset on a centralized
exchange, what you actually own is just a "deposit", which is an IOU from
the exchange that you can redeem for the underlying asset. These are subject
to different counterparty risks depending on the exchange, and are arguably
not the same asset.

So for simplicity, we use AbstractSpotAsset to represent what most users and
exchanges think of as a single spot asset.

