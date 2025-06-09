# Reproducibility for: "Associations between lifetime fitness and social bonds in female red deer"

This repository contains the data and Quarto document necessary to reproduce the analyses and figures for the paper investigating the link between sociality, fitness, and survival in female red deer (*Cervus elaphus*).

**Author:** Sebastian Sosa

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
