# Nile Flow: Filtering and Smoothing with a Dynamic Linear Model

Analysis of annual Nile flow using a Gaussian local level model, distinguishing sequential filtering, one-step-ahead prediction, and retrospective smoothing.

## Files

- [Read the report](nile_dynamic_linear_model.pdf)
- [View the R Markdown source](nile_dynamic_linear_model.Rmd)

## Analysis

The workflow includes:

- Kalman filtering and credible intervals for the latent level.
- One-step-ahead forecasts and prediction intervals for observed flow.
- Sensitivity to observation and state innovation variances.
- Standardized forecast errors and residual diagnostics.
- Smoothing and a comparison of state estimates for 1898.
- Maximum-likelihood estimation of the two variance parameters.

The interpretation distinguishes uncertainty about the latent state from uncertainty about future observations.

## Data

The analysis uses `Nile`, included in R's `datasets` package. It contains 100 annual observations of Nile flow at Aswan from 1871 to 1970, measured in units of 10⁸ m³.

No external data files are required.

## Reproducing the Report

Required R packages: `ggplot2`, `dlm`, `knitr`, and `rmarkdown`.

Open `nile_dynamic_linear_model.Rmd` in RStudio and select **Knit to PDF**. PDF compilation requires a LaTeX installation.

## Interpretation and Limitations

The model assumes Gaussian, independent observation and state innovations with constant variances. It describes changes in the latent level without explicitly identifying structural breaks or their causes.

Smoothing uses the full sample and therefore provides a retrospective reconstruction. State intervals condition on the specified variances and exclude parameter uncertainty. Maximum-likelihood estimates and their approximate standard errors depend on the fixed initial distribution.

## Author

Gianmaria Monaco  
Bocconi University · Time Series Analysis · Academic year 2025–2026 · Group 32
