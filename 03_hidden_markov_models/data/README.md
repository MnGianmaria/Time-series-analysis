# Data

[italian_bond_yields.csv](italian_bond_yields.csv) contains 271 monthly
observations from January 1997 to July 2019, with no missing values.

The dataset was supplied with the course materials and described
as compiled mainly from OECD data.

## Variables

| Column | Description |
| --- | --- |
| Time | Observation date, formatted as YYYY_MM_DD |
| ITAbond_nom | Nominal yield on 10-year Italian government bonds (%) |
| inflation | Inflation measure based on the HICP |
| Moodys | Numerically coded Moody’s credit rating |
| Fitch | Numerically coded Fitch credit rating |
| ITAbond_real | Nominal yield minus inflation |
| gdp | GDP-related variable; not used in this analysis |

## Use in the Analysis

The three-state Gaussian Hidden Markov Model uses `ITAbond_nom`.
Nominal and inflation-adjusted yields are compared descriptively.

Credit ratings and GDP are not included in the model.
