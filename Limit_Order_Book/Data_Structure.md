# Polymakret Modeling


## Polymakret Data

Because
- buying / selling an `up` is equivalent to selling / buying a `down`
- the book of `up` and `down` is basically symmetric
we only need to consider the `up` token only, which already captures the relevant state information.

S.N.: Good point — the symmetry halves the state space without loss of information.

### Data types

#### Raw data

##### Order book

- `timestamp`: time in seconds or milliseconds since the market opened, maybe normalized to `[0, 1]`.
- `bid_price_i`
- `bid_volume_i`
- `ask_price_i`
- `ask_volume_i`
Here, `i` ranges from $0$ to $N$ and denotes the $i$'th price-volume level from the best price. $N$ may be determined by the data source or chosen manually.

S.N.: Reasonable; this frames each order book snapshot as a $(2N+1)$-dimensional vector.

##### Trade

- `timestamp`: same structure as the orderbook's
- `side`: `-1` for `buy` maker (`sell` taker) and `+1` for `sell` maker (`buy` taker.)
- `price`
- `volume`

S.N.: Does every trade event generate a corresponding book update? If so, snapshot labels could distinguish limit orders, market orders, and cancellations.

#### Derived data

##### Prices

##### Spread

- `spread`: `ask_price_0` - `bid_price_0`

##### Depth

- `bid_depth_i`: sum over `bid_volume_j` with `j` goes from `0` to `i`
- `ask_depth_i`: same structure as `bid_depth_i`

##### Imbalance

- `imbalance_i`: `bid_depth_i` - `ask_depth_i`

##### Spread

##### Order flow

### Others

This category includes information about the asset or market that the prediction market refers to. In our case, this is the crypto market.

It may include prices or order book snapshots from multiple exchanges. Each source should contain at least a `timestamp` column.


## Input data structure

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

S.N.: Rather than indexing by raw timestamp, I would prefer bundling a fixed number of snapshots per latent update — this pins the input dimension and enables direct checks on what the latent encodes (volume, fill rate, book imbalance, etc.). The sequence model would then operate on successive latents during supervised learning.


**To do:** Enumerate microstructure LOB features (spread, book imbalance, depth, fill rate, order flow) to serve as interpretability benchmarks for latent quality.

## Benchmark data structure