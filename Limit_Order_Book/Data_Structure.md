# Order book

## Simplification

Because
- buying / selling an `up` is equivalent to selling / buying a `down`
- the book of `up` and `down` is basically the same empirically (with a flip of sign)
one can consider the book of `up` token only. Which already contains all information of the order book(s).
## Columns

- `timestamp`: seconds (or ms) starts from the begin of market.
- `bid_price_i`
- `bid_volume_i`
- `ask_price_i`
- `ask_volume_i`
`i` means the i'th price-volume pair from the best price, which can be limited by the data source or selected manually.
# Trade

Due to the same reason from the order book part, information of trades can be reduced to consider buying / selling of the `up` token only.

## Columns

- `timestamp`: same as the orderbook part
- `side`: `-1` for `buy` maker (`sell` taker) and `+1` for `sell` maker (`buy` taker.)
- `price`
- `volume`

# Event

The information from the target to be predicted. In our case is the crypto market.

Maybe consists of prices / orderbooks from different exchange platforms.