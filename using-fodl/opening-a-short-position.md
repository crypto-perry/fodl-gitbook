# Opening short positions

Short positions are defined as Fodls where the supplied asset is a stablecoin and the borrowed asset is a non-stablecoin. The positions are for users who are bearish on market conditions and seek to profit from price depreciation of assets against fiat stablecoins.&#x20;

## Opening a short position on Fodl

1. Select an asset to Supply you think will go up against the asset you choose to Borrow&#x20;

OR

Select an asset to Borrow you think will go down against the asset you choose to Supply

![](<../.gitbook/assets/Screenshot 2021-10-04 at 15.47.09.png>)

3\. Select your desired leverage. You can use the slider or the buttons

![](<../.gitbook/assets/Screenshot 2021-10-04 at 15.40.34.png>)

{% hint style="warning" %}
The higher your leverage the more profitable your position will be if you are right. However, the higher your leverage the higher your starting health limit (closer to liquidation/close out position), so the less room you have for the market to move opposite your bet before your position is closed. Selecting lower leverage is safer!
{% endhint %}

4\. Input the amount of assets you want to supply, and click 'Enter Position'&#x20;

![](<../.gitbook/assets/Screenshot 2021-10-04 at 15.48.11.png>)

5\. Approve the spending of the selected asset in your Web3 wallet if you haven't already. Confirm the transaction in your Web3 wallet

6\. Your position is now visible on your Fodl dashboard

![](<../.gitbook/assets/Screenshot 2021-10-04 at 15.51.14.png>)

## Examples

* Supply DAI, borrow ETH. Supply USDC, borrow COMP. Supply USDC, borrow ETH.

Example in action: Supply 500,000 USDC to borrow ETH @ $2k w/ 3x Leverage

* Your net starting position would be:&#x20;
  * Supply: 1,500,000 USDC
  * Borrow: 500 ETH ($1,000,000)
  * Health: 66%

Example in action: ETH moves to $1k

* Your new current position would be:&#x20;
  * Supply: 1,500,000 USDC&#x20;
  * Borrow: 500 ETH ($500k)
  * Health: \~33%

Example in action: Close position with ETH at $1k\*\*

* Sell 500,000 USDC for 500 ETH&#x20;
* Repay 500 ETH
* User Receives 987,500 USDC&#x20;
  * (500,000 USDC principal + 500,000 USDC Profit - 12,500 USDC Profit share fee)
    * Profit share fee = 2.5% of Profit only -- fees never taken on principal

{% hint style="info" %}
Interest & governance token APR not calculated in these examples – true profits may be higher or lower&#x20;
{% endhint %}

