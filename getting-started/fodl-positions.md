# FODL Positions

On FODL, each position (trade) opened is implemented as a smart wallet (smart contract with flexible functionality) owned by the user with the following high-level features:

* Supply / borrow tokens to / from lending platforms (eg. Aave, Compound, etc.)
* Exchange tokens using decentralised exchanges (eg. Uniswap, Curve, Quickswap, etc.)
* Take flash loans and use them within a transaction (eg. DyDx, Aave, UniswapV3, etc.)
* Configure stop-loss / take-profit triggers to be executed by a decentralised network of bots

FODL uses these features as building blocks to construct financial instruments such as Long / Short positions.

> Note: Any trade is both a Long and a Short. For example, a Long ETH vs BTC trade is equivalent to a Short BTC vs ETH trade. However, when one of the assets is a stable coin, the common practice is to only refer to the trade as the direction of the non-stable coin asset. For instance, a Short ETH vs. USDC trade (aka Long USDC vs ETH) is just called “Short ETH” as the Long (supply) asset is a stable coin.

To present the trading flow and the mathematics behind it we will be using the following notations:

```
S_Amount = Amount of Supply asset on the underlying lending market
B_Amount = Amount of Borrow asset on the underlying lending market
L = Leverage multiplier
P = Principal provided by the user in Supply token
Entry_Price_B_to_S = Price of Borrow to Supply at position entry
Current_price_B_to_S = Price of Borrow to Supply at current time
Price_Change_B_to_S = Relative price change between entry and current price
Close_price_B_to_S = Price of Borrow to Supply at position close
Position_Value = Current value of the position expressed in Supply asset
```

### Trade Flow & PnL Mathematics

The FODL smart wallet uses the aforementioned features to execute the following trading flow when opening a position:

1. Flash loan Long asset of amount `L * P`
2. Take principal `P` from user
3. Supply Long asset of amount `S_Amount = (L + 1) * P`
4. Borrow Short asset of amount `B_Amount = L * P / Entry_Price_B_to_S` such that on entry it is worth exactly the flash loan amount `L * P` when measured in Long asset.
5. Exchange the Short asset borrowed into `L * P` Long asset
6. Repay the flash loan

When closing a position the trading flow is:

1. Flash loan enough Short asset to cover the full debt (i.e. `B_Amount` plus some interest which we will ignore for simplicity)
2. Repay the full debt
3. Redeem all the Long asset (i.e. `S_Amount` plus some interest which we will ignore for simplicity)
4. Exchange enough Long asset into Short asset to cover the flash loan amount. Ignoring, interest rates and fees, the amount of Long asset that needs to be exchanged is: `B_Amount * Close_Price_B_to_S`
5. Repay the flash loan
6. Return the remaining funds to user: `S_Amount - B_Amount * Close_Price_B_to_S`

So when opening / increasing the value of a position, some amount of the borrowed asset is exchanged into the supply asset and when closing / decreasing the value of a position, some amount of supplied asset is exchanged into the borrowed asset. As the amount exchanged is amplified by the leverage, so is the relative price movement of the Short asset compared to the Long asset.

More precisely, as the relative price of the assets changes, we can express the current `Position_Value` and `PnL`, measured in Long asset and ignoring interest rates on the lending market:

```
Position_Value = S_Amount - B_Amount * Current_Price_B_to_S
PnL = Position_Value - P
PnL = S_Amount - B_Amount * Current_Price_B_to_S - P
PnL = (L + 1) * P - (L * P / Entry_Price_B_to_S) * Current_Price_B_to_S - P 
PnL = L * P * (1 - Current_Price_B_to_S / Entry_Price_B_to_S) 
PnL = L * P * Price_Change_B_to_S
```

Notice how the profit or loss is directly proportional (with a factor of leverage) to the price change of the borrowed (Short) asset. See detailed examples below!

### Long Position

By going _long_, a trader opens a position with the expectation that, in the future, the underlying borrowed (Long) asset will appreciate against the borrowed (Short) asset.

{% hint style="info" %}
**Example: Long ETH**   (supply ETH & borrow USDC)

**Entry Price:** `1 ETH = 1000 USDC or 1 USDC = 0.001 ETH`

**Principal:** `100 ETH`

**Leverage:** `3x`
{% endhint %}

Your net starting position would be:

```
Supply = (Leverage + 1) * Principal = 4 * 100 = 400 ETH 
Borrow = Leverage * Principal / price_USDC_ETH = 3 * 100 / 0.001 = 300,000 USDC
Position_Value = Supply - Borrow * price_USDC_ETH = 400 - 300,000 * 0.001 = 100 ETH
```

{% hint style="success" %}
**Price change:** ETH price appreciates to 1200 USDC

**New Price:** `1 ETH = 1200 USDC or 1 USDC = 0.00083 ETH`

**Price Move:** `+20% ETH or -16.66% USDC`
{% endhint %}

While the relative price changed, the supply and borrow amounts do not change (ignoring the interest rates). Your position would now be:

```
Supply: 400 ETH
Borrow: 300,000 USDC
Position Value: 400 - 300,000 * 0.00083 = 150 ETH
Profit: 50 ETH (50% profit = 3 * 16.66% = Leverage * price drop USDC to ETH)
```

### Short Position

By going _short_, a trader opens a position with the expectation that the underlying borrowed (Short) asset will drop in value against the supplied (Long) asset in the future.

#### **Example: Short ETH**

{% hint style="info" %}
**Asset Pair:** supply USDC & borrow ETH

**Price:** `1 USDC = 0.001 ETH or 1 ETH = 1000 USDC`

**Principal:** `100,000 USDC`

**Leverage:** `3x`
{% endhint %}

Your net starting position would be:

```
Supply = (Leverage + 1) * Principal = 4 x 100,000 = 400,000 USDC
Borrow = Leverage * Principal / price_ETH_USDC = 3 * 100,000 / 1000 = 300 ETH
Position Value = Supply - Borrow * price_ETH_USDC = 400,000 - 300 * 1000 = 100,000 USDC
```

{% hint style="success" %}
**ETH prices moves to $900**

**New Price:** `1 USDC = 0.001111 ETH or 1 ETH = 900 USDC`

**Price Move:** `11.11% ETH or -10% USDC`
{% endhint %}

Your position would now be:

```
Supply: 400,000 USDC
Borrow: 300 ETH
Position Value: 400,000 - 300 * 900 = 130,000 USDC
Profit: 30,000 USDC (30% profit = 3 * 10% = Leverage * price drop ETH to USDC)
```

### APRs – Funding Rate

As the user supplies / borrows assets to / from an underlying lending market **with leverage** the APRs that are normally displayed on the underlying lending market should be adjusted accordingly.&#x20;

For simplicity, we define **`Supply_APR`** as the sum of the annualised supply interest rate on the supplied asset and the APR that stems from other rewards (e.g. AAVE, COMP, AVAX). `Supply_APR` is always positive as the funds deposited accrue interest and other reward tokens are distributed by the underlying lending platform to incentivise liquidity.

Similarly, we define the **`Borrow_APR`** as the sum between the annualised borrow interest rate on the borrowed asset and the APR that stems from other rewards (e.g. AAVE, COMP, AVAX). The annualised borrow interest rate is always negative as it is meant to incentivise users to repay the loans they take. Therefore, the `Borrow_APR` is in most cases negative. However, perhaps surprisingly, in certain cases the underlying lending market is emitting enough reward tokens that it completely offsets the annualised borrow interest rate and the `Borrow_APR` becomes positive. Usually lending platforms take this approach during the bootstrapping period in order to incentivise users to take on loans and utilise the liquidity available, thereby allowing them to pay higher interest rates to suppliers.

The overall APR (essentially the annualised funding rate: `Funding_Rate`) can be obtained by applying the same leverage amplifications used to compute the supply and borrow amounts:

`Funding_Rate = Supply_APR * (L * 1) + Borrow_APR * L`&#x20;

Notice that even when the `Borrow_APR` is slightly negative the overall `Funding_Rate` can still be positive. Due to this effect and because FODL does not charge any other interest, the funding rates we can offer outcompete those offered by centralised trading platforms considerably.
