# Simplification

Because
- buying / selling an `up` is equivalent to selling / buying a `down`
- the book of `up` and `down` is basically symmetric
we only need to consider the `up` token, which already captures the relevant state information.

# Data types

## Order book

### Columns

- `timestamp`: time in seconds or milliseconds since the market opened, maybe normalized to `[0, 1]`.
- `bid_price_i`
- `bid_volume_i`
- `ask_price_i`
- `ask_volume_i`
Here, `i` ranges from $0$ to $N$ and denotes the $i$'th price-volume level from the best price. $N$ may be determined by the data source or chosen manually.
## Trade

### Columns

- `timestamp`: same structure as the orderbook's
- `side`: `-1` for `buy` maker (`sell` taker) and `+1` for `sell` maker (`buy` taker.)
- `price`
- `volume`

## Others

This category includes information about the asset or market that the prediction market refers to. In our case, this is the crypto market.

It may include prices or order book snapshots from multiple exchanges. Each source should contain at least a `timestamp` column.

# Input data structure

To represent the market state, the *latent*  must be generated from all historical data. If the latent is formed from limited information, we will definitely loose *some knowledge*, even if we don't know exactly what is lost.

Accordingly, I imagine the model should be something RNN/LSTM-like, so we can continuously feed in new data to update the latent. In general, it can be expressed as

$$
l_{i+1} = f(l_i, X_{t-\tau})
$$
where
- $f$ is the update model
- $l_i$ is the i'th latent with $l_0=0$
- $X_t$ is some information of the market with timestamp $t$
- $\tau$ is the delay time between the data being generated and collected

For different types of data, I imagine that different versions of $f$ can be traind to update the same latent respectively. Therefore, for now, I will keep each type of data separate.