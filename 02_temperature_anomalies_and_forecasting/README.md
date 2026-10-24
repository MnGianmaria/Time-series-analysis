# Temperature Anomalies: Decomposition and Forecasting

Analysis of monthly Northern Hemisphere temperature anomalies using time series decomposition and exponential smoothing in R.

[Read the report](temperature_anomalies_and_forecasting.pdf) · [View the R Markdown source](temperature_anomalies_and_forecasting.Rmd)

## Overview

The analysis uses 1,752 monthly GISTEMP land–ocean temperature anomalies from January 1880 to December 2025, relative to the 1951–1980 baseline.

The workflow includes:

- Exploring long-term movements, autocorrelation, and rolling variability.
- Comparing classical additive and multiplicative decompositions.
- Examining fixed and time-varying seasonality using robust STL.
- Comparing simple exponential smoothing and Holt’s method.
- Producing forecasts for 2011–2025 from a model estimated on 1950–2010.
- Evaluating cumulative mean absolute error over four horizons.

Seasonal adjustment for forecasting is estimated exclusively on the training sample.

## Main Findings

An additive representation is more suitable for anomalies that include negative and near-zero values. Both STL specifications recover a similar long-term warming pattern, while allocating different amounts of variation to seasonality.

Holt’s forecasts generally underpredict anomalies in the later test years. Cumulative MAE increases from 0.120 °C over the first year to 0.239 °C over fifteen years.

| Evaluation horizon | Months | MAE (°C) |
| --- | ---: | ---: |
| 1 year | 12 | 0.120 |
| 5 years | 60 | 0.157 |
| 10 years | 120 | 0.200 |
| 15 years | 180 | 0.239 |

Each MAE averages all monthly absolute errors from January 2011 through the indicated horizon.

## Files

- [PDF report](temperature_anomalies_and_forecasting.pdf): methods, figures, and results.
- [R Markdown source](temperature_anomalies_and_forecasting.Rmd): complete analysis code.
- [Dataset](data/gistemp.csv): the CSV used in the analysis.
- [Data documentation](data/README.md): dataset details.

## Running the Analysis

Install the required R packages:

```r
install.packages(c(
  "ggplot2", "zoo", "tidyr", "scales", "dplyr",
  "forecast", "knitr", "rmarkdown"
))
```

PDF compilation also requires a LaTeX installation. If none is installed, TinyTeX can be installed with:

```r
install.packages("tinytex")
tinytex::install_tinytex()
```

Open the `.Rmd` file in RStudio and select **Knit**, or run the following command from this project folder:

```r
rmarkdown::render("temperature_anomalies_and_forecasting.Rmd")
```

An internet connection is required because the source reads the dataset from this repository’s raw GitHub URL. Package versions are not pinned.

## Limitations

The evaluation uses a single forecast origin and a dataset retrieved after 2010, rather than the historical data vintage available at that date. Prediction intervals depend on the fitted model and exclude uncertainty in seasonal adjustment.

The analysis describes statistical patterns and forecast performance; it does not identify the physical causes of temperature changes.

## Author

Gianmaria Monaco  
Bocconi University · Time Series Analysis · Academic year 2025–2026 · Group 32
