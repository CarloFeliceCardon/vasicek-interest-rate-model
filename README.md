# Vasicek Interest Rate Model

Simulation and calibration of the Vasicek (1977) short-rate model in Python.

## What this project does

- Simulates interest rate trajectories using Euler-Maruyama discretization
- Compares the simulated terminal distribution against the analytical solution
- Prices zero-coupon bonds and derives the implied yield curve
- Estimates model parameters (κ, θ, σ) from real US Treasury Bill data (FRED)
- Calibrates the yield curve on current market rates

## Model

The Vasicek model describes the evolution of the short rate as:

$$dr_t = \kappa(\theta - r_t)dt + \sigma dW_t$$

Where:
- κ: speed of mean reversion
- θ: long-run mean rate
- σ: volatility
- W_t: standard Brownian motion

Zero-coupon bond prices have a closed-form solution: P(t,T) = A(t,T) · exp(−B(t,T) · r_t)

## Data

Parameters are estimated via OLS regression on monthly 3-Month Treasury Bill rates
sourced from FRED (Federal Reserve Bank of St. Louis), from 2000 to present.

## Limitations

Being a Gaussian process, Vasicek does not preclude negative interest rates.
The Cox-Ingersoll-Ross (CIR) model addresses this by ensuring non-negativity.

## Libraries

numpy, matplotlib, pandas-datareader, ipywidgets

## Author

Carlo — MSc Finance student, Bocconi University