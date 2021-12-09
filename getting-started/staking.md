# Staking/Position Rewards

## Staking

FODL currently has two staking mechanisms: LP-Staking and single currency staking. A total of 200,000,000 FODL are allocated for staking over 3 years since project inception. xFODL and LP-Holders will be able to participate in [DAO ](dao.md)resolutions equally based on their holdings.&#x20;

From this amount 50M are allocated to single sided staking in the xFODL staking contract. Users can lock their FODL token in the contract and receive the fully liquid derivative token xFODL back that can be later redeemed at the contract for the principal plus staking rewards. There is no lockup or vesting period attached to this.&#x20;

The other 150M are allocated to LP Staking to make sure that the FODL liquidity pools are always filled with sufficient liquidity to also support larger trade sizes and dampen price volatility and arbitraging between the two pools. The LP rewards are designed to subsidize impermanent loss risk for participants and to reward liquidity providers with a bonus for locking up their capital.&#x20;

LP-Staking is available for the two original Sushi pools FODL-ETH and FODL-USDC. Staking is available under [https://app.fodl.finance/staking](https://app.fodl.finance/staking). Since the total amount of rewards in this pool is three times higher there is a lockup and vesting period attached:

One third (1/3) of the rewards are directly available after each rewards period which is one week. Two thirds (2/3) are vesting over 12 Months with a 6 Months cliff. This means the rewards unlock linearly after 6 Months for 6 Months i.e:

* Alice is entitled to 1500 FODL as reward from LP staking.
* 500 FODL can be claimed immediately
* After 6 Months \~167 FODL can be claimed every month for a period of 6 Months

Note: In a future release on the UI the unlocking schedule of entitled users will be shown more clearly as of current only the currently claimable rewards are visible.

## Position Rewards

Position rewards are given for all open positions on the FODL platform and your individual rewards can be found [here](https://app.fodl.finance/rewards). A total of 400,000,000 $FODL is allocated for position rewards in 4 years after the platform's inception. 200,000,000 are reserved for future events like trading contests on the FODL platform which will be governed by the DAO. The other 200,000,000 are distributed every month following a decreasing curve.&#x20;

Rewards are subject to a 12 months lock up period after they are accounted for. During the lock up period, users can claim their rewards by paying an early withdrawal fee proportional with the amount of time remaining from the lock up:

* After 1 month users are entitled to 1/12 of their rewards. After 2 months users are entitled to 2/12 of their rewards etc.
* Claiming before the full 12 months period is over will put all non vested rewards into this [fee address](https://etherscan.io/address/0x9bC4B846317040ee649416924C5C5BA4bd16f10c) for future community use.

Positions can be by design weighted differently for reward emissions. This will be later turned over to the DAO. Rewards are calculated based on total TVL and these additional weights:

* 20% are going to perfectly correlated FODL Positions (USDC-USDC, USDC-DAI, ETH-ETH etc.)
* 80% are going to other positions (ETH-BTC, ETH-USDC, etc.)

The current 20/80 split is designed to drive trading on the platform which is what mostly drives the projects revenue and therefore the communities revenue.
