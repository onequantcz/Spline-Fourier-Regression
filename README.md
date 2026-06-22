# Spline-Fourier-Regression
Flexible extrapolator, inspired by PROPHET.

A lightweight forecasting and signal extraction framework written entirely in base R.
The model combines:

- Cubic B-spline regression
- Automatic Fourier seasonality detection
- Ridge regularization
- Exogenous regressors

The goal is to provide a highly flexible non-linear forecasting model capable of approximating arbitrary smooth relationships while automatically extracting dominant seasonal patterns. Should be used NOT for interpretability, but rather for fitting and exprapolating time series with hard non-linear structure with different regimes.

<img width="679" height="83" alt="image" src="https://github.com/user-attachments/assets/92d7336c-9970-4cc1-a934-90328a40ce37" />


