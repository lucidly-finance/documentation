# Introduction

Stablecoins have always been an area of very intensive research and interest in decentralised finance. Most stablecoins in the ecosystem can be categorised into custodian, soft-pegged over-collateralized and under-collateralized algorithmic designs.

Custodian stablecoins are centralised institutions that allow deposits in fiat and other RWAs and issue tokens on the blockchain that are hard-pegged to the exact value of the currency. Hence a very centralised approach.
Soft-pegged over-collateralized stablecoins have different designs, the most popular amongst them are CDPs(Collateralized Debt Positions).

Depositors deposit an asset to issue a stable position at a premium. These positions get liquidated when the value of the collateral gets lower than the loan issued and depositors need to add more margin to prevent the same. This is a permissionless and decentralised approach and the requirement of a premium to issue stablecoin makes it hard to scale.

Under-collateralized algorithmic stablecoins are backed by endogenous assets and provide a highly trustless and scalable model that captures the early Bitcoin vision of decentralized money but with useful stability. They're extremely difficult to bootstrap and highly risky, as seen in the LUNA-UST crash.

We've come up with a novel mechanism of cross/isolated Vaults which allow depositors to hedge risks with multiple assets and allows integration of risk management strategies on top of the protocol without much gas overhead. Lucidly relies on a protocol managed stability pool as the primary mechanism to liquidate risky Vaults.

### uLCD

Lucidly Finance is an overcollateralised stablecoin lending protocol designed to offer efficient borrow rates and a robust dynamic interest rate to maintain peg. The first product is uLCD which is soft-pegged to USD.

The protocol uses governance to vote on gauges to use the collateral to earn yield on other defi money markets like yearn vaults, morpho aave, gearbox etc.

- [Good ol' Vitalik's post on stablecoins](https://vitalik.ca/general/2022/05/25/stable.html)