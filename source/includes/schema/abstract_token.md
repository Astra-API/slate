## AbstractToken

Represents an abstract "token" such as BTC, ETH, USD, USDT, etc. This will usually refer to a
fungible blockchain token, but could potentially refer to other token-like assets such as equities,
etc.

This representation is agnostic to implementation details such as the network and token standard,
such as ERC-20 or TRC-20 or SPL. 

It is also agnostic to any particular exchange's symbology. For example, Bitcoin from both Binance
and BitMEX will map to an `AbstractToken` of `BTC`, even though Binance refers to Bitcoin as 'BTC'
and BitMEX refers to Bitcoin as 'XBT'.

*NOTE:* We do incorporate the exchange's symbology into our market symbols! So our symbol for the
BTC/USDT spot market on Binance is `BINANCE_SPOT_BTC_USDT`, while our symbol for the same market on
BitMEX (once we enable support for BitMEX) will be `BITMEX_SPOT_XBT_USD` - because BitMEX uses 'XBT'
to refer to Bitcoin and uses 'USD' rather than 'USDT' as the quote asset for this market. However,
when you fetch the `MarketMetadata` for both these markets using our `/markets` endpoint, they will
both have a `baseAsset` of `BTC`.

|AbstractToken|Description|
|---------|-----------|
|BTC|Bitcoin|
|ETH|Ether|
|SOL|Solana|
|XRP|Ripple|
|...|...|

<aside class="notice">
We are in the process of adding an endpoint that will return all the `AbstractToken`s in our
symbology, along with their descriptions.
</aside>

<!-- The assets are "abstract" in the sense that they doesn't necessarily
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
exchanges think of as a single spot asset. -->