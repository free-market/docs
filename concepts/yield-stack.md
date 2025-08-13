# Yield Stack

**Overview:**

The Yield Stack is Pathfinder’s decision engine for yield. It finds, scores, and allocates capital into DeFi and tokenized real-world asset strategies, all while keeping enough liquidity for instant withdrawals.

\


**Key Roles:**

* Strategy Discovery — scans across chains for the best yield opportunities.
* Scoring Engine — ranks options based on yield, risk, and liquidity profile.
* Dynamic Allocation — decides how much goes into short-term vs. long-term yield strategies (Tiers B & C).
* Real-Time Adjustment — responds to liquidity spikes by pulling funds back to Tier A instantly.

\


**Unique to DeFi:**

* Composability allows stacking yield strategies.
* No rebuild needed to integrate new protocols.
* Instant settlement between tiers.

\


**Example Capital Flow:**

* $100M TVL
* $10M in Tier A (instant liquidity)
* $25M in Tier B (short-term yield, 1–2 day unwind)
* $65M in Tier C (long-term yield, 3–7 day unwind)

***
