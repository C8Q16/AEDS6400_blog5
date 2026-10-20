# AEDS6400_blog5
# The Geography of Rent Burden in Philadelphia

**Computational Methods for Economists — Blog Post 5**

## Overview

This project examines the geographic distribution of housing affordability challenges across Philadelphia, Pennsylvania. Using Census Tract-level data, it investigates how the share of rent-burdened renter households varies across neighborhoods and how rent burden is associated with household income.

A household is considered **rent-burdened** if it spends at least 30% of its household income on gross rent.

The project addresses three main questions:

- How does rent burden vary geographically across Philadelphia?
- How does median household income vary across Census Tracts?
- What is the relationship between household income and rent burden?

## Data Sources

The analysis uses data from the **2020–2024 American Community Survey (ACS) five-year estimates**, published by the U.S. Census Bureau.

| Dataset | ACS Table | Description |
|---|---|---|
| Gross rent as a percentage of household income | B25070 | Used to calculate the rent-burden rate |
| Median household income | B19013 | Used to examine income differences across Census Tracts |
| Census Tract boundaries | U.S. Census Bureau | Used to construct geographic visualizations |

The data are retrieved programmatically in R using the `tidycensus` package.

**Geographic coverage:** Philadelphia County, Pennsylvania, at the Census Tract level.

## Repository Structure

The repository contains the following files:

```text
.
├── README.md
├── blog5.qmd
├── blog5.R
├── figure1.png
├── figure2.png
└── figure3.png
```

- **`blog5.qmd`** — Quarto document containing the written analysis and visualizations.
- **`blog5.R`** — R script for data retrieval, processing, statistical analysis, and visualization.
- **`figure1.png`** — Map of rent burden across Philadelphia Census Tracts.
- **`figure2.png`** — Map of median household income across Philadelphia Census Tracts.
- **`figure3.png`** — Scatter plot showing the relationship between median household income and rent burden.
- **`README.md`** — Project description and reproduction instructions.

## Requirements

To reproduce this project, you will need:

- R
- RStudio (recommended)
- Quarto
- A U.S. Census Bureau API key

The R script uses `tidycensus` to retrieve ACS data. You can request a free Census API key here:

https://api.census.gov/data/key_signup.html

Install the required R packages by running:

```r
install.packages(c(
  "tidycensus",
  "dplyr",
  "sf",
  "ggplot2",
  "scales",
  "readr",
  "tidyr"
))
```

## How to Reproduce the Analysis

### 1. Clone or download the repository

Clone the repository to your local machine:

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd <YOUR_REPOSITORY_NAME>
```

Alternatively, download the repository as a ZIP file from GitHub and extract it.

Replace the placeholders above with your actual GitHub repository URL and folder name.

### 2. Configure your Census API key

After obtaining an API key, configure it in R:

```r
tidycensus::census_api_key(
  "YOUR_CENSUS_API_KEY",
  install = TRUE
)
```

Replace `YOUR_CENSUS_API_KEY` with your actual key. This configuration is generally saved for future R sessions.

**Security note:** Do not commit your API key or other credentials to a public GitHub repository.

### 3. Run the R script

Open the project directory in RStudio and run:

```r
source("blog5.R")
```

The script retrieves the ACS data, processes the relevant variables, calculates rent-burden measures and correlations, and generates the visualizations.

If the script saves output files to an `output/` directory, check that directory for the generated results.

### 4. Render the Quarto blog post

Make sure Quarto is installed and available on your system. In the project directory, run:

```bash
quarto render blog5.qmd
```

This generates an HTML version of the blog post, typically named `blog5.html`, containing the written analysis and figures.

The three figure files should be available at the paths referenced in `blog5.qmd`. If they are stored in the project root, no additional path changes are needed.

## Key Findings

The analysis produces the following descriptive results:

- The aggregate rent-burden rate is approximately **52.3%** among renter households with computable rent-to-income ratios.
- The median Census Tract-level rent-burden rate is approximately **54.0%**.
- The Pearson correlation between median household income and rent burden is approximately **−0.546**.
- The Spearman rank correlation is approximately **−0.595**.

Together, these results indicate a moderate negative association between neighborhood-level household income and rent burden: higher-income Census Tracts generally tend to have lower rent-burden rates.

These findings describe an association and do not establish a causal relationship.

## Limitations

- ACS five-year estimates are subject to sampling uncertainty.
- Some Census Tracts have missing or unavailable estimates.
- Extremely high rent-burden estimates may be less reliable when based on small numbers of renter households.
- Census Tract-level relationships do not necessarily represent individual household experiences.
- The analysis is descriptive and does not identify the causal effects of income, rent prices, or neighborhood characteristics.

## Reproducibility Notes

Results may differ slightly if the Census Bureau updates its data or if package versions change. The analysis uses the 2020–2024 ACS five-year estimates, and the reported statistics are based on the data available when the project was conducted.

## Author

**Yixin Yang**

Computational Methods for Economists  
Blog Post 5: GIS Data Visualization
