# Fees

FODL fees are designed to be simple to understand, transparently calculated on-chain, and low.&#x20;

### **Reward Token Fees**&#x20;

FODL takes 10% of governance token rewards from the underlying platform. For example, when a user has a position open on Compound, they will receive COMP rewards for supplying and borrowing assets. Once the position is closed, these rewards are claimed and 10% of them are taken into the FODL treasury.&#x20;

### **Trading Fees**&#x20;

FODL takes a small fee of 0.1% on principal when the position is closed.&#x20;

### **Exchange Fees**&#x20;

FODL relies on 3rd party decentralized exchangers (e.g. Uniswap V3, QuickSwap, PancakeSwap) to execute trades. The fees taken by such exchanges are usually between 0.05% and 0.3% and are reflected in the price impact displayed when executing a transaction.&#x20;

### **Profit Share Fees**&#x20;

FODL takes a 2.5% profit share fee whenever a position is (partially) closed. When the position is partially closed, the withdrawn value is broken down into the principal that contributed towards this value (taxed at 0.1%) and the profit (taxed at 2.5%). If the position does not close in profit, FODL does not take any additional fee.

### **How are FODL fees used?**&#x20;

The goal is to provide a low-risk, forgiving fee structure where the protocol mostly takes fees from profits derived from using the platform. A few examples of possibilities:&#x20;

* FODL buybacks on the LP pools to refill rewards contracts or fuel future development grants.&#x20;
* Direct token profit share (either the native tokens that are in the pool or conversion to stable coins).&#x20;
* Reward token fees provide a leverage trading experience with fully decentralized liquidity, where users’ positions pay their own funding rates.

It's up to the FODL DAO to decide!

