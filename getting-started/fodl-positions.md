# FODL Positions

On FODL, each position (trade) opened is implemented as a smart contract (smart wallet) owned by the user with the following high-level features:

* Supplying/borrowing assets with lending platforms (eg. Aave, Compound, etc.)
* Exchange of assets using the decentralized exchanges available on-chain (eg. Uniswap, Curve, Quickswap, etc.)
* Operation using flash loans (eg. DyDx, Aave, UniswapV3, etc.).
* Configuration of stop-loss / take-profit price triggers to be executed by a decentralised network of bots.

FODL uses these features as building blocks to construct financial instruments such as Long / Short positions: borrowing the Short asset, exchanging it for the Long asset, and supplying it together with some initial principal investment that acts as a margin.

> Note: Any trade is both a Long and a Short. For example, a Long ETH vs BTC trade is equivalent to a Short BTC vs ETH trade. However, when one of the assets is a stable coin, the common practice is to only refer to the trade as the direction of the non-stable coin asset. For instance, a Short ETH vs. USDC trade (aka Long USDC vs ETH) is just called “Short ETH” as the Long (supply) asset is a stable coin.

When opening / increasing the value of a position, some amount of the borrowed asset is exchanged into the supply asset. On the other hand, when closing / decreasing the value of a position, the supplied asset is exchanged into the borrowed asset.

Using the following notations:

```
S_Amount = Amount of Supply asset on the underlying lending market
B_Amount = Amount of Borrow asset on the underlying lending market
L = Leverage multiplier
P = Principal provided by the user in Supply token
Entry_Price_B_to_S = Price of Borrow to Supply at position entry
Current_price_B_to_S = Price of Borrow to Supply at current time
Price_Change_B_to_S = Relative price change between entry and current price
Position_Value = Current value of the position expressed in Supply asset
We can mathematically represent the state of a Long / Short position on the underlying lending platform as follows:
```

1. Supplied asset: `S_Amount = (L + 1) * P`
2. Borrowed asset: `B_Amount = L * P / Entry_Price_B_to_S`

As the relative price of the assets changes, we can express the current `Position_Value` and `PnL` as:

```
Position_Value = S_Amount - B_Amount * Current_Price_B_to_S
PnL = Position_Value - P
PnL = S_Amount - B_Amount * Current_Price_B_to_S - P
PnL = (L + 1) * P - (L * P / Entry_Price_B_to_S) * Current_Price_B_to_S - P 
PnL = L * P * (1 - Current_Price_B_to_S / Entry_Price_B_to_S) 
PnL = L * P * Price_Change_B_to_S
```

Notice how the profit or loss is directly proportional (with a factor of leverage) to the price change of the borrowed (Short) asset. See detailed examples below!

### APRs – Funding Rate

As the user supplies / borrows assets to / from an underlying lending market **with leverage** the APRs that are normally displayed on the underlying lending market should be adjusted accordingly.&#x20;

For simplicity, we define **`Supply_APR`** as the sum of the annualised supply interest rate on the supplied asset and the APR that stems from other rewards (e.g. AAVE, COMP, AVAX). `Supply_APR` is always positive as the funds deposited accrue interest and other rewards tokens are distributed by the underlying lending platform to incentivise liquidity.

Similarly, we define the **`Borrow_APR`** as the sum between the annualised borrow interest rate on the borrowed asset and the APR that stems from other rewards (e.g. AAVE, COMP, AVAX). The annualised borrow interest rate is always negative as it is meant to incentivise users to repay the loans they take. Therefore, the `Borrow_APR` is in most cases negative. However, perhaps surprisingly, in certain scenarios when the underlying lending market is emitting rewards in order to diminish or completely offset this interest in order to incentivise users to take on loans and utilise the liquidity available.&#x20;

The overall interest rate (essentially the `Funding_Rate`) can be obtained by applying the same leverage amplifications that amplify the principal value on the supply and borrow sides:

`Funding_Rate = Supply_APR * (L * 1) + Borrow_APR * L`&#x20;

On platforms that incentivise

### Long Position

By going _long_, a trader opens a position with the expectation that the underlying borrowed (Short) asset will drop in value against the supplied (Long) asset in the future.

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
Position Value = Supply - Borrow * price_USDC_ETH = 400 - 300,000 * 0.001 = 100 ETH
```

{% hint style="success" %}
**Price change:** ETH price appreciates to 1200 USDC

**New Price:** `1 ETH = 1200 USDC or 1 USDC = 0.00083 ETH`

**Price Move:** `+20% ETH or -16.66% USDC`
{% endhint %}

The supply and borrow amounts do not change at all (ignoring the interest rates). Your position would now be:

```
Supply: 400 ETH
Borrow: 300,000 USDC
Position Value: 400 - 300,000 * 0.00083 = 150 ETH
Profit: 50 ETH (50% profit = Leverage * price move)
```

### Short Position

By going short, a trader opens a position with the expectation that the underlying borrowed (Short) asset will drop in value against the supplied (Long) asset in the future.

#### **Example: Short ETH**

{% hint style="info" %}
**Asset Pair:** supply USDC & borrow ETH

**Price:** 1 USDC = 0.001 ETH or 1 ETH = 1000 USDC

**Principal:** 100,000 USDC

**Leverage:** 3x
{% endhint %}

Your net starting position would be:

* Supply = (Leverage + 1) \* Principal = 4 x 100,000 = 400,000 USDC
* Borrow = Leverage \* Principal / price\_ETH\_USDC = 3 \* 100,000 / 1000 = 300 ETH
* Position Value = Supply - Borrow \* price\_ETH\_USDC = 400,000 - 300 \* 1000 = 100,000 USDC

{% hint style="warning" %}
**ETH prices moves to $900**

**New Price:** 1 USDC = 0.001111 ETH or 1 ETH = 900 USDC

**Price Move:** 11.11111% ETH or -10% USDC
{% endhint %}

Your position would now be:

* Supply: 400,000 USDC
* Borrow: 300 ETH
* Position Value: 400,000 - 300 \* 900 = 130,000 USDC
* Profit: **30,000 USDC** (30% profit = Leverage \* _price move)_

### Correlated Position

Correlated positions can be defined as FODLs where the supply and borrow asset prices are exactly the same. Correlated positions are a strategy focused on maximizing governance token farming of COMP or AAVE, or other governance tokens with reduced risk of loss due to underlying asset price movements. Specifically, around two USD peg tokens these strategies can be considered risk-averse.

#### Example: Farm DAI vs. USDC

The aim of such correlated positions with virtually no price volatility risk is to simply farm the governance rewards provided by the underlying lending platform.

{% hint style="info" %}
**Asset Pair:** supply DAI & borrow USDC (1 DAI = 1 USDC or 1 USDC = 1 DAI)

**Principal:** 100 DAI

**Leverage:** 3x
{% endhint %}

Your net starting position would be:

* Supply = (Leverage + 1) \* Principal = 4 \* 100 = 400 DAI
* Borrow = Leverage \* Principal / price\_USDC\_DAI = 3 \* 100 \* 1 = 300 USDC
* Position Value = Supply - Borrow \* price\_USDC\_DAI = 400 - 300 \* 1 = **100 DAI**
