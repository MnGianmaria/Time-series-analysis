# Data

This folder contains the two datasets used in the report.

## GISTEMP — `gistemp.csv`

Monthly Northern Hemisphere land–ocean temperature anomalies, expressed in degrees Celsius relative to the 1951–1980 reference period.

The analysis uses 1,752 monthly observations from January 1880 to December 2025. Annual and seasonal summary columns are not used.

## GHCN — `ghcn_maine.csv`

Daily weather observations for Houlton AP and Augusta State AP in Maine, extracted from the dataset supplied for the coursework.

The file preserves the available observations for both stations over June 1948–December 2024. The analysis uses daily maximum temperature (`TMAX`), converted from tenths of a degree Celsius to degrees Celsius during data preparation.

Houlton has a 944-day gap from May 1, 1985 to November 30, 1987. The analysis therefore uses January 1, 1988–December 31, 2024, a complete common period containing 13,515 consecutive daily observations per station. No observed temperatures are interpolated.

Seasonal adjustment is performed in the R Markdown source. Both files contain the input data before that adjustment.
