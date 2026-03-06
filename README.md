# Monte Carlo Pricing of VIX Options under an Ornstein–Uhlenbeck Model

This project implements a Monte Carlo framework for pricing European-style VIX options under an Ornstein–Uhlenbeck (OU) process. The workflow includes market data preparation, simulation input construction, Monte Carlo pricing across strikes, implied volatility extraction, calibration of OU parameters from historical VIX data, pricing diagnostics relative to market mid prices, and estimation of option Greeks via finite differences.

## Project Objective

The goal of this project is to study how a mean-reverting stochastic process can be used to model volatility dynamics and price VIX options in a structured quantitative workflow. Rather than treating the VIX as a standard equity-like underlying, the project explores a framework better aligned with its mean-reverting behavior and evaluates the resulting model prices against observed market quotes.

## Methodology

The notebook follows the pipeline below:

1. **Load market data**
   - Historical VIX index data
   - SPX reference data
   - 3-month Treasury bill rate for discounting

2. **Construct simulation inputs**
   - Valuation date
   - Expiry date
   - Spot VIX
   - Risk-free rate
   - Initial OU parameters
   - Strike grid and market mid prices

3. **Process options chain**
   - Load cleaned VIX option data
   - Compute bid-ask mid prices
   - Filter for the target expiration
   - Sort strikes and align inputs for pricing

4. **Monte Carlo pricing**
   - Simulate VIX paths under OU dynamics
   - Estimate call and put prices across strikes
   - Visualize option price curves

5. **Implied volatility extraction**
   - Use Black–Scholes inversion to recover implied volatilities from Monte Carlo prices
   - Plot the implied volatility smile

6. **Model extension**
   - Explore a stochastic-volatility extension for VIX dynamics

7. **OU parameter calibration**
   - Estimate OU parameters from historical log-VIX data using maximum likelihood

8. **Diagnostics and Greeks**
   - Compare model prices against observed market mid prices
   - Estimate Delta, Gamma, Vega, Theta, and Rho via finite-difference methods

## Model Overview

The core framework models VIX dynamics with an Ornstein–Uhlenbeck process to capture mean reversion. Monte Carlo simulation is then used to generate terminal values and estimate discounted option payoffs.

In calibration sections, the project works with transformed VIX data to improve numerical stability and estimate model parameters from historical observations.

## Repository Structure

```text
.
├── data/
│   ├── raw/
│   └── processed/
├── notebooks/
│   └── vix_option_pricing_ou_mc.ipynb
├── results/
│   └── figures/
├── src/
├── requirements.txt
├── README.md
├── LICENSE
└── .gitignore
