# Time Series Analysis in R

Seven projects exploring time series decomposition, forecasting,
Hidden Markov Models, and Dynamic Linear Models through
applications to temperature anomalies, government bond yields,
river flow, and other observed series.

The projects move from exploratory decomposition and exponential
smoothing to latent-state models, distinguishing retrospective
reconstruction, sequential prediction, and forecast evaluation.

## Projects

| Project | Focus | Report |
| --- | --- | --- |
| [01 · Decomposition and Exponential Smoothing](01_decomposition_and_smoothing/) | Trend and seasonality, transformations, classical decomposition, STL, and simple exponential smoothing across several datasets. | [PDF](01_decomposition_and_smoothing/decomposition_and_smoothing.pdf) |
| [02 · Temperature Anomalies: Decomposition and Forecasting](02_temperature_anomalies_and_forecasting/) | Monthly Northern Hemisphere anomalies, seasonal adjustment, exponential smoothing, and forecasts evaluated over 2011–2025. | [PDF](02_temperature_anomalies_and_forecasting/temperature_anomalies_and_forecasting.pdf) |
| [03 · Italian Bond Yield Regimes](03_hidden_markov_models/) | A three-state Gaussian HMM for monthly Italian government bond yields, with transition probabilities and Viterbi decoding. | [PDF](03_hidden_markov_models/italian_bond_yield_regimes.pdf) |
| [04 · Temperature Anomalies: Hidden Markov Models](04_climate_hidden_markov_models/) | State-dependent levels and linear trends, model selection, multiple initializations, and retrospective state decoding. | [PDF](04_climate_hidden_markov_models/climate_hidden_markov_models.pdf) |
| [05 · Nile Flow: A Dynamic Linear Model](05_nile_dynamic_linear_model/) | Kalman filtering, one-step prediction, smoothing, variance sensitivity, and maximum-likelihood estimation. | [PDF](05_nile_dynamic_linear_model/nile_dynamic_linear_model.pdf) |
| [06 · Temperature Anomalies: Dynamic Linear Models](06_climate_dynamic_linear_models/) | Local level and local linear trend models, conditional state intervals, and sequential forecast evaluation over 2005–2024. | [PDF](06_climate_dynamic_linear_models/06_climate_dynamic_linear_models.pdf) |
| [07 · Climate Trends and Weather Prediction](07_climate_and_weather_models/) | HMM and DLM representations of temperature anomalies, followed by a comparison of three bivariate models for daily temperatures at two weather stations. | [Project folder](07_climate_and_weather_models/) |

Each project folder contains its own README with the analysis
scope, file links, data information, reproduction instructions,
and limitations.

## Data and Applications

The decomposition project uses datasets included in R alongside
Italian daily COVID-19 observations. The financial application
uses monthly Italian 10-year government bond yields from
January 1997 to July 2019, while the Nile application uses
annual flow observations from 1871 to 1970.

The climate projects use monthly GISTEMP Northern Hemisphere
land–ocean temperature anomalies relative to the 1951–1980
reference period. Projects 02, 04, and 07 cover January
1880–December 2025; Project 06 analyzes 1880–2024.

Project 07 also uses GHCN daily maximum temperatures at
Houlton AP and Augusta State AP in Maine. The station pair
follows the assignment's suggestion. Modelling is restricted
to January 1988–December 2024, providing 13,515 consecutive
daily observations per station after an earlier prolonged
gap in Houlton's record. The original station records are
retained in the data file; the analysis selects this common
period without interpolating missing temperatures.

Data files and their documentation are linked from the
individual project READMEs.

## Reproducing the Analyses

The reports are written in R Markdown. To reproduce a project:

1. Download or clone the repository.
2. Open the project's README and install its required R packages.
3. Open the `.Rmd` source in RStudio and select **Knit to PDF**.

PDF rendering requires a LaTeX installation. If needed,
TinyTeX can be installed from R:

```r
install.packages("tinytex")
tinytex::install_tinytex()
```

Alternatively, render a report from its project folder:

```r
rmarkdown::render("decomposition_and_smoothing.Rmd")
```

Replace the filename with the source listed in the relevant
project README.

Several sources retrieve data through raw GitHub URLs and
therefore require an internet connection. Computational
requirements vary: the climate HMM analysis in Project 04
fits many initializations and can take substantially longer
than the other examples.

Package versions are not pinned, so numerical results may
vary across environments, particularly for models estimated
through iterative optimization.

## Interpreting the Results

The projects distinguish descriptive fit from predictive
performance. Projects 02 and 06 include held-out forecast
evaluation under their stated designs, whereas Project 07
compares weather predictions using parameters and seasonal
components estimated on the full sample.

Decoded HMM states are statistical classifications rather
than independently established physical or economic regimes.
Likewise, smoothed latent levels are retrospective estimates,
and state intervals differ from prediction intervals for
future observations. The reports discuss these distinctions
alongside residual dependence, boundary estimates, and other
limitations of the fitted specifications.

## Author

Gianmaria Monaco  
Bocconi University · Time Series Analysis  
Academic year 2025–2026 · Group 32
