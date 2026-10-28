# Climate Trends and Weather Prediction

Analysis of Northern Hemisphere temperature anomalies and daily temperatures at two Maine weather stations using Hidden Markov Models and Dynamic Linear Models in R.

[Read the report](climate_and_weather_models.pdf) · [View the R Markdown source](climate_and_weather_models.Rmd)

## Overview

The project contains three connected applications:

1. **Climate states:** Gaussian Hidden Markov Models with two to five states, compared using AIC and BIC, with Viterbi decoding of the selected model.
2. **Climate levels and decadal changes:** random walk plus noise and local linear trend models, estimated by maximum likelihood and reconstructed through Kalman filtering and smoothing.
3. **Joint weather modelling:** three bivariate local-level models for Houlton AP and Augusta State AP, comparing independent, unrestricted, and distance-based innovation covariance structures.

Seasonal adjustment uses periodic STL. Climate reconstructions and weather prediction comparisons use parameters and seasonal components estimated from the full samples.

## Main Findings

### Climate

The five-state HMM achieves the lowest AIC and BIC among the two- to five-state candidates. Its decoded states summarize changing temperature levels, without independently identifying physical climate regimes.

The random walk and local linear trend models produce nearly indistinguishable level reconstructions. The estimated slope innovation variance is numerically near zero, making the fitted local linear trend model approximately a random walk with constant drift.

Ten-year changes in the smoothed level are predominantly positive in recent decades but retain substantial interannual variability. These overlapping differences describe changes between endpoints ten years apart; they do not provide a formal test of acceleration.

### Weather

Allowing correlated level innovations substantially improves the joint likelihood. AIC and BIC favour the unrestricted covariance model, but improvements in point prediction are small.

| Model | Covariance structure | Pooled RMSE (°C) |
| --- | --- | ---: |
| M1 | Independent | 4.410 |
| M2 | Unrestricted | 4.398 |
| M3 | Distance-based | 4.399 |

All three models retain short-lag autocorrelation in their prediction errors, indicating temporal dynamics left unexplained by the local-level specifications.

With only one station pair, the distance-based model cannot establish a geographical decay relationship that generalizes to other distances.

## Data

- **GISTEMP:** 1,752 monthly Northern Hemisphere land–ocean temperature anomalies from January 1880 to December 2025, relative to the 1951–1980 reference period.
- **GHCN weather observations:** daily maximum temperatures at Houlton AP and Augusta State AP in Maine. The stored dataset preserves the available observations for both stations over June 1948–December 2024.

The weather analysis uses January 1988–December 2024, comprising 13,515 consecutive daily observations per station. This common period avoids Houlton’s 944-day gap during 1985–1987 without interpolating observed temperatures or compressing the time axis.

Weather seasonal adjustment is estimated on a 365-day calendar and mapped back to the complete daily record. All observed leap-day temperatures are retained.

See [data documentation](data/README.md) for details.

## Files

- [PDF report](climate_and_weather_models.pdf): methods, figures, tables, and interpretation.
- [R Markdown source](climate_and_weather_models.Rmd): complete analysis code.
- [GISTEMP dataset](data/gistemp.csv).
- [Weather dataset](data/ghcn_maine.csv).
- [Data documentation](data/README.md).

## Reproducing the Report

Install R and the required packages:

```r
install.packages(c(
  "ggplot2", "dplyr", "tidyr", "zoo", "depmixS4",
  "dlm", "knitr", "patchwork", "rmarkdown"
))
```

PDF compilation also requires LaTeX. If needed, install TinyTeX:

```r
install.packages("tinytex")
tinytex::install_tinytex()
```

Open `climate_and_weather_models.Rmd` in RStudio and select **Knit to PDF**, or run this command from the project folder:

```r
rmarkdown::render("climate_and_weather_models.Rmd")
```

The source first looks for datasets in the local `data` folder and falls back to this repository’s raw GitHub URLs if they are unavailable. An internet connection is required for that fallback.

HMM estimation uses 25 initializations per candidate model, and each weather model uses three starting parameter vectors. Some estimation chunks are cached, so the first render may take longer than subsequent runs. Package versions are not pinned, and numerical results may vary slightly across environments.

## Interpretation and Limitations

Climate state assignments and smoothed levels are retrospective reconstructions. The weather errors are in-sample one-step-ahead prediction errors, rather than a held-out assessment of forecasting performance.

State intervals condition on the estimated model parameters and seasonal adjustment. Near-boundary variance and correlation estimates require caution when interpreting approximate standard errors.

The analyses describe statistical patterns in the supplied records; they do not establish physical causes, real-time forecasting accuracy, or performance at longer horizons.

## Author

Gianmaria Monaco  
Bocconi University · Time Series Analysis · Academic year 2025–2026 · Group 32
