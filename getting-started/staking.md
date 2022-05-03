# Staking & Position Rewards

## Staking

Staking is available under https://app.fodl.finance/staking.

FODL currently has two staking mechanisms: (1) LP-Staking and (2) single currency staking (xFODL). Both mechanisms allow users to participate in the [FODL DAO](https://fodl-1.gitbook.io/fodl-1/getting-started/dao) resolutions with voting power proportional to the user’s holdings.

A total of 200,000,000 FODL are allocated to staking rewards over a 3-year period since the project's inception. From this amount, 150,000,000 FODL are allocated to LP Staking across multiple chains. The remaining 50,000,000 FODL are allocated to single-sided staking in the xFODL staking contract.&#x20;

### **LP Staking**&#x20;

LP Staking is available on:&#x20;

* Ethereum, Sushiswap pools: FODL-ETH and FODL-USDC&#x20;
* Polygon, Quickswap pool: FODL-WMATIC&#x20;
* BNB Chain, Pancakeswap pool: FODL-WBNB.&#x20;

The LP rewards are designed to mitigate impermanent loss risk for participants and to reward liquidity providers with a bonus for locking up their capital. The intention is both to reduce price volatility by increasing the liquidity, and to minimize arbitrage opportunities across different pools and chains.

After staking, users can claim the rewards accrued at any time. The reward rate is constant within a week, but the amount of rewards allocated to each week is decreasing based on a polynomial curve.&#x20;

### **Single-Sided Staking (xFODL)**&#x20;

Users can lock their FODL token in the contract and receive the fully liquid derivative token xFODL. The xFODL token can later be redeemed at the contract for the principal plus staking rewards. There is no lockup or vesting period associated with xFODL.

After staking, users can claim the rewards accrued at any time. The rewards are distributed at a constant rate over a 3-year period.&#x20;

## Position Rewards

Position rewards are given for all open positions on the FODL platform and your individual rewards can be found [here](https://app.fodl.finance/rewards).

A total of 400,000,000 FODL are allocated over a 4-year period since the platform's inception. Half are reserved for future events like trading contests governed by the DAO, while the other half are distributed every month following a decreasing curve that incentivizes early adopters.

Once distributed, rewards are subject to a 12-month lock-up period. During the lock-up period, users can claim their rewards by paying an early withdrawal penalty proportional to the amount of time remaining from the lock-up. For instance, after 1 month users are entitled to 1/12 of their rewards and the penalty they would need to pay is 11/12 of their rewards. The early withdrawal penalties are sent to this [fee address](https://etherscan.io/address/0x9bC4B846317040ee649416924C5C5BA4bd16f10c) for future community use.

By design, positions can be weighted differently for reward emissions. Rewards are calculated based on total TVL and these additional weights:&#x20;

* 20% are going to be correlated FODL Positions (USDC-USDC, USDC-DAI, ETH-ETH, etc.)&#x20;
* 80% are going to other positions (ETH-BTC, ETH-USDC, etc.)
