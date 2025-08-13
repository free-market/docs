# Hooks

### Overview

In Pathfinder, hooks are automated triggers that manage liquidity dynamically within the yield pipeline. They ensure that users always have immediate access to their funds while maintaining continuous yield generation. Specifically, hooks work in two main phases: a **pre-transaction hook** that unwinds enough of the yield stack to satisfy a withdrawal or spending request, and a **post-transaction hook** that re-deploys any excess stablecoins back into the yield pipeline.

### How It Works

#### Pre-Transaction Hook

* **Trigger:** When a user initiates a transaction (such as a withdrawal, swap, or purchase) that requires stablecoins.
* **Operation:**
  * The hook calculates the exact amount needed.
  * It automatically unwinds the necessary layers in the yield stack—starting from the topmost layer—converting the stacked yield tokens back into stablecoins.
  * The Liquidity Vault is leveraged to quickly supply any additional shortfall.
* **Outcome:**
  * The required stablecoins are made available instantly, ensuring that the transaction proceeds without delay.

#### Post-Transaction Hook

* **Trigger:** Once the user’s transaction is complete.
* **Operation:**
  * The hook checks for any stablecoins left over after the transaction.
  * It then automatically re-sweeps (re-deposits) the surplus funds back into the yield pipeline, preserving the optimized yield strategy.
* **Outcome:**
  * Residual funds continue earning yield without requiring further user intervention, maintaining an efficient “set-and-forget” system.

#### Emergency Hook (Optional)

* **Trigger:** In cases of a risk event, such as a stablecoin depeg or protocol exploit.
* **Operation:**
  * The emergency hook bypasses standard procedures and unwinds the entire yield stack immediately.
* **Outcome:**
  * All assets are converted back to stablecoins, protecting user funds from cascading losses.

### Technical Workflow

1. **Detection and Calculation:**
   * Upon a transaction initiation, the hook system analyzes the required stablecoin amount by reading real-time data from the yield pipeline and liquidity vault.
2. **Automated Unwinding:**
   * The system calls pre-defined functions in the Brevity scripts that systematically redeem tokens from the highest yield layers down to the baseline.
3. **Liquidity Coordination:**
   * If the internal pipeline does not provide enough liquidity, the Liquidity Vault is tapped to bridge the shortfall.
4. **Re-Sweeping:**
   * After the transaction completes, the post-transaction hook triggers a rebalancing function, ensuring any excess stablecoins are re-invested into the appropriate yield layers.
5. **Monitoring and Logging:**
   * All hook events are logged and monitored via integrated oracles and dashboards to ensure transparency and for audit purposes.

### Benefits

* **Instant Access:**\
  Users experience near-instant liquidity even when their funds are deployed in complex yield strategies.
* **Seamless Automation:**\
  Automated hooks remove the need for manual intervention, ensuring that yield generation continues uninterrupted while meeting withdrawal demands.
* **Optimized Yield Retention:**\
  By re-sweeping leftover funds, the system maximizes yield retention, ensuring that assets are always deployed to earn returns.
* **Risk Mitigation:**\
  Emergency hooks provide a rapid fallback mechanism, protecting users during critical events by unwinding the entire pipeline swiftly.
