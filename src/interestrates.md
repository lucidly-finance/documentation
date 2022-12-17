# Interest Rates and Price Stability

Lucidly has a novel reactive interest rate mechanism that enforces peg stability by adjusting interest rates algorithmically.

When uLCD is below the peg(i.e, the demand for uLCD is less as a result of too much supply), the interest rate increases, hence prompting Vault owners to repay their loan back. This increases demand for uLCD in the open market and hence will bring price up to 1 USD.

When uLCD is above peg(i.e, there is more demand for uLCD than supply), the interest rates decrease, hence incentivizing users to borrow more uLCD against their margin. This increases supply and hence will bring price down to 1 USD.

Theoretically, interest cost should tend towards infinity if the price of uLCD tends towards zero and vice versa. Interest rates should reflect market supply and demand. An Asset should cost more to borrow if there's more demand for it than supply and less for the opposite.

The interest rate is to be controlled programmatically by a [PI controller](https://en.wikipedia.org/wiki/PID_controller#PI_controller) and the aim is to achieve the following goals in mind:

- _Optimal operation_ - The system must stay at an equilibrium state where the market price of 1 uLCD is 1 USD while holding the interest rate relatively constant.

- _Attractive interest rate for borrowers_ - We want the interest rate to quickly react when the price deviates from 1 USD.

Lucidly Finance uses a PI controller to determine rates. The interest rate for a loan at any point of time consists on a proportional and integral factor.

### Derivation for the interest rate

At any point of time, the ideal price of 1 uLCD should be 1 USD.

The peg deviation \\( \Delta P \\) at any point of time can be denoted by:

$$\Delta P = P_t - P_o$$

where \\(P_o\\) is 1 USD and \\(P_t\\) is the market price of 1 uLCD.
<!-- The protocol will set tolarable values of \\(P_t\\) between 0.98 USD and 1.02 USD. So we assume \\(P_c\\) = 0.98 and \\(P_l\\) = 1.02 -->

The controller is composed of the integral (\\(r_I\\)) and proportional (\\(r_P\\)) parts \\(r_L\\):

$$r = r_I + r_P$$

### Integral term

We need a controller that has adaptive behaviour. It should search for the interest rate that corresponds to the optimal price: when price is above peg, it should grow, otherwise it should go down. This is formulated below: 

$$r_i(t) = k_i\int_0^t\Delta P~d\tau$$

where \\(k_I\\) > 0 is a constant. The discrete form on the above equation is
$$r_I(t + \Delta t) = r_I(t) + k_I(\Delta P)\Delta t$$

### Proportional term

The proportional term \\(r_P\\) captures the following behaviour: when peg deviates below 1 USD, sharply increase the interest rate; when peg deviates below 1 USD, drop the interest rate. It is expressed by the formula

$$r_P(t) = k_P \Delta P$$

where \\(k_P\\) is a positive constant.

This approach is risky in a way that is \\(k_P\\) is not large enough, it may not succeed in pushing the peg back to 1 USD in case of price volatility. We need to assume a tolerable critical price on either side of the deviation beyond which \\(r_P\\) has more effect on the interest rate. 

Let's assume we can tolerate the price of 1 uLCD between $0.98 and $1.02, these two prices are our critical prices.

Therefore, we need to make \\(r_P\\) adaptive in the following way:


$$r_P(t) = k_c\Delta P$$
$$r_P(t) = k_c(1+T_c(t))\Delta P, if |\Delta P| > 0.02$$

Here \\(T_c\\) is a positive factor that grows while the peg stays above $1.02 or below $0.98 and decreses otherwise:

$$T_c(t+\Delta t) = \\{T_c(t) + \beta \Delta t\\}$$

<!-- $$r_P(t) = k_P\Delta P, if |\Delta P| < 0.02$$ -->

<!-- $$r_i(t + \Delta t) = max\\{r_i(t) + k_i(\Delta P)\Delta t, r_lin(t)\\}$$ -->

<!-- $$\int_\Omega \nabla u \cdot \nabla v~dx = \int_\Omega fv~dx$$ -->

- [Monetary Policy and PID Control](https://www.imfs-frankfurt.de/fileadmin/user_upload/Events_2018/MMCI_Conference/Papers/09-Raymond_Hawkins-Monetary_Policy_and_PID_Control.pdf)

- [Gauntlet's report on DeFi rates](https://gauntlet.network/reports/pid)