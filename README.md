# Spline-Fourier-Regression
Flexible extrapolator, inspired by PROPHET.

A lightweight forecasting and signal extraction framework written entirely in base R.
The model combines:

- Cubic B-spline regression
- Automatic Fourier seasonality detection
- Ridge regularization
- Exogenous regressors

The goal is to provide a highly flexible non-linear forecasting model capable of approximating arbitrary smooth relationships while automatically extracting dominant seasonal patterns. Should be used NOT for interpretability, but rather for fitting and exprapolating time series with hard non-linear structure with different regimes.

## Motivation

Classical linear regression often fails to capture non-linear effects. ARIMA-type models assume a specific stochastic structure. However, some time series (aspecially related to demand or product-driven) either have no reliable hypothesis of stochastic structure, or obvious solution could be very complicated computationaly. 
This project aims to build a general-purpose regression framework that:

- Learns arbitrary smooth effects of explanatory variables.
- Automatically extracts dominant seasonal frequencies.
- Supports exogenous variables.
- Uses regularization to prevent overfitting.
- Remains interpretable.
- Can be further extended in Biasian paradigm with simulations. 

## Mathematical Formulation
The model is basically

<img width="679" height="83" alt="image" src="https://github.com/user-attachments/assets/92d7336c-9970-4cc1-a934-90328a40ce37" />

Each explanatory variable is transformed into a cubic B-spline basis (polynomial function, 3. degree). This allows the model to learn highly non-linear relationships while preserving smoothness. 

Seasonality is extracted through the periodogram. The frequencies corresponding to the largest spectral peaks are selected. This allows automatic discovery of seasonal patterns without specifying their periods manually. 

o reduce overfitting, separate ridge penalties are applied for spline and fourier coefficients. 

