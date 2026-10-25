# Italian Bond Yield Regimes: A Hidden Markov Model

Analysis of Italian government bond yields using a three-state Gaussian Hidden Markov Model in R.

[Read the report](italian_bond_yield_regimes.pdf) · [View the R Markdown source](italian_bond_yield_regimes.Rmd)

## Overview

The analysis uses 271 monthly observations on nominal Italian 10-year government bond yields, from January 1997 to July 2019.

The workflow includes:

- Comparing nominal and inflation-adjusted yields.
- Estimating a Gaussian HMM with state-specific means and variances.
- Examining transition probabilities and approximate standard errors.
- Decoding the most probable joint state sequence using Viterbi.

States are ordered by estimated mean yield and labelled low-, medium-, and high-yield. Estimation and decoding use the full sample.

## Main Findings

| State | Mean yield (%) | SD (percentage points) |
| --- | ---: | ---: |
| Low-yield | 2.137 | 0.581 |
| Medium-yield | 4.251 | 0.377 |
| High-yield | 5.639 | 0.713 |

The fitted states are highly persistent. The high-yield state appears near the beginning of the sample and during 2011–2012, while the low-yield state covers the final years.

Few decoded transitions and boundary probability estimates limit the interpretation of persistence and parameter uncertainty. State labels do not independently identify economic expansions or crises.

## Files

- [PDF report](italian_bond_yield_regimes.pdf): methods, tables, figures, and interpretation.
- [R Markdown source](italian_bond_yield_regimes.Rmd): complete analysis code.
- [Dataset](data/italian_bond_yields.csv): the observations used in the analysis.
- [Data documentation](data/README.md): provenance and variable descriptions.

## Running the Analysis

Install the required R packages:

```r
install.packages(c(
  "ggplot2", "depmixS4", "knitr", "rmarkdown"
))
```

PDF compilation requires LaTeX. If needed, install TinyTeX:

```r
install.packages("tinytex")
tinytex::install_tinytex()
```

Open the `.Rmd` file in RStudio and select **Knit**, or run this command from the project folder:

```r
rmarkdown::render("italian_bond_yield_regimes.Rmd")
```

An internet connection is required because the source reads the dataset from this repository’s raw GitHub URL. A random seed is specified, but package versions are not pinned and numerical results may vary slightly across environments.

## Limitations

The model fixes the number of states at three, assumes constant transition probabilities, and excludes additional serial dependence conditional on the states.

Estimation uses one initialization, so a global likelihood maximum is not established. Approximate standard errors exclude boundary parameters and depend on the model assumptions.

The analysis is retrospective and does not establish real-time classification or forecasting performance.

## Author

Gianmaria Monaco  
Bocconi University · Time Series Analysis · Academic year 2025–2026 · Group 32
