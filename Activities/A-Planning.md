# More Financial Simulations

## Overview

This activity will let you practice generating some more simulations covering common scenarios that show up in financial planning.

Start by changing to your `3-Simulation` directory:
```
cd 3-Simulation
```
You can then run `claude` and work through the questions below.

## Dollar-Cost Averaging

Suppose that you receive a windfall of $10,000 and want to invest it in an S&P 500 index fund, like we used in the last examples. There are two basic strategies:

- Invest the whole amount as one lump sum
- Invest a fixed amount each month for a number of months, until the full amount is invested. This strategy is called *dollar-cost averaging*.

The argument for dollar-cost averaging is that it smoothes out market fluctuations and makes the timing of when you enter less important. Consider: the lump sum strategy would do poorly if you invested right as the market hit a peak (when stocks are expensive), and then had to wait out a bear period where stocks are down. On the other hand, the market generally goes up over time, which would argue in favor of just going in immediately.

Prompt Claude to create a simulation comparing lump sum investing vs. dollar-cost averaging strategies. Assume you have $10,000 that you want to put into an S&P 500 index fund. Compare investing as a lump sum vs. a few different dollar-cost strategies, say, $2500 per month for four months and $1000 per month for 10 months. Use two years (24 months) as the total length of the simulation period.

Produce a chart with box plots comparing the simulated outcomes achieved by the different strategies. Which one seems to perform best? After you have your results, chat with Claude about them. What are the considerations involved in choosing between lump sum and dollar-cost approaches in the real world?

## Withdrawal rates

Once they retire, most Americans are living off of a combination of Social Security benefits and income earned by drawing down their investment portfolio. Retirees would like to take as much income from the investment portfolio each year as possible, but not at the risk of depleting it too aggressively.

A standard piece of financial advice is the *4% rule*: That a withdrawal rate of 4% per year is a safe amount to take out of a portfolio. Historically, this withdrawal rate is balanced by growth in the markets, so the portfolio has a high probability of lasting for the retiree's life.

Consider a retiree with investments of $1 million, again in an S&P 500 index fund. She wants to plan on 30 years of withdrawals.

Simulate the impact of withdrawing at rates of 2% ($20k per year) up to 7% ($70k per year) for 30 years. For each rate, simulate the probability that the portfolio goes to zero before the end of the time horizon. Also produce a plot showing the distribution of portfolio values for each withdrawal rate.

Note: We're using the S&P 500 index fund to keep the simulation simple. In reality, retirees generally shift to a balanced portfolio that includes a high percentage of investments like Treasury bonds that have lower but safer returns.

## Inflation adjustment

Modify the previous problem to include a 3% annual inflation rate.

Assume that our investor wants to withdraw a fixed annual amount ranging from $20k up to $70k. Adding inflation requires that she withdraw a higher percentage of the portfolio each year to hit the target income level.

How does this change the results?

## Believe it or not, calls

For the truly sophisticated investor - or degenerate gambler - the real money is made by trading **options**.

The simplest vanilla option is the *call*, which is essentially a bet that the price of an asset will rise in the future. A call is a contract that gives its owner the *right* (but not the obligation) to buy a share of a stock at a pre-set price at some future date. Here's an example:

- Google's stock (GOOG) is currently trading for about $320 per share

- I buy a call option for $320 with a 30-day expiration date. The broker offering the contract charges me a fixed fee for this purchase

- Suppose, at the end of 30 days, the price of GOOG has gone up to $350. I exercise my option contract to buy a share at the strike price of $320, then sell it at the current price of $350, making $30, less the price of purchasing the option contract.

- Suppose that GOOG drops below $320 at the end of the 30-day window. In this case, there's no point in exercising the contract, so I let it expire. My loss is the up-front cost of puchasing the contract.

Options like calls are known as *financial derivatives*: their value depends on the change of value in *some other asset*. You can buy options on pretty much anything and there are a vast number of variations on the basic call contract.

Here's a key question: what is the fair price to pay for an option contract like the one in my example? This is tricky, because it depends on the **future price** of GOOG. If it's likely that GOOG is going up aggressively, the contract is more likely to pay out and should therefore demand a higher up-front fee. If GOOG is flat or declining, then the call option isn't worth very much.

Quantitative traders address these questions through complex financial models. The most famous model for options is the Black-Scholes model, which models returns theoretically and uses stochastic calculus to derive the estimated present value of an option contract. 

Try creating a simulation to estimate the value of an option contract using the parameters above: GOOG with a 30-day window and a strike price of $320. Use `yfinance` to pull daily percentage changes in the stock and simulate its estimated forward pricing. Then repeat for a few different stocks or assets of interest.

- Start with the current price. Each trajectory then simulates 30 days of movements

- The value of the option at the end of 30 days is `max(final_price - strike_price, 0)`

- Assume that we're considering only the final price at the end of the 30 day window. This is known as a *European call option*. A variation is the *American option*, which allows exercise at any point in time within the range. American options have more flexibility, so they're worth more.
