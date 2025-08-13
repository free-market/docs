# Active Yield

### Overview

Active Yield is designed to deliver dynamic, real-time yield optimization while maintaining instant liquidity. Leveraging the same yield stacking framework as Passive Yield, Active Yield uses automated pre- and post-transaction hooks to actively manage funds across multiple yield layers—such as on-chain T-bills, lending protocols, and specialized yield contracts. Additionally, it integrates a dedicated Liquidity Vault that temporarily holds a portion of assets, enhancing the speed and efficiency of unwinding the yield stack when a withdrawal is triggered.

### How It Works

* **Automated Hooks & Yield Stacking:**\
  When a user initiates a transaction, a pre-transaction hook automatically calculates the required stablecoin amount and unwinds the necessary yield layers. After the transaction, any remaining funds are promptly re-deposited into the yield stack. This mechanism allows funds to continuously earn compounded returns while remaining instantly accessible.
* **Liquidity Vault Integration:**\
  The Liquidity Vault acts as an internal reserve that holds up to 20% of user funds. It functions as a dedicated liquidity source exclusively for the yield stacking engine. When a withdrawal is requested, the vault plays a key role in rapidly supplying stablecoins. This vault mechanism is unique compared to traditional systems, as it provides a seamless “loan” to the yield engine, ensuring that funds can be quickly converted back into liquid assets.

### Comparison with TradFi Cash Sweep

In traditional finance, cash sweeps automatically transfer idle cash into short-term, interest-bearing instruments—often with delays and limited flexibility. However, individual users have little bargaining power and must rely on large deposit sizes to achieve optimal rates.

Pathfinder’s Active Yield offers a significant improvement:

* **Dynamic and Automated:**\
  While TradFi cash sweeps require periodic manual rebalancing or suffer from rigid schedule constraints, Pathfinder continuously optimizes yields with real-time automated hooks.
* **Instant Liquidity:**\
  The Liquidity Vault, in combination with automated yield unwinding, ensures that funds are available on demand—mirroring the liquidity of a checking account.
* **Enhanced Yield Stacking:**\
  Instead of a single cash sweep vehicle, Pathfinder stacks multiple yield layers. This composability means users can capture higher compounded returns than would be possible with a traditional money market account.
* **User and Platform Control:**\
  With non-custodial management, users maintain full control of their assets, and platforms can leverage collective bargaining power to secure better yield terms—something individual investors in TradFi rarely achieve.

### Benefits

* **Optimized Returns:**\
  Active Yield maximizes overall returns by dynamically compounding yield from multiple layers.
* **Immediate Access:**\
  Automated hooks and the Liquidity Vault ensure near-instant fund availability, offering a seamless user experience.
* **Competitive Advantage:**\
  By integrating advanced yield stacking and real-time liquidity management, Pathfinder outperforms traditional cash sweep models and standard DeFi aggregators.
* **Scalable and Adaptive:**\
  The system continuously recalibrates based on market data, ensuring that yield strategies remain competitive while adhering to defined risk parameters.
