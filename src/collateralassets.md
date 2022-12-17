# Collateral Assets

Assets are permissioned to be used as collateral by the governance and are priced using Chainlink oracles and Euler Finance isolated lending markets for select assets.

Every collateral asset to be whitelisted by the protocol has a few quantitative parameters which are analyzed for risk :

 - Market Cap / Fully Diluted Market Cap
 - Trading Volume
 - Liquidity
 - Cost needed to manipulate a 30 minute TWAP

Extensive analysis is to be performed by the core team before governance takes over regarding any asset whitelisting.

- [Euler Finance's paper on TWAP manipulation](https://github.com/euler-xyz/uni-v3-twap-manipulation/blob/master/cost-of-attack.pdf)