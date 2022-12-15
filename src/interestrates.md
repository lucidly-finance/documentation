# Interest Rates and Price Stability

Lucidly has a novel reactive interest rate mechanism that enforces peg stability by adjusting interest rates algorithmically.

When uLCD is below the peg(i.e, the demand for uLCD is less as a result of too much supply), the interest rate increases, hence prompting Vault owners to repay their loan back. This increases demand for uLCD in the open market and hence will bring price up to 1$.

When uLCD is above peg(i.e, there is more demand for uLCD than supply), the interest rates decrease, hence incentivizing users to borrow more uLCD against their margin. This increases supply and hence will bring price down to 1$.

Theoretically, interest cost should tend towards infinity if the price of uLCD tends towards zero and vice versa. Interest rates should reflect market supply and demand. An Asset should cost more to borrow if there's more demand for it than supply and less for the opposite.

Lucidly Finance uses a PI controller to determine rates.

Ri = k() 

- [Monetary Policy and PID Control](https://www.imfs-frankfurt.de/fileadmin/user_upload/Events_2018/MMCI_Conference/Papers/09-Raymond_Hawkins-Monetary_Policy_and_PID_Control.pdf)