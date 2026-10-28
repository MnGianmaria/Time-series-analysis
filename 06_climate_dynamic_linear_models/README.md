# Temperature Anomalies: Dynamic Linear Models

Analysis of Northern Hemisphere temperature anomalies using local level and local linear trend models, with Kalman filtering, smoothing, and sequential forecast evaluation.

## Report and Source

- [Read the report](06_climate_dynamic_linear_models.pdf)
- [View the R Markdown source](06_climate_dynamic_linear_models.Rmd)

## Analysis

Monthly GISTEMP observations for 1880–2024 are seasonally adjusted using periodic STL.

The analysis includes:

- Maximum-likelihood estimation of model variances.
- Kalman filtering and smoothing with conditional state intervals.
- Sequential one-step-ahead forecasts for 2005–2024.
- Comparison through RMSE, autocorrelation diagnostics, and normal Q-Q plots.

Both models achieve very similar test RMSE. Forecast errors retain substantial serial dependence, indicating limitations of these specifications.

## Data

The source reads `gistemp.csv` from the `02_temperature_anomalies_and_forecasting/data` folder of this repository through its raw GitHub URL. An internet connection is required.

For forecast evaluation, seasonal effects and model parameters are estimated using the training sample only.

## Reproduce

Open `06_climate_dynamic_linear_models.Rmd` in RStudio and select **Knit → Knit to PDF**.

Required R packages: `ggplot2`, `zoo`, `dlm`, `knitr`, and `rmarkdown`. A LaTeX installation is also required.

## Limitations

State intervals exclude parameter and seasonal-adjustment uncertainty. Evaluation uses a single chronological split and revised historical data; it does not establish long-horizon or real-time forecasting performance.

## Author

Gianmaria Monaco  
Bocconi University · Time Series Analysis · Academic year 2025–2026 · Group 32
