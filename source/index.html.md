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

  - auth/intro
  
  - public_http_api/intro
  - public_http_api/get_markets
  # - public_http_api/get_price
  # - public_http_api/get_bbo
  - public_http_api/get_orderbook
  - public_http_api/get_trades

  - private_http_api/intro
  - private_http_api/get_orders
  - private_http_api/get_fills
  - private_http_api/get_balances
  - private_http_api/get_positions
  - private_http_api/place_order
  - private_http_api/cancel_order

  - websockets/intro
  - websockets/subscribing
  - websockets/orderbook_updates
  - websockets/trade_updates

  - schema/intro
  # - schema/format_of_parameters
  - schema/bid
  - schema/ask
  - schema/exchange
  - schema/asset
  - schema/market
  - schema/subscription
  - schema/trade
  - schema/order
search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Astra API
---

