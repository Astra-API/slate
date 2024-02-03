## Market

> Sample Data

Represents a particular market on a particular trading venue.

```bash
# Format for spot and perpetual futures markets:
{EXCHANGE}-{ASSET_TYPE}-{BASE_ASSET}-{QUOTE_ASSET}-?{DISAMBIGUATOR}

# Format for expiring futures markets:
{EXCHANGE}-{ASSET_TYPE}-{BASE_ASSET}-{QUOTE_ASSET}-{EXPIRY_SYMBOL}-?{DISAMBIGUATOR}

# Format for options markets:
{EXCHANGE}-{ASSET_TYPE}-{BASE_ASSET}-{QUOTE_ASSET}-{EXPIRY_SYMBOL}-{STRIKE_SYMBOL}-?{DISAMBIGUATOR}
```

Astra has developed a custom naming scheme to represent crypto markets across many diverse trading venues. Every tradeable market is assigned a "market symbol", which is a string that serves as the globally unique identifier for that market. The market symbol is also human-readable, and contains information about the exchange, base asset, quote asset, and metadata of that market.

On the right, you can see the format of market symbols for four popular asset types: spot, perpetual futures, expiring futures, and options.

"Disambiguator" is an optional parameter which is used to differentiate markets that are the same on all other parameters. For example, many exchanges have two types of futures contracts which differ in their margin behavior: those margined in USD or stablecoins (usually called "USD-margined" or "USD-M"), and those margined in the underlying base asset of the market (usually called "coin-margined" or "Coin-M"). To differentiate these, we use the "-COINM" disambiguator for coin-margined markets, and no disambiguator for USD-margined markets, which are more popular.

Here are some examples of various market symbols, along with descriptions of the markets they map to:


| Market Symbol Example          | Description                                              |
|--------------------------------|----------------------------------------------------------|
| BINANCE-SPOT-BTC-USDT          | Binance BTC/USDT spot market                             |
| BINANCE-PERP-BTC-USDT          | Binance USD-margined BTC/USDT perpetual futures          |
| BINANCE-PERP-BTC-USD-COINM     | Binance coin-margined BTC/USD perpetual futures          |
| COINBASE-SPOT-BTC-USD          | Coinbase BTC/USD spot market                             |
| OKX-FUT-BTC-USDT-210625        | OKX BTC/USDT futures, expiring on 2021-06-25            |
| BINANCE-OPT-BTC-USDT-210625-50000-C | Binance BTC/USDT options, strike price 50000, expiring on 2021-06-25 |
| ...                            | ...                                                      |