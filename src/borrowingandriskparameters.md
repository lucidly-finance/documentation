# Borrowing and Risk Parameters

Lucidly Finance offers dynamic interest rate loans aiming to be the most capital-efficient borrowing protocol. A user who needs liquid funds can use the protocol to lock up multiple assets listed on the protocol to borrow against the collateral and withdraw uLCD, which could be repaid at any future date.

Users can deposit multiple assets and borrow a certain amount of uLCD tokens. 
Each collateral has a certain LTV ratio (loan-to-value).

Each Vault has a single owner(can be an EOA or a contract) and a health factor that determines how much risk the owner assumes.

![Health Factor](./img/hf.png "health factor")

Any position that is under water and is eligible for liquidation if the health factor reached the liquidation threshold.

Cross collateral allows users to diversify their risk across multiple assets. At launch, the protocol is going to support the following assets as collateral:
- [WETH](https://etherscan.io/token/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2)
- [wstETH](https://etherscan.io/token/0x7f39c581f595b53c5cb19bd0b3f8da6c935e2ca0#code)
- [rETH](https://etherscan.io/token/0xae78736cd615f374d3085123a210448e74fc6393#code)
- [CRV](https://etherscan.io/token/0xD533a949740bb3306d119CC777fa900bA034cd52)
- [gOHM](https://etherscan.io/token/0x0ab87046fBb341D058F17CBC4c1133F25a20a52f)