# Vaults

The Lucidly Protocol uses chainlink oracles and Euler's isolated lending markets to allow users to adjust their risk tolerance according to the collateral they decide to use.

Users can deposit multiple collateral into their vaults and borrow a maximum amount of uLCD tokens calculated from their health factor. 

Cross-margin enables users to hedge risks according to total notional value in the margin account.

A Vault is where the borrower takes out and maintains the $uLCD loan against multiple assets on the protocol. Every vault is linked to an individual ERC20 address and each address can have just one vault. 

Lucidly Vaults are conceptually similar to the vaults or CDPs managed by other protocols. Each vault maintains two balances: One balance is the user debt denominated in ETH and the other balance is the net value of the users collateral equivalent to the total margin of all the assets (ETH, wStETH, APE, LINK, AVAX, etc.) supplied by the user, also denominated in ETH. 

The vault’s collateral ratio is dependent on the above two balances of the vault. The amount of each balance could be altered by adding more collateral or by repaying the user debt. The vault could be closed anytime by paying off the complete debt + interest.