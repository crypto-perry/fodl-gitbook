# Fees

Fodl fees are designed to be simple to understand, transparently calculated on-chain, and low.

### Reward Token Fees

* FODL takes 10% of governance token rewards from the underlying position.&#x20;
  * i.e. when a user opens a folded position on Compound, they will receive a certain APR in $COMP.&#x20;
* The FODL protocol will take 10% of those $COMP tokens as the margin funding rate.&#x20;

### Profit Share Fees

* FODL takes 2.5% profit share of appreciating long or short positions.&#x20;
* 2.5% is only applied to profit, not principal.
  * i.e. if the position does not close in profit, FODL does not take any additional fee&#x20;

### Trading Fees

* FODL takes a small principal fee of 0.1%. This fee is taken from the unleveraged principal and the amount does therefore not change with the chosen leverage.
* FODL relies on Uniswap V3 and trading fees occur depending on the pool the trades are routed through with flash swaps.&#x20;

### Purpose of Fees

* Reward token fees provide a leverage trading experience with fully decentralized liquidity, where users’ positions pay their own funding rates.&#x20;
* The goal is to provide a low risk, forgiving fee structure where the protocol mostly takes fees from profits derived from using the protocol.&#x20;

### How are FODL fees used?

All revenue that the platform generates is controlled by the DAO. The DAO is able to decide how to use the revenue. A few examples of possibilities:

* FODL buybacks on the Sushi LP to refill rewards contracts or fuel future development grants
* Direct token profit share (Either the native tokens that are in the pool or conversion to stable coin)

