# Pathfinder Liquidity Layer

Overview:

The Liquidity Layer is Pathfinder’s real-time cash desk.

It ensures that any user can move money instantly — whether that’s paying a bill, swapping assets, or cashing out — without waiting for other investments to unwind.\


**Think of it like a payment network combined with a high-yield reserve account:**

* It processes instant withdrawals and payments (like Visa/Mastercard do for purchases)
* But instead of holding all the cash idle, it keeps part of it earning yield until it’s needed

\


Key Roles:

* Tier A (Instant Liquidity) — same-block access for withdrawals and payments.
* Tier B (Short-Notice Reserves) — yield-earning assets that can be unwound in hours to a day.
* Tier C (Long-Duration Reserves) — high-return positions with longer unwind times.
* Flow Control — automatically rebalances between tiers to match usage patterns.

\


Why It’s Like a Payment Network:

* Transactions are instant for the user, even though back-end settlement and fund rebalancing happen later.
* Tiers act like settlement buffers, just as card networks keep reserve accounts to handle surges in payments.

\


Unique to DeFi:

* Tiers B & C aren’t idle reserves — they’re actively deployed in external protocols.
* Reserve ratios are dynamic, adjusting in real time.
* Fully transparent and auditable on-chain.

\


Example Flow:

1. User requests $5M withdrawal from Tier A.
2. Tier B backfills Tier A within seconds.
3. Yield Stack begins unwinding a $5M position from Tier C to restore Tier B balance.

