# Time Series Decomposition and Exponential Smoothing

An exploration of trend, seasonality, and simple exponential smoothing in R.

**[Read the report](decomposition_and_smoothing.pdf)** ·
**[View the source code](decomposition_and_smoothing.Rmd)**

## Analysis

- **Simulated series:** time series objects and a random walk.
- **AirPassengers:** classical multiplicative decomposition, additive decomposition of logarithms, and periodic STL.
- **Atmospheric CO₂:** additive decomposition and removal of trend and seasonality.
- **UK gas consumption:** comparison of decomposition on original and logarithmic scales.
- **Nile river flow:** simple exponential smoothing with estimated and fixed smoothing parameters.
- **Italian COVID-19 data:** descriptive plots and smoothing of daily reported cases.

## Main Findings

Logarithmic transformations reduce differences in seasonal amplitude in the AirPassengers and UKgas series. However, repeating seasonal components are imposed by the selected specifications and do not demonstrate that observed seasonality is constant.

For the Nile series, the estimated smoothing parameter yields the lowest in-sample MAPE among the three specifications compared. For daily COVID-19 cases, the estimated parameter is close to one, making fitted values highly responsive to recent observations.

The analysis distinguishes decomposition and in-sample fitting from evidence of forecasting accuracy. No held-out forecast evaluation is performed.

## Run the Analysis

The source requires R and the following packages:

```r
install.packages(c(
  "ggplot2", "zoo", "tidyr", "scales", "knitr", "rmarkdown"
))
```

PDF rendering also requires a LaTeX installation. If needed, install TinyTeX:

```r
install.packages("tinytex")
tinytex::install_tinytex()
```

Open `decomposition_and_smoothing.Rmd` in RStudio and select **Knit to PDF**.

Alternatively, run this command from the folder containing the source:

```r
rmarkdown::render("decomposition_and_smoothing.Rmd")
```

An Internet connection is required because the source retrieves the COVID-19 dataset from this repository. Package versions are not pinned.

## Data

AirPassengers, co2, UKgas, and Nile are included in R's datasets package.

The COVID-19 data file is stored in
[data/coronavirus-data.txt](data/coronavirus-data.txt).
The analysis covers 20 February 2020 to 11 February 2021.

## Author

Gianmaria Monaco  
Bocconi University — Time Series Analysis  
Academic Year 2025–2026 — Group 32
