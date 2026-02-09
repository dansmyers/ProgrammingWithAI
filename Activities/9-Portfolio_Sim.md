# Monte Carlo Portfolio Simulation

## Overview

## Setup

Open your Codespace. Start by making a new directory to hold files for this unit. Type the following command in the terminal:
```
mkdir 3-Simulation
```
Then `cd` into it:
```
cd 3-Simulation
```
You should see your terminal prompt update to indicate that you're now working in the `3-Simulation` folder.

Next, install the `yfinance` Python module that we'll use to fetch stock market data:
```
pip install yfinance
```

## Example: Plotting a stock price with `yfinance`

The `yfinance` library has the ability to pull data from Yahoo Finance for specified stock tickers over a given range of dates. The example below shows how to get the price of a specific stock over 
