## Asian & Lookback Options Pricing

This report explores the numerical pricing of two example path-depending option, Asian option and Lookback option. These option value are dependent on some movement in underlying asset price during the lifetime of the option. This report will focus on the pricing of these two path-dependent options using the Euler-Maruyama Scheme with a framework of risk-neutral density $\mathbb{Q}$. The Primary objective of this report is to come up with appropriate pricing of Asian and Lookback option, as well as determine the affect to option price under various scenarios considering factor changes in initial spot value $S_0$, strike price $E$, volatility $\sigma$, time to expiry ($T$ - $t$).

An Asian Option is exotic derivatives which derive their value from the average price of underlying asset over a specific time period, rather than the asset's price at the single point in time or at expiration date. The Asian Option provides the holder the right (but not the obligation) to buy or sell the underlying asset at the average price over the specific time period. Pricing the Asian Option can be challanging due to their dependence on averaging prices. This report will explore the unique characteristics of the Asian Option and analyze how their pricings are impacted by the averaging feature and further compare the result to a vanilla European Option.

Lookback Option, on the other hand are derivatives that allows the holder to buy or sell the underlying assets at its highest or lowest price over the life of the option contract. The payoff of this option depends on the maximum and minimum value of the underlying asset throughout the duration of the contract and therefore, will require a pricing method that allows to mark the movement of the underlying prices until the contract expiry date. In this report, we will dive into the complexities of lookback options, discussing their distinct payoffs and pricing mechanisms.

For these two Option above with dependence to movement of the underlying price, there does not exist any closed form analytical formula to calculate the theoretical option value, however we can use aproximation formula to value this kind of options. The numerical technique employed in this report is the "Euler-Maruyama Scheme" which is the stochastic differential equation (SDE) based method, that dicretizes the dynamics of the underlying asset's price. Using this scheme, we can simulate the movement of stock price to analyse the option payoff for both Asian and Lookback options, and subsequently use the Euler-Maruyama scheme to estimate the expected values of these payoffs under the risk-neutral measure $\mathbb{Q}$, ultimately deriving the option price. This report will provide outline of the "Euler-Maruyama" scheme's theoretical foundation and practical application in Option pricing.

Furthermore, this report highlights the application of Monte-Carlo simulation as numerical technique for the option pricing. Monte-Carlo simulation involves the generation of random scenarios for the unerlying asset's price and calculation of option payoff across these scenarios. Here, I will discuss how this method can offer better accuracy in option pricing, especially for complex derivatives. 

The goal of this report is to provide insights into the pricing of Asian and Lookback option, offering comprehensive understanding of their unique characteristics and pricing methodologies. The methodolgies explored, including Euler-Maruyama scheme and Monte-Carlo simulation, can be powerful tools for option pricing, risk management, and decision-making in financial markets.

### Key Concepts:
- Risk-neutral valuation:<br>
![Option Pricing Formula](https://latex.codecogs.com/svg.image?%5Cbg_white%20V%28S%2Ct%29%20%3D%20e%5E%7B-r%28T-t%29%7D%5Cmathbb%7BE%7D%5E%7B%5Cmathbb%7BQ%7D%7D%5B%5Ctext%7BPayoff%7D%28S_T%29%5D)
- Euler–Maruyama discretization for simulating geometric Brownian motion.
- Focus on *path-dependent payoffs*, where the option value depends on the trajectory of the asset, not just the terminal value.

### Implementation Details:
- Simulated stock paths using 10,000+ paths per scenario for statistical stability.
- Used parameters:
  - Initial stock price \( S_0 = 100 \)
  - Strike price \( K = 100 \)
  - Volatility \( \sigma = 20\% \)
  - Risk-free rate \( r = 5\% \)
  - Time to maturity = 1 year
- Developed reusable functions to handle both:
  - **Asian call/put options**: payoff based on the average of the underlying price over the path.
  - **Lookback call/put options**: payoff based on the maximum or minimum price observed during the life of the option.
- Extended the analysis by varying:
  - Strike prices
  - Volatility levels
  - Time to maturity
  - Number of timesteps (granularity of simulation)

### Results & Observations:
- **Asian options** showed significantly lower prices compared to vanilla options due to averaging effects reducing volatility.
- **Lookback options** were highly sensitive to path volatility, especially with higher timestep resolution.
- Compared the effect of discretization (daily vs. weekly sampling) on pricing accuracy and convergence.
- Discussed the impact of drift, diffusion, and sampling granularity on exotic option valuation.
- Identified convergence characteristics and variance reduction opportunities (not yet implemented, e.g., antithetic variates or control variates).

### Takeaways:
- The project reinforced understanding of stochastic calculus applied to financial modeling.
- Showcased the practical challenges of path-dependent options—where analytical solutions are intractable.
- Demonstrated strong Python capabilities in numerical finance, including simulation, vectorization, and statistical analysis.
