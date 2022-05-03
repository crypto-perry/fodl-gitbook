# Bots

One of the primary benefits of FODL is its smart contract bots. Three primary bots provide unique value for traders:

### **Anti-Liquidation Bots**&#x20;

* FODL positions are isolated accounts with supply and borrow balances. An account is allowed to borrow up to a certain “collateral factor” of the value of the supply balance. If the value of the borrowed asset exceeds the borrow limit (either due to appreciation of the borrowed asset or depreciation of the supplied asset), the underlying platform allows any user to liquidate this position, incentivizing them with a premium price (i.e. “liquidation incentive”).&#x20;
* Anti-Liquidation Bots allow FODL users to overwrite the underlying liquidation threshold imposed by the borrow limit by configuring a lower threshold and a lower “liquidation incentive”.

### **Stop Loss / Take Profit Bots**&#x20;

* FODL positions allow users to configure price thresholds to act as triggers for decentralized bots that close the position when the price crosses the configured threshold.&#x20;
* Users can set triggers above the current price to take profit or below to stop loss.&#x20;
* The price configured by the user is only the trigger price, while the actual execution price might be worse depending on the priority the decentralized bots gave your position. To incentivize the bots to prioritize a position, users can configure two settings:&#x20;
  * The percentual bot incentive is a user-configurable percentage of the trade size.&#x20;
  * The fixed bot incentive is a user-configurable amount of supply asset.&#x20;
* Users can combine the bot settings to best match their risk levels. Large positions that expect a significant price impact (e.g.,1%), often have a percentual bot incentive configure, while small positions can just provide a fixed incentive that just covers the transaction gas fees.

{% hint style="warning" %}
While FODL bots have proven reliable and fast, due to the nature of Ethereum relying on miners and network performance to execute transactions, no transaction can be 100% guaranteed to execute (even if using FODL bots).&#x20;
{% endhint %}
