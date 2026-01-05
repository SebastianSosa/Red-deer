# Data from: Associations between lifetime fitness and social bonds in female red deer

**Author:** Sebastian Sosa
**License:** CC0 1.0 Universal (CC0 1.0) Public Domain Dedication

## Data Overview

This dataset contains four data files required to interpret the results of the associated publication. The files contain summary metrics for individual female deer, longitudinal survival data, and calf survival data.

**Note on Scaling:** Files with "scaled" in the filename contain data that have been centered and scaled (Z-scores) to facilitate statistical modeling.

### File List
1.  `life_time_data.csv`
2.  `scaled_life_time_data.csv`
3.  `scaled_annual.csv`
4.  `scaled_calves_survival.csv`

---

## File Descriptions

### 1. life_time_data.csv AND scaled_life_time_data.csv
**Description:** Summary metrics for individual female deer calculated over their entire lifespan.
**Row definition:** One row per individual female.

*   `id`: Unique identifier for the individual female deer (alphanumeric string).
*   `lifespan`: Total years lived (unit: years).
*   `sum_degree`: The sum of the individual's annual degree centrality scores over its lifetime (count).
*   `sum_strength`: The sum of the individual's annual social strength scores (sum of weighted ties).
*   `sum_eigen`: The sum of the individual's annual eigenvector centrality scores (unitless index).
*   `mean_mat`: Average matrilineal rank or status during the individual's life (numeric rank).
*   `mean_matSize`: Average size of the individual's matriline over its life (unit: count of individuals).
*   `mean_HRO`: Mean Home Range Overlap index (unitless index, 0-1).
*   `mean_N`: Mean spatial coordinate - Northings (unit: meters, UK Ordnance Survey grid).
*   `mean_E`: Mean spatial coordinate - Eastings (unit: meters, UK Ordnance Survey grid).
*   `matriline`: The specific matrilineal group name/ID the individual belonged to (categorical).
*   `LRS`: Lifetime Reproductive Success - Total number of calves produced that survived to 1 year (unit: count of calves).
*   `LBS`: Lifetime Breeding Success - Total number of calves born (unit: count of calves).
*   `mean.grp.size`: Average size of the social groups the individual was observed in (unit: count of individuals).
*   `matSize`: Final or average size of the matriline (unit: count of individuals).

### 2. scaled_annual.csv
**Description:** Longitudinal data used for survival analysis.
**Row definition:** One row per individual per year (person-year format).

*   `id`: Unique identifier for the individual (alphanumeric string).
*   `year`: The calendar year of observation (unit: year).
*   `degree`: Number of social associates in that year (count).
*   `strength`: Sum of the weights of social ties in that year (sum of weights).
*   `eigen`: Eigenvector centrality in that year (unitless index).
*   `mat`: Matriline identifier (categorical).
*   `start`: Start time of the interval for survival modeling (unit: age in years).
*   `end`: End time of the interval for survival modeling (unit: age in years).
*   `death`: Binary indicator of mortality (1 = died in this interval, 0 = survived).
*   `DeathYear`: Calendar year of death (unit: year).
*   `BirthYear`: Calendar year of birth (unit: year).
*   `lastSeen`: The last calendar year the individual was observed alive (unit: year).
*   `matSize`: Number of individuals in the matriline in that year (count).
*   `HRO2`: Home Range Overlap metric for that year (unitless index).
*   `LifetimeE`: The overall lifetime average spatial coordinate - Eastings (unit: meters).
*   `LifetimeN`: The overall lifetime average spatial coordinate - Northings (unit: meters).
*   `centroid`: Spatial centroid of the individual's sightings (coordinate pair).
*   `sex`: Biological sex (all "F" for females).

### 3. scaled_calves_survival.csv
**Description:** Data linking maternal social traits to the survival of specific offspring.
**Row definition:** One row per calf.

*   `ego`: Unique identifier for the calf (alphanumeric string).
*   `ego.birth`: Calendar year the calf was born (unit: year).
*   `ego.mom`: Unique identifier for the calf's mother (alphanumeric string).
*   `ego.survived.frist.year`: Binary survival indicator (1 = calf survived to 1 year of age, 0 = died).
*   `mom.degree`: The mother's degree centrality in the year of the calf's birth (count).
*   `mom.strength`: The mother's social strength in the year of the calf's birth (sum of weights).
*   `mom.eigen`: The mother's eigenvector centrality in the year of the calf's birth (unitless index).
*   `mom.obs`: Number of times the mother was observed/sampled in that year (count).
*   `matSize`: Size of the matriline in the year of birth (count).
*   `id`: Maternal ID, matches `ego.mom` (alphanumeric string).
*   `HRO2`: Maternal Home Range Overlap index (unitless index).
*   `LifetimeE`: Maternal spatial metric - Eastings (unit: meters).
*   `LifetimeN`: Maternal spatial metric - Northings (unit: meters).
*   `centroid`: Maternal spatial centroid.

---

## Code and Software Availability

The analysis code (`red_deer_analysis.qmd`) and auxiliary network data files (`MRQAP_data.RData`) are not included in this Dryad package but are available for download at Zenodo to facilitate reproducibility.

**Software/Code Location:**
[INSERT LINK TO YOUR ZENODO OR GITHUB REPOSITORY HERE]

**Software Requirements:**
*   R (v4.2.0 or later)
*   Quarto
*   R Packages: ANTs, lme4, lmerTest, sjPlot, ggplot2, MASS, asnipe, survival, survminer, rptR, PerformanceAnalytics, gtsummary, coxme.