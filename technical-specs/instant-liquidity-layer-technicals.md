# Liquidity Pool

### 5. Pathfinder Liquidity Pool — Technical Detail

#### Liquidity Tiers

| Tier               | Liquidity Time | Example Assets                                               | Role in Pool                                      |
| ------------------ | -------------- | ------------------------------------------------------------ | ------------------------------------------------- |
| **A — Immediate**  | < 1 block      | Hot wallet USDC, same-chain CCT yield tokens                 | Covers 100% of expected instantaneous withdrawals |
| **B — Short-term** | < 1 day        | On-chain lending positions, tokenized overnight repos        | Backstop for large withdrawals, low unwind risk   |
| **C — Mid-term**   | 1–7 days       | Uniswap v3/v4 LPs, tokenized treasuries, staking derivatives | Collateral for synthetic IOUs, higher yield       |

***

#### Synthetic Flash-Loan IOUs

When Tier A liquidity is insufficient for a given draw:

1. **Synthetic credit** is issued to the PLP, collateralized by Tier B/C assets.
2. Credit is repaid as positions unwind or new deposits arrive.
3. Underlying assets may continue earning yield during IOU periods.
4. Accounting is on-chain and auditable.

**Benefits:**

* Smaller Tier A footprint while guaranteeing instant liquidity.
* “Stacked yield” — fees + underlying asset yield.
* Efficient capital reuse across Pathfinder architecture.

***

#### Dynamic Pool Sizing

The allocator adjusts pool size **weekly** (or more often) based on:

* Transaction frequency and borrow size.
* VIP fee caps and utilization thresholds.
* Available synthetic capacity from Tier B/C.

**Core Formulae:**

```
F_annual = Y_target / U_target
F_per_borrow = (F_annual / turnover_per_year) * 10,000
Coverage Floor = safety_factor × peak_fraction_of_weekly_volume
```

Allocator Logic:

1. Estimate **weekly borrow demand**.
2. Target utilization (e.g., 75%).
3. If **per-borrow bps > cap**, shrink pool to raise turnover.
4. If **per-borrow bps ≪ cap** and utilization is low, grow pool.
5. Maintain a **coverage floor**.
6. Include synthetic capacity in available liquidity calculations.

***

#### User Fee Management

* **Fee Caps:** Default ≤ 10 bps (goal: ≤ 5 bps for HNW/institutional).
* **VIP Rebates:** Volume-based rebate tiers.
* **VIP Pool Participation:** High-volume users can contribute capital to PLP for a larger LP yield share.

**Example VIP Fee Schedule:**

| Tier     | Monthly Borrow Volume | Fee (bps) | Rebate % | Effective Fee (bps) |
| -------- | --------------------- | --------- | -------- | ------------------- |
| Standard | $0–$5M                | 10        | 0%       | 10                  |
| Silver   | $5–$25M               | 8         | 20%      | 6.4                 |
| Gold     | $25M+                 | 5         | 50%      | 2.5                 |

***

#### LP Yield Composition

LP yield sources:

1. **Fee Yield:** Instant liquidity fees × utilization × turnover.
2. **Portfolio Yield:** Yield from Tier B/C collateral backing synthetic IOUs.
3. **Passive Yield:** Yield on idle LP funds outside the PLP.

***

#### Risk Management

* **Liquidity Coverage Ratio (LCR):** Weighted by unwind times.
* **Stress Testing:** Model 3× peak draw and 2× tx/day spikes.
* **Synthetic IOU Limits:** Max % of Tier B/C pledgable.
* **Circuit Breaker:** Halt expansion if coverage risk exceeds threshold.

***

#### Monitoring & Telemetry

Allocator decisions are driven by:

* Tx frequency distribution
* Peak concurrent borrow % of weekly volume
* Pool turnover
* Per-borrow bps (raw & VIP effective)
* LP yield actual vs. target
