# Opening long positions

By going long, a trader opens a position with the expectation that the underlying borrowed (short) asset will drop in value against the supplied (long) asset in the future.&#x20;

For example, a 2.34x long ETH vs. USDC would yield a profit of 23.4% on a 10% price drop in the price of USDC to ETH.

## Opening a long position on FODL

1. Select an asset to long. You should select an asset that you think will go up in value compared to the asset you choose to short.

![](https://lh3.googleusercontent.com/FdODq-W9Kh5SR7ho5bfZakVpU59z1a7p140QaVP3-V3MNUoaGnq8iICW1xviycdXC4zErVcHPUK1Rk7nxl7RNsqW-UuuZhmJ0tvqATEGLQeKnorvuDEzDwuHRCwvtGjCmKLfrH6\_)

2\. Input the amount of assets you want to supply

![](https://lh4.googleusercontent.com/64D7J4-wehb2GDlGd58XmP2E5XSkvnWdogNNPIm1SnRLPdzAKC4O0IuV5yNmr2X2OdqVTSXvqvfejbHGA8M--W6kAiUXmRxd8WY6RbDZwMpqQrlQ8g\_AOGPMnAzN\_fXOxJ-Ddcr1)

3\. Select your desired leverage using the slider

![](https://lh6.googleusercontent.com/xI1CYj7WfJnapbAJ1WBIxVHCNuIo7KSWW3nYu16bmyRVvZhDFnp6iM6nB-UV\_RDWTzWKcx3Gg0Rt7FVom\_hm8uKmdaBKgwNVWQ0qMcrJ00QWKR08egMDhjXXVj0OV2YYTFnpTyMJ)

{% hint style="warning" %}
The higher your leverage, the more profitable your position will be if you are right. However, with greater leverage comes greater risk, which means less room for the market to move opposite to what you hoped for when placing your bet before your position is closed & liquidated. Selecting lower leverage is safer!
{% endhint %}

4\. Review the position details and click ‘’Open Position’’

![](https://lh3.googleusercontent.com/a9XfkUSWxPwTSQUDJML7\_6RGjj9ykmohcMlcs0PVNSrbzpep8yit2RoWz2dhI-Bj6OJdEdLzgvkLY5giWwYwAC-p7H6YQ00zMsQN9GFLhtg4MJQ\_9eiJ6wuhg76mDqslBYGcLlAc)

5\. Confirm the transaction in your Web3 wallet.&#x20;

{% hint style="warning" %}
Note: If you haven’t already, you will need to approve the spending of the selected asset in your Web3 wallet.
{% endhint %}

6\. Your position is now visible on ‘’Your Positions’’ on the FODL dashboard

![](https://lh3.googleusercontent.com/NVzNxOEI9GH2cxZpxooitdHZ3496uicwoltG4M7J1fNSZbnXo1N4l9mLXW\_u\_FD0VH5EEIThwN0TWZYywwHKDsPYDSqqE4F2s6uVlBpyiP4sA\_9Ln6wqivdic1\_0wtXAHF8Mq3Nc)

## Example

### **Trade: Long ETH vs. USDC**

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
