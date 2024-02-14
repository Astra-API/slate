---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  # - python
  # - javascript
  # - shell

toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  # - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

# Order of files determines outline of website
includes:
  - intro
  - getting_started

  # - auth/intro

  - public_rest_api/intro
  - public_rest_api/get_markets
  # - public_rest_api/get_price
  # - public_rest_api/get_bbo
  - public_rest_api/get_orderbook
  # - public_rest_api/get_trades

  
  - websockets/intro
  - websockets/subscribing
  - websockets/orderbook_updates
  - websockets/trade_updates

  - private_rest_api/intro
  - private_rest_api/get_orders
  - private_rest_api/get_fills
  - private_rest_api/get_balances
  - private_rest_api/get_positions
  - private_rest_api/place_order
  - private_rest_api/cancel_order

  - schema/intro
  # - schema/format_of_parameters
  - schema/exchange
  - schema/market
  - schema/market_metadata
  - schema/asset_type
  # - schema/asset
  - schema/abstract_token
  - schema/data_type
  - schema/bid
  - schema/ask
  - schema/trade
  # - schema/order
  # - schema/subscription

  - self_hosting
search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Astra API
---

