# Brevity

### Overview

Brevity is a language, similar in syntax to Solidity, that is transpiled into an EVM\
transaction and executed via a smart contract interpreter. Because Brevity is interpreted\
rather than compiled, it does not require deploying new smart contracts to implement each\
additional workflow. Every Pathfinder user has their own Brevity Interpreter smart contract,\
which costs only about 90,000 gas to deploy using the clones pattern.

\
**Key Features of the Brevity Interpreter**

\
• **All-in-One General-Purpose Contract**: Each user deploys a dedicated interpreter\
contract owned by them. The same contract can run multiple workflows without new\
code deployments.\
• **Guardrails**: Pathfinder’s configuration applies restrictions on which external methods\
can be called, reducing potential attack surfaces.\
• **Metering**: The protocol tracks native (ETH) and ERC-20 outflows from the Brevity\
Interpreter, ensuring user-specific quotas or security rules.\
• **MetaTransactions**: Brevity calls can be submitted as EIP-712 meta-transactions,\
allowing wallets that hold no tokens to control the interpreter.\
• **Gas Savings**: Deploying EVM code costs around 200 gas/byte, while calldata is about\
4–16 gas/byte. Brevity places code in calldata, reducing deployment costs for one-off\
workflows.

\
By leveraging Brevity, Pathfinder can offer flexible workflows—from complex yield re-\
balancing to emergency exits—all under a single smart contract paradigm, fully controlled\
by the user.
