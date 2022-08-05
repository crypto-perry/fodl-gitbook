# FODL User Journey

The FODL platform combines several money "legos" of the DeFi ecosystem such as flash loans, lending platforms and decentralised exchanges to build a fully decentralised margin trading platform.

From the user's perspective, a typical FODL trade lifecycle would look like this:

1. The user selects a **Long** (supply) asset and a **Short** (borrow) asset.&#x20;
2. The user inputs an amount of Long asset to be used as **principal** investment.
3. The user chooses a **leverage** factor.
4. The FODL platform calculates how much of the Short asset needs to be borrowed to obtain the desired leverage. Furthermore, FODL displays the **Execution Price** at which the trade would actually happen on the exchange and the **Liquidation Price** at which the underlying lending platform would liquidate this position.
5. Once the user chooses a leverage factor that produces an acceptable trade-off between the potential gains and the losses that would be realised at the liquidation price, the position can be opened by clicking the **Open Position** button.
6. A Metamask popup will show up asking to **approve** the principal amount to be taken from the user and once the transaction is mined, a second popup will appear asking to **execute** the actual transaction that opens the position. For details of what the transaction does, refer to the trade flow described in[fodl-positions.md](fodl-positions.md "mention"). Once this transaction is mined as well, the page should refresh and the user can see his opened position.
7. The user can further configure a stop loss bot or take profit bot.
   * This action sends configuration data around cross-asset price action to FODL’s bot system.
8. If market conditions reach the user’s configured price, FODL bots will unwrap a portion or entirety of the user’s position per configuration.
   * Prices are determined by price oracles of the underlying platform (ie. Compound price oracles or Aave price oracles respectively for positions on each platform)
