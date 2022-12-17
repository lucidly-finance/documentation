# Liquidations and Stability Pool

Lucidly’s liquidation model provides relevant benefits from a user’s perspective with its design exploring relevant solutions.

One of the main issues for borrowing services is the fact that the protocol must always remains solvent: there are therefore, if necessary, liquidations to restore the balance. Liquidation of positions requires a certain infrastructure when it is the liquidators who do it directly, as on Maker, Compound or Aave. To optimize the process, the idea of having a liquidity “backstop” has emerged.

It is about having a reserve of funds, generally stablecoins that the protocol uses if necessary to manage liquidations: at Lucidly Finance, we call it the Stability Pool inspired from Liquity. The users who wish to do so can deposit their uLCD in this pool: they are remunerated in the asset that the protocol liquidates. Lucidly Finance will deploy a stability pool for each collateral that it supports.

The funds in the stability pool are used when necessary for liquidations. With quantified figures, the protocol runs the stability pool in a fully secure manner. Liquidations tend to happen mostly in case of a sharp drop in the total margin price of the assets stored in the vault. A position in the Stability Pool therefore allows one to profit from these juicy liquidations without having the skills or infrastructure to execute them.

The stability pool thus offers a rather gas-efficient and attractive native return option on uLCD. With a conservative collateral ratio, it may even be suitable for an almost entirely passive position. Rewards from the stability pool is distributed to depositors in a O(1) complexity.

The stability pool acts as the first shock absorber for liquidations in the protocol. However, if certain cases, if the debt amount cannot be covered by stability pool reserves, the protocol will put up the collateral up for a dutch auction.

The collateral in that case is sold off to the highest bidder and protocol takes a certain amount of the collateral in this case as a liquidation fee. This amount is dynamic, rather than a fixed discount percentage for the liquidator, we allow the discount to rise as a function of how under-water a position is. As the discount slowly increases, each would-be liquidator must decide whether or not to bid for a liquidation at the current discount on offer. Liquidator A might be profitable at 4%, but liquidator B might run a more efficient operation and be able to jump in sooner at 3.5%. The Dutch auction is aided by Uniswap TWAP oracles because a shock to the price does not bring with it a singular point at which every liquidator becomes profitable all at once. Instead, the price moves more smoothly over time leading to a continuum of opportunities to liquidate, which further helps to limit PGAs. Overall, this process should help to drive the discount price towards the marginal operating cost of liquidating a borrower.

- [Scalable Reward Distribution with Compounding Stakes](https://github.com/liquity/liquity/blob/master/papers/Scalable_Reward_Distribution_with_Compounding_Stakes.pdf)
- [Maker liquidations 2.0](https://arxiv.org/pdf/2201.03519.pdf)