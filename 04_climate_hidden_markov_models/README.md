# Temperature Anomalies: Hidden Markov Models

Analysis of Northern Hemisphere temperature anomalies using Gaussian Hidden Markov Models with state-dependent levels and linear trends.

## Files

- [Read the report](climate_hidden_markov_models.pdf)
- [View the R Markdown source](climate_hidden_markov_models.Rmd)

## Analysis

Monthly GISTEMP anomalies are seasonally adjusted using periodic STL. Gaussian HMMs with two to five states are then compared using AIC and BIC.

The analysis covers:

- Full-sample models with state-specific mean levels.
- A separate analysis of the sample ending in 1975.
- Models with state-specific linear trends.
- Viterbi decoding, state persistence, and residual diagnostics.

Estimation uses 25 initializations per candidate level model and 150 per candidate trend model, retaining the fit with the highest log-likelihood.

## Data

The analysis reuses the [GISTEMP dataset stored in this repository](../02_temperature_anomalies_and_forecasting/data/gistemp.csv).

Observations cover January 1880–December 2025. Anomalies are expressed in degrees Celsius relative to the 1951–1980 reference period.

## Reproducing the Report

Required R packages: `ggplot2`, `zoo`, `depmixS4`, `knitr`, and `rmarkdown`.

Open `climate_hidden_markov_models.Rmd` in RStudio and select **Knit to PDF**. PDF compilation requires a LaTeX installation. The source downloads the dataset from this repository, so an internet connection is required.

The analysis performs 800 model fits. A complete run may take 15 minutes or longer, depending on the computer.

## Interpretation and Limitations

The decoded states provide a retrospective statistical description, rather than independently identified physical climate regimes.

Model selection is limited to two through five states. Multiple initializations reduce sensitivity to local likelihood maxima but do not guarantee a global optimum. Residual serial dependence and uncertainty in seasonal adjustment and state assignments also limit interpretation.
