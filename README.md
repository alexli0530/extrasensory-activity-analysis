# Social Context and Physical Activity — ExtraSensory

This repository contains a **team project completed for COGS 108: Data Science in Practice at UC San Diego**.

The project studies whether a person's social context — especially being **alone, with friends, or with coworkers** —
is associated with the probability of being physically active in the same minute. The analysis uses the
**ExtraSensory** smartphone/smartwatch dataset together with contextual information from **NOAA hourly weather data**
and a **2015 non-workday / holiday calendar**.

## Recommended Version

If you are visiting this repository as part of a portfolio or recruiting review, please start with:

**`ExtraSensory_Portfolio_Clean.ipynb`**

This is a presentation-oriented version assembled from the original course notebooks. It removes course-template
instructions, placeholder text, and redundant setup material while preserving the project's analysis, code, methods,
outputs, and conclusions.

The repository also keeps the original course files so that the class submission and team-project context remain transparent:

- `02-EDACheckpoint.ipynb` — original exploratory-data-analysis checkpoint
- `03-FinalProject.ipynb` — original final course report
- `ExtraSensory_Portfolio_Clean.ipynb` — cleaned portfolio version recommended for readers

## Research Question

Using minute-level ExtraSensory data, is social context associated with the probability that a person is physically
active in the same minute, after accounting for time of day, environment, weather, holidays, and repeated observations
within individuals?

The outcome variable, `active_minute`, is defined as 1 when a minute is labeled as walking, running, or bicycling,
and 0 otherwise.

## Data and Methods

The project uses:

- **ExtraSensory** minute-level behavioral/context data from 60 users
- approximately **377,000 minute-level observations** in the combined raw load
- **NOAA Global Hourly** weather data
- a **2015 non-workday / holiday calendar**

Main techniques used in the project include:

- Python data processing with **pandas** and **NumPy**
- timestamp conversion and date/hour key construction
- missing-label handling and validation checks
- multi-source dataset integration
- descriptive statistics and grouped comparisons
- data visualization with **Matplotlib**
- exploratory analysis of:
  - social-context activity rates
  - time-of-day patterns
  - indoor/outdoor and home/workplace context
  - temperature
  - holidays / non-workdays
  - user-level heterogeneity
- baseline **logistic regression**
- clustered logistic regression using **Generalized Estimating Equations (GEE)**
- participant-level clustering with `user_id`
- categorical controls for time of day, temperature, and social context

## My Contributions — Alex Li

This was a collaborative project. My work included both research/design responsibilities and hands-on data-analysis work.

### Research and project design
- Helped formulate the central research question connecting **social context** with **minute-level physical activity**.
- Conducted background research and literature review on social support, social integration, and physical activity.
- Contributed to the operational definition of `active_minute` and the choice of contextual controls.
- Helped coordinate the project and wrote substantial portions of the original report.

### Data processing and integration
- Worked on preprocessing and validation of the ExtraSensory data.
- Converted timestamps into analysis-ready date/time variables and checked observation-level consistency.
- Integrated the behavioral data with **NOAA hourly weather data**.
- Integrated a **holiday / non-workday calendar** and constructed date-based indicators.
- Checked merge behavior, missingness, duplicate keys, and coverage of the merged datasets.

### Exploratory data analysis
I contributed substantially to the EDA code, including analysis of:

- baseline physical-activity and social-context rates;
- activity conditional on being with friends / coworkers;
- **time-of-day** patterns and time-of-day confounding;
- **environmental context** such as home, workplace, indoors, and outdoors;
- **user-level heterogeneity**, motivating methods that account for repeated observations;
- **temperature** distributions and temperature bins;
- **holiday / non-workday** differences;
- interactions between social context and environmental conditions.

This work used Python tools including **pandas, NumPy, and Matplotlib**, together with grouped summaries, pivot tables,
feature construction, dataset merges, and visualization.

### Modeling context
The final project compared a baseline logistic-regression specification with a **GEE clustered logistic model** that
groups observations by participant. The modeling and final interpretation were completed collaboratively by the team.

## Main Result

Raw descriptive patterns showed substantially higher activity rates when participants were with friends or coworkers
than when they were alone. After accounting for repeated observations and contextual controls using GEE, the
social-context coefficients were no longer statistically significant. Environmental setting and time of day explained
much of the observed difference.

The result illustrates why descriptive differences should be interpreted cautiously when behavior is strongly tied to
time, place, and repeated observations from the same individuals.

## Team and Acknowledgments

This project was completed by:

- **Alex Li**
- **Alexander Zhang**
- **Zongxi He**
- **Jack Ding**
- **Logan Zeto**

I am grateful to my teammates for their contributions across **analysis, methodology, data curation, software,
visualization, interpretation, and editing**. The original course notebooks preserve the formal team-role summary used
for the class submission.

## Data Availability

The repository does **not** include the original raw datasets. The raw ExtraSensory files are relatively large, and the
purpose of this repository is to present the analysis rather than redistribute the full source data.

The processed CSV files used by the notebooks are also **not included in this portfolio repository** because some of
them exceed GitHub's browser-upload size limit. Their expected locations are documented under `data/README.md`.

To reproduce the full project from source data:

1. Download the ExtraSensory data from the official UC San Diego ExtraSensory website:
   https://extrasensory.ucsd.edu/
2. Download the 2015 NOAA Global Hourly station file used in the project:
   https://www.ncei.noaa.gov/data/global-hourly/access/2015/72290023188.csv
3. Follow the preprocessing code preserved in `02-EDACheckpoint.ipynb`.
4. Place the generated processed files under `data/02-processed/` using the filenames listed in `data/README.md`.

## Notes on the Portfolio-Clean Version

`ExtraSensory_Portfolio_Clean.ipynb` is **not a new independent project**. It is a cleaned presentation copy of the
original COGS 108 team project. The edits are organizational only: course instructions, placeholder text, and redundant
setup material were removed or renamed for readability. The underlying project, methods, results, and team attribution
remain the same.
