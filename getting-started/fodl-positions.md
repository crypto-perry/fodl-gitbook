# FODL Positions

On FODL, each position (trade) opened is implemented as a smart contract (smart wallet) owned by the user with the following high-level features:&#x20;

* Supplying/borrowing assets with lending platforms (eg. Aave, Compound, etc.)&#x20;
* Exchange of assets using the decentralized exchanges available on-chain (eg. Uniswap, Curve, Quickswap, etc.)&#x20;
* Operation using flash loans (eg. DyDx, Aave, UniswapV3, etc.).
* Configuration of stop-loss / take-profit price triggers to be executed by a decentralised network of bots.

FODL uses these features as building blocks to construct financial instruments such as Long / Short positions: borrowing the Short asset, exchanging it for the Long asset, and supplying it together with some initial principal investment that acts as a margin.

> Note: Any trade is both a Long and a Short. For example, a Long ETH vs BTC trade is equivalent to a Short BTC vs ETH trade. However, when one of the assets is a stable coin, the common practice is to only refer to the trade as the direction of the non-stable coin asset. For instance, a Short ETH vs. USDC trade (aka Long USDC vs ETH) is just called “Short ETH” as the Long (supply) asset is a stable coin.

To simplify the trade execution, FODL requires users to provide a principal investment in the supply (Long) asset. A Long / Short position is represented on the underlying lending platform as follows:&#x20;

1. Supplied asset: `Supply_Amount = (Leverage + 1) \* Principal`
2. Borrowed asset: `Borrow_Amount = Leverage * Principal / Price_Borrow_to_Supply`

When opening / increasing the value or leverage of a position, some amount of the borrowed asset is exchanged into the supply asset. On the other hand, when closing / decreasing the value or leverage of a position, the supplied asset is exchanged into the borrowed asset. Therefore, if the borrowed asset depreciated between opening and closing a position, the price movement will be amplified with the leverage taken on entry.

Notice the value and PnL of a position can be expressed mathematically: 
```
Position_Value = Supply_Amount - Borrow_Amount * Current_Price_Borrow_to_Supply
PnL = Position_Value - Principal 
PnL = Supply_Amount - Borrow_Amount * Current_Price_Borrow_to_Supply - Principal
PnL = (Leverage + 1) * Principal - (Leverage * Principal / Entry_Price_Borrow_to_Supply) * Current_Price_Borrow_to_Supply - Principal = Leverage * Principal * (1 - Current_Price_Borrow_to_Supply / Entry_Price_Borrow_to_Supply) = Leverage * Principal * Price_Drop_Borrow_to_Supply
```

Notice how the profit is directly proportional (with a factor of `Leverage`) to the price drop of the borrowed (Short) asset. See detailed examples below!

### Long Position

By going _long_, a trader opens a position with the expectation that the underlying borrowed (Short) asset will drop in value against the supplied (Long) asset in the future.

#### **Example: Long ETH**&#x20;

{% hint style="info" %}
**Asset Pair:** supply ETH & borrow USDC&#x20;

**Price:** 1 ETH = 1000 USDC or 1 USDC = 0.001 ETH

**Principal:** 100 ETH&#x20;

**Leverage:** 3x&#x20;
{% endhint %}

Your net starting position would be:&#x20;

* Supply = (Leverage + 1) \* Principal = 4 \* 100 = 400 ETH&#x20;
* Borrow = Leverage \* Principal / price\_USDC\_ETH = 3 \* 100 / 0.001 = 300,000 USDC&#x20;
* Position Value = Supply - Borrow \* price\_USDC\_ETH = 400 - 300,000 \* 0.001 = **100 ETH**&#x20;

{% hint style="warning" %}
**ETH prices moves to $1200**&#x20;

**New Price:** 1 ETH = 1200 USDC or 1 USDC = 0.00083 ETH

**Price Move:** +20% ETH or -16.66% USDC
{% endhint %}

Your position would now be:&#x20;

* Supply: 400 ETH&#x20;
* Borrow: 300,000 USDC&#x20;
* Position Value: 400 - 300,000 \* 0.00083 = 150 ETH&#x20;
* Profit: **50 ETH** (50% profit = Leverage \* _price move)_

### Short Position

By going short, a trader opens a position with the expectation that the underlying borrowed (Short) asset will drop in value against the supplied (Long) asset in the future.

#### **Example: Short ETH**&#x20;

{% hint style="info" %}
**Asset Pair:** supply USDC & borrow ETH

**Price:** 1 USDC = 0.001 ETH or 1 ETH = 1000 USDC&#x20;

**Principal:** 100,000 USDC&#x20;

**Leverage:** 3x&#x20;
{% endhint %}

Your net starting position would be:&#x20;

* Supply = (Leverage + 1) \* Principal = 4 x 100,000 = 400,000 USDC&#x20;
* Borrow = Leverage \* Principal / price\_ETH\_USDC = 3 \* 100,000 / 1000 = 300 ETH&#x20;
* Position Value = Supply - Borrow \* price\_ETH\_USDC = 400,000 - 300 \* 1000 = 100,000 USDC&#x20;

{% hint style="warning" %}
**ETH prices moves to $900**&#x20;

**New Price:** 1 USDC = 0.001111 ETH or 1 ETH = 900 USDC

**Price Move:**  11.11111% ETH or -10% USDC
{% endhint %}

Your position would now be:&#x20;

* Supply: 400,000 USDC&#x20;
* Borrow: 300 ETH&#x20;
* Position Value: 400,000 - 300 \* 900 = 130,000 USDC&#x20;
* Profit: **30,000 USDC** (30% profit = Leverage \* _price move)_

### Correlated Position

Correlated positions can be defined as FODLs where the supply and borrow asset prices are exactly the same. Correlated positions are a strategy focused on maximizing governance token farming of COMP or AAVE, or other governance tokens with reduced risk of loss due to underlying asset price movements. Specifically, around two USD peg tokens these strategies can be considered risk-averse.

#### Example: Farm DAI vs. USDC&#x20;

The aim of such correlated positions with virtually no price volatility risk is to simply farm the governance rewards provided by the underlying lending platform.

{% hint style="info" %}
**Asset Pair:** supply DAI & borrow USDC (1 DAI = 1 USDC or 1 USDC = 1 DAI)&#x20;

**Principal:** 100 DAI&#x20;

**Leverage:** 3x&#x20;
{% endhint %}

Your net starting position would be:&#x20;

* Supply = (Leverage + 1) \* Principal = 4 \* 100 = 400 DAI&#x20;
* Borrow = Leverage \* Principal / price\_USDC\_DAI = 3 \* 100 \* 1 = 300 USDC&#x20;
* Position Value = Supply - Borrow \* price\_USDC\_DAI = 400 - 300 \* 1 = **100 DAI**
