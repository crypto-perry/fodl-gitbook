# Stop loss bot set-up

One of the primary benefits of Fodl are its smart contract bots, offering protection against liquidations by setting stop losses.

## Setting up the Fodl stop loss bot

1. Click on the settings icon on the right hand side of your open position on the Fodl dashboard

![](<../.gitbook/assets/Screenshot 2021-10-05 at 12.33.22.png>)

2\. Use the slider to set the stop loss price. In this case it's the price of WETH in USDT at which the bot should take the action

![](<../.gitbook/assets/Screenshot 2021-10-05 at 12.34.15.png>)

3\. Use the slider to set the unwind factor. This is the percentage by which your position will be decreased when the action is triggered

![](<../.gitbook/assets/Screenshot 2021-10-05 at 12.36.36.png>)

4\. Use the slider to set the bot incentive. This is the percentage of your position value that you want to give to the bot to incentivise

![](<../.gitbook/assets/Screenshot 2021-10-05 at 12.43.59.png>)

5\. If you're satisfied with these settings, click 'Save' and confirm the transaction in your Web3 wallet

{% hint style="warning" %}
Please note that the bot operates at collateral usage limit, not the fixed price
{% endhint %}
