# Opening long positions

Long positions are defined as Fodls where the supplied asset is a non-stablecoin and the borrowed asset is a stablecoin. The positions are for users who are bullish on market conditions and seek to profit from price appreciation of assets against fiat stablecoins.&#x20;

## Opening a long position on Fodl

1. Select an asset to Supply you think will go up against the asset you choose to Borrow&#x20;

OR&#x20;

Select an asset to Borrow you think will go down against the asset you choose to Supply

![](<../.gitbook/assets/Screenshot 2021-10-04 at 15.19.38.png>)

3\. Select your desired leverage. You can use the slider or the buttons

![](<../.gitbook/assets/Screenshot 2021-10-04 at 15.24.00.png>)

{% hint style="warning" %}
The higher your leverage, the more profitable your position will be if you are right. However, the higher your leverage the higher your starting health limit (you'll start closer to possible liquidation), so the less room you have for the market to move opposite your bet before your position is closed. Selecting lower leverage is safer!&#x20;
{% endhint %}

4\. Input the amount of assets you want to supply, and click 'Enter Position'

![](<../.gitbook/assets/Screenshot 2021-10-04 at 15.28.55.png>)

5\. Approve the spending of the selected asset in your Web3 wallet if you haven't already. Confirm the transaction in your Web3 wallet.

6\. Your position is now visible on your Fodl dashboard

![](<../.gitbook/assets/Screenshot 2021-10-05 at 12.26.43.png>)

## Examples

* Supply ETH, borrow DAI. Supply COMP, borrow USDC. Supply ETH, borrow USDC.

Example in action: ETH @ $2k, supply 100 ETH to borrow USDC w/ 3x Leverage

* Your net starting position would be:&#x20;
  * Supply: 300 ETH ($600k)
  * Borrow: 400,000 USDC
  * Health: 66%

Example in action: ETH moves to $3k

* Your new current position would be:&#x20;
  * Supply: 300 ETH ($900k)
  * Borrow: 400,000 USDC
  * Health: \~40%

Example in action: Close position with ETH at $3k\*\*

* Sell 133.33 ETH for 400,000 USDC&#x20;
* Repay 400,000 USDC
* User Receives 174.724 ETH&#x20;
  * (100 ETH principal + 76.64 ETH Profit - 1.916 ETH profit share fee)
    * Profit share fee = 2.5% of Profit only -- fees never taken on principal

{% hint style="info" %}
Interest & governance token APR not calculated in these examples – true profits may be higher or lower
{% endhint %}
