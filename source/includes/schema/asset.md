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
