# FODL trade lifecycle

The FODL platform combines several money "legos" of the DeFi ecosystem - flash loans and collateral lending platforms, combined with proprietary position protection bots and cross-asset price indexing - to build a fully decentralized margin trading platform.

The following describes a typical FODL trade lifecycle:

1. A user selects a supply asset and supply amount, a borrow asset and leverage.
2. The FODL platform calculates how much of the borrow asset is required to match the leverage.
3. When a user opens the position, FODL takes out a flash loan capable of opening the full leverage position in a single transaction.
   * This effectively allows the user to leverage their principal beyond the limits of the underlying platform
4. A user configures a stop loss bot or take profit bot.
   * This action sends configuration data around cross-asset price action to FODL’s bot system.
5. If market conditions reach the user’s configured price, FODL  bots will unwrap a portion or entirety of the user’s position per configuration.&#x20;
   * Prices are determined by price oracles of the underlying platform (ie. Compound price oracles or Aave price oracles respectively for positions on each platform)&#x20;

