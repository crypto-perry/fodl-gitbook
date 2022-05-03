# Opening short positions

By going short, a trader opens a position with the expectation that the underlying borrowed (Short) asset will drop in value against the supplied (Long) asset in the future.

For example, a 2.34x short USDC vs. ETH would yield a profit of 23.4% on a 10% price drop in the price of ETH to USDC.

## Opening a short position on FODL

1\. Select an asset to long, which you think will go up in value compared to the asset you choose to short

![](https://lh5.googleusercontent.com/Ryl4aoFY77PlCttCAMB-fq3RRXeX9H911v197a0o\_iDzn9P2CTP39ctxrvoMLYATquVf8utzbKMCaM7Xir5e22St8e4o1xZN8\_4bqsku6T-Sgbzq1Ui-K4kpq7A-fD7BogSbX762)

2\. Input the amount of assets you want to supply

![](https://lh6.googleusercontent.com/1QnRETM0\_cEFFHY3f9anlYZvMSOHjbRLRRl8qx\_R\_eJoauXWttYpBbpWThelP4nzDtIzjFIG-K5Mig8rd3pRY3R1E4ka98VJYl945A2dneYkPq\_eQJXrEMXBBBnd2RXymo1yTwlB)

3\. Select your desired leverage using the slider

![](https://lh4.googleusercontent.com/yXwPFBFs3D0SzCeEL08KNF9yZPFyqoo-4vhsnQqFfgiXvgEdzCf1sGnGbM96m3zzcJRQxO5okLQFoGhDme85Zfz7iuucH1ZM0A1r\_3TlAi-s\_17DwqeKWoVAqVaH5T2JqRsJaZnG)

{% hint style="warning" %}
The higher your leverage, the more profitable your position will be if you are right. However, with greater leverage comes greater risk, which means less room for the market to move opposite to what you hoped for when placing your bet before your position is closed & liquidated. Selecting lower leverage is safer!
{% endhint %}

4\. Review the position details and click ‘’Open Position’’

![](https://lh5.googleusercontent.com/hF3OFONVHaQjUC\_YqrilGDOEZkqM7XDNy0pCEG5NOYkkSbrKecFa46GkF40kFAvltRrnCFiBACQQq0-zcycx-z4W-lVafR6WB8rotXonD0MRhE-Faw6spFmCOZwqA1ZostrNIniy)

5\. Confirm the transaction in your Web3 wallet.&#x20;

{% hint style="warning" %}
Note: If you haven’t already, you will need to approve the spending of the selected asset in your Web3 wallet.
{% endhint %}

6\. Your position is now visible on ‘’Your Positions’’ on the FODL dashboard

![](https://lh5.googleusercontent.com/QlKZWlwzC8z0mBnFB2fkOgClnrQQkHVKdXKyZZjWxf8igFSoHFWi-q7fm-zWwdZileoXsNyDIRk244gthjEpO9jeA0PjVNXARmDRNXJiPAVAOKpmBxUW7-iIJm-D5UTCaThi3dfb)

## Example

### **Trade: Short ETH**&#x20;

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
