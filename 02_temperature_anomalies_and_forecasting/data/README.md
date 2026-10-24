# Data

## Dataset

[gistemp.csv](gistemp.csv) contains Northern Hemisphere land–ocean
temperature anomalies from GISTEMP, relative to the 1951–1980
reference period. Values are expressed in degrees Celsius.

The file was supplied with the course materials and is retained
here as the dataset used in the analysis.

## Structure and Preparation

- Coverage: January 1880–December 2025.
- Each row represents a calendar year.
- The analysis uses only the January–December columns.
- Annual and seasonal summary columns are excluded.
- Missing-value markers (`***`) are read as `NA`.
- The selected monthly columns contain 1,752 observations with no missing values.

The first descriptive line is skipped when importing the CSV.

## Reproducibility

The R Markdown source reads this file through its raw GitHub URL.
This copy is not automatically updated from GISTEMP and does not
represent the historical data vintage available in 2010.
