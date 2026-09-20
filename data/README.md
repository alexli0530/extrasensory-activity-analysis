# Data

This folder documents the data layout expected by the original COGS 108 notebooks.

## Why the data files are not included

The repository does **not** contain the original raw ExtraSensory dataset, and it also does not include the larger
processed CSV files used during analysis. Some of these files exceed GitHub's browser-upload size limit.

The notebooks and repository structure are preserved so that the data pipeline can still be reproduced from the
original sources.

## Expected processed files

The main EDA and final-analysis notebooks expect the following files under:

`data/02-processed/`

```text
extrasensory_processed_model.csv
noaa_hourly_cleaned.csv
non_workdays_2015.csv
ex2_processed.csv
```

These are the filenames referenced directly by the notebooks.

## Original data sources

### ExtraSensory

The primary behavioral dataset is the **ExtraSensory Dataset — Features and Cleaned Context Labels** from UC San Diego.

Official project website:

https://extrasensory.ucsd.edu/

The original course project used the ExtraSensory features/context-label files and combined data from 60 users.

### NOAA Global Hourly Weather Data

The weather data come from NOAA / NCEI Global Hourly.

The specific 2015 station file used in the project is:

https://www.ncei.noaa.gov/data/global-hourly/access/2015/72290023188.csv

### Non-workday / holiday data

`non_workdays_2015.csv` is a derived project file used as a contextual control for weekends / holidays.

## Reproducing the processed data

The preprocessing and integration steps are preserved in `02-EDACheckpoint.ipynb`.

That notebook includes the logic for:

- loading and combining ExtraSensory files;
- selecting analysis variables;
- creating processed modeling tables;
- cleaning NOAA temperature data;
- constructing holiday / non-workday indicators;
- merging weather and calendar information with the behavioral data;
- creating the final merged dataset used by later analysis.

After running the preprocessing pipeline, place the resulting files under `data/02-processed/` with the filenames listed above.
