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

## Simulations and visualisation

To evaluate proposed framework, several synthetic datasets were generated containing nonlinear trend dynamics, multiple seasonal components, exogenous effects, and additive Gaussian noise(more in R folder). The objective was to assess whether the model could simultaneously recover smooth nonlinear structure and automatically identify periodic patterns through spectral analysis.

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/725dbe89-6441-4f0c-916f-06322a6586fd" /> <img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/4556ad94-bdc3-468d-958d-86da0e6ba9f5" />

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/205c0d62-916f-4b40-89cb-5f8469c516f3" /> <img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/3d0b4bc0-94d9-40a1-8061-63b575081e8a" />



Several spectral peaks can be observed, indicating that a significant part of the signal is concentrated within a relatively small number of frequencies. This is precisely the situation for which fourier-based decomposition is most effective. Rather than requiring the user to manually specify seasonal periods, the model identifies dominant frequencies directly from the data and incorporates them into the regression through sine and cosine basis functions. The fitted series demonstrates that the model successfully captures both the long-run trend and the cyclical behavior of the signal.



