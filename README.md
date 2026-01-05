# Reproducibility for: "Associations between lifetime fitness and social bonds in female red deer"

This repository contains the data and Quarto document necessary to reproduce the analyses and figures for the paper investigating the link between sociality, fitness, and survival in female red deer (*Cervus elaphus*).

**Author:** Sebastian Sosa

---

Sharing/Access Information
License:
This dataset is made available under a CC0 1.0 Universal (CC0 1.0) Public Domain Dedication. You may copy, modify, and distribute the data without restriction. While not legally required, we request that users cite the original publication and this repository when using these data for secondary analyses.

---

## Repository Content

This repository contains all the necessary components to reproduce the analysis in a self-contained manner.

*   `red_deer_analysis.qmd`: The Quarto source file containing all R code for data loading, analysis, and figure/table generation.
*   **`in the root directory`**: The folder containing the data files required by the analysis:
    *   `MRQAP_data.RData`
    *   `annual_data.csv`
    *   `scaled_life_time_data.csv`
    *   `life_time_data.csv`
    *   `scale_annual.csv`
    *   `scaled_calves_survival.csv`

---
## Data Availability

The primary data for this analysis are archived at Dryad:
[https://zenodo.org/records/18152463](https://zenodo.org/records/18152463)

While copies of the data are included in this repository for reproducibility, 
the Dryad submission should be considered the permanent record for the dataset. 
Please cite the Dryad package if you use this data for secondary analyses.

## Data Overview

The dataset includes six data files. "Scaled" files are versions of the raw data that have been centered and scaled (Z-scores) to facilitate statistical modeling.

### 1. life_time_data.csv / scaled_life_time_data.csv
*   **Description:** Summary metrics for individual female deer calculated over their entire lifespan.
*   **Row definition:** One row per individual female.
*   **Variables:**
    *   `id`: Unique identifier for the individual female deer.
    *   `lifespan`: Total years lived (numeric).
    *   `sum_degree`: The sum of the individual's annual degree centrality scores over its lifetime.
    *   `sum_strength`: The sum of the individual's annual social strength scores (weighted ties).
    *   `sum_eigen`: The sum of the individual's annual eigenvector centrality scores.
    *   `mean_mat`: Average matrilineal rank or status during the individual's life.
    *   `mean_matSize`: Average size of the individual's matriline (number of related females) over its life.
    *   `mean_HRO`: Mean Home Range Overlap index.
    *   `mean_N` / `mean_E`: Mean spatial coordinates (Northings/Eastings) of the individual's home range.
    *   `matriline`: The specific matrilineal group name/ID the individual belonged to.
    *   `LRS`: Lifetime Reproductive Success (Total number of calves produced that survived to 1 year).
    *   `LBS`: Lifetime Breeding Success (Total number of calves born).
    *   `mean.grp.size`: Average size of the social groups the individual was observed in.
    *   `matSize`: Final or average size of the matriline.

### 2. annual_data.csv / scaled_annual.csv
*   **Description:** Longitudinal data for survival analysis.
*   **Row definition:** One row per individual per year (person-year format).
*   **Variables:**
    *   `id`: Unique identifier for the individual.
    *   `year`: The calendar year of observation.
    *   `degree`: Number of social associates in that year.
    *   `strength`: Sum of the weights of social ties in that year.
    *   `eigen`: Eigenvector centrality (measure of being connected to other well-connected individuals) in that year.
    *   `mat`: Matriline identifier.
    *   `start` / `end`: Time intervals used for survival modeling (e.g., age in years).
    *   `death`: Binary indicator of mortality (1 = died in this interval, 0 = survived).
    *   `DeathYear` / `BirthYear`: Calendar years of birth and death.
    *   `lastSeen`: The last calendar year the individual was observed alive.
    *   `matSize`: Number of individuals in the matriline in that year.
    *   `HRO2`: Home Range Overlap metric for that year.
    *   `LifetimeE` / `LifetimeN`: The overall lifetime average spatial coordinates (Eastings/Northings).
    *   `centroid`: Spatial centroid of the individual's sightings.
    *   `sex`: Biological sex (all "F" for females).

### 3. scaled_calves_survival.csv
*   **Description:** Data linking maternal social traits to the survival of specific offspring.
*   **Row definition:** One row per calf.
*   **Variables:**
    *   `ego`: Unique identifier for the calf.
    *   `ego.birth`: Calendar year the calf was born.
    *   `ego.mom`: Unique identifier for the calf's mother.
    *   `ego.survived.frist.year`: Binary (1 = calf survived to 1 year of age, 0 = died).
    *   `mom.degree`: The mother's degree centrality in the year of the calf's birth.
    *   `mom.strength`: The mother's social strength in the year of the calf's birth.
    *   `mom.eigen`: The mother's eigenvector centrality in the year of the calf's birth.
    *   `mom.obs`: Number of times the mother was observed/sampled in that year.
    *   `matSize`: Size of the matriline in the year of birth.
    *   `id`: Maternal ID (matches `ego.mom`).
    *   `HRO2`: Maternal Home Range Overlap index.
    *   `LifetimeE` / `LifetimeN` / `centroid`: Maternal spatial/geographic metrics.

### 4. MRQAP_data.RData
*   **Description:** R data object containing social networks corrected by SRI over the years of observations.
*   **Contents:** Adjacency matrices representing social associations (weights based on the Gambit-of-the-group) and matrices of attributes (e.g., kinship, spatial overlap) used as predictors.

---

## Methodological Notes

*   **Social Metrics:** All social network metrics (degree, strength, eigenvector) were calculated using the `{ANTs}` and `{asnipe}` R packages based on census observations.
*   **Spatial Data:** Northings and Eastings are based on the UK Ordnance Survey grid system (typically in meters).
*   **Missing Data:** [Mention how missing data is handled, e.g., "NA indicates years where the individual was not observed or the metric could not be calculated"].

---
## System and Software Requirements

The analysis was performed using **R** and **Quarto**.

### Software
*   **R** (version 4.2.0 or later recommended)
*   **RStudio IDE** (version 2022.07 or later recommended for best Quarto support)
*   **Quarto** (should be bundled with recent versions of RStudio)

### R Packages
The analysis requires the following R packages. All dependencies are listed in the `renv.lock` file.
- `{ANTs}`
- `{lme4}`
- `{lmerTest}`
- `{sjPlot}`
- `{ggplot2}`
- `{MASS}`
- `{asnipe}`
- `{survival}`
- `{survminer}`
- `{rptR}`
- `{PerformanceAnalytics}`
- `{gtsummary}`
- `{coxme}`

---

## How to Reproduce the Analysis

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/[your-username]/[your-repo-name].git
    cd [your-repo-name]
    ```

2.  **Open the qmd file  `red_deer_analysis.qmd`:**

3.  **Render the Quarto Document:**
    With the `red_deer_analysis.qmd` file open in RStudio, simply click the **"Render"** button at the top of the script editor.

    ![Render Button Screenshot](https://quarto.org/docs/get-started/hello/images/rstudio-render-button.png)

    This will execute all the code chunks within the `.qmd` file sequentially and generate an HTML file (`red_deer_analysis.html`) in the same directory. This single HTML file will contain all the analyses, tables, and figures, identical to the results reported in the paper.

---

## Data Availability

The data required to run the analysis are provided in this repository. These data are derived from the long-term study of red deer on the Isle of Rum, Scotland. If you intend to use this data for novel analyses beyond reproducing this paper, please ensure you properly cite the original data sources and adhere to any data use policies from the Isle of Rum Red Deer Project.

---
