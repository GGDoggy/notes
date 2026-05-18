---
title: RL_QF

---

# Autonomous Representation Learning in High-Frequency Markets

- Traditional algorithmic trading and high-frequency market-making rely heavily on hand-crafted, microscopic features (e.g., order book imbalance, micro-price) to forecast market dynamics.
- While statistically robust, these legacy data science approaches fail to capture the complex, non-linear, high-dimensional latent structures inherent in modern electronic markets.
- This project proposes a *paradigm shift*: bypassing manual feature engineering to learn intrinsic, self-supervised representations of High-Frequency Markets (HFMs) directly from raw sequential transaction data.
- Leveraging recent breakthroughs in *Joint-Embedding Predictive Architectures (JEPA)* and *World Models*, we aim to build a foundational model for market dynamics capable of simultaneous multi-task forecasting and autonomous planning (market making) across Limit Order Book (LOB) and Automated Market Maker (AMM).



## Research Roadmap & Architecture

```
[Raw HFM Sequence Data] ──> [Stage 1: JEPA Latent Encoder] ──> [Stage 2: Multi-Task Predictor] ──> [Stage 3: World Model Planner]
```

### Stage 1: Self-Supervised Representation Learning

- Instead of predicting raw, noisy tick-level data, we utilize the JEPA framework to extract high-dimensional latent states $s_t \in \mathbb{R}^d$ from raw sequence inputs. 
- As a core validation metric, the learned representations must robustly capture and reconstruct standard, well-known microstructural features. 

### Stage 2: Multi-Task Supervised Dynamics

Using the frozen or fine-tuned latent embeddings, we train a unified network to predict the holistic evolution of LOB and AMM state variables. Rather than optimizing for a single, isolated metric (like mid-price direction), the model simultaneously forecasts:

- Volume-Weighted Average Price (VWAP) trajectories.
- Order Flow Dynamics (Limit Orders (LO), Market Orders (MO), and cancellation rates).
- Tick-Level Fill Probabilities and post-fill toxic order returns.


## Stage 3: Model-Based Planning & Market Making

- We introduce agent actions (e.g., passive limit orders, liquidity provisioning) directly into the learned latent space.
- By constructing an end-to-end World Model (akin to *LeWorldModel* architectures), an autonomous agent can simulate market rollouts internally.
- This allows us to derive optimal market-making policies that natively navigate the trade-off between fill probability and adverse selection, completely bypassing simplified or fragile mathematical assumptions.


## Data Scope & Environment
We target highly active, data-rich venues across both Web2 and Web3 ecosystems:

- *Centralized/Order Book (LOB)*: Level 2 tick data from Hyperliquid, Binance, and Polymarket.
- *Decentralized/AMM*: Granular pool transaction and liquidity event data from Uniswap.



## References
- LeCun, Y. (2022). A path towards autonomous machine intelligence [Position paper]. OpenReview. https://openreview.net/forum?id=BZ5a1r-kVsf
- Terver, B., Balestriero, R., Dervishi, M., Fan, D., Garrido, Q., Nagarajan, T., Sinha, K., Zhang, W., Rabbat, M., LeCun, Y., & Bar, A. (2026). A lightweight library for energy-based joint-embedding predictive architectures. arXiv. https://doi.org/10.48550/arXiv.2602.03604
- Balestriero, R., & LeCun, Y. (2025). LeJEPA: Provable and scalable self-supervised learning without the heuristics. arXiv. https://doi.org/10.48550/arXiv.2511.08544
- Kuang, Y., Dagade, Y., Rudner, T. G., Balestriero, R., & LeCun, Y. (2026). Rectified LpJEPA: Joint-embedding predictive architectures with sparse and maximum-entropy representations. arXiv. https://doi.org/10.48550/arXiv.2602.01456
- Maes, L., Lidec, Q. L., Scieur, D., LeCun, Y., & Balestriero, R. (2026). LeWorldModel: Stable end-to-end joint-embedding predictive architecture from pixels. arXiv. https://doi.org/10.48550/arXiv.2603.19312
- Avellaneda, M., & Stoikov, S. (2008). High-frequency trading in a limit order book. Quantitative Finance, 8(3), 217–224. https://doi.org/10.1080/14697680701381228
- Albers, J., Cucuringu, M., Howison, S., & Shestopaloff, A. Y. (2025). The market maker's dilemma: Navigating the fill probability vs. post-fill returns trade-off. arXiv. https://doi.org/10.48550/arXiv.2502.18625