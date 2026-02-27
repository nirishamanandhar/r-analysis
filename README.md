# R Analysis for three datasets

## Overview

This R Notebook (`r-analysis.Rmd`) contains a statistical analysis across three datasets, covering descriptive statistics, logistic regression, multi-criteria decision analysis (TOPSIS) and spatial visualization.

## Datasets Required

| File | Description |
|---|---|
| `Test.xlsx` | Survey data with demographic and socioeconomic variables (age, sex, marital status, income, height, weight, locality class, etc.) |
| `Credit.xlsx` | Bank customer loan data with outcome variable (loan repayment) and predictors (employment, residence, education, age, gender) |
| `Data.xlsx` | Economic indicators for Polish provinces in 2021 (two sheets: `Data` and `Variables`) |
| `Wojewodztwa.shp` | Shapefile for Polish province boundaries (used for map visualization) |

## Dependencies

Install the following R packages before running the notebook:

```r
install.packages(c("readxl", "dplyr", "tidyr", "ggplot2", "ggpubr",
                   "ggthemes", "sf", "tmap", "topsis", "scales"))
```

## Analysis Structure

### Part 1 – Survey Data (`Test.xlsx`)

Exploratory analysis of a social survey dataset:

- Count of married respondents (`fc11`)
- Average age of married respondents
- Descriptive statistics (min, max, mean, SD, median) of income (`fp65`) for males
- Contingency table: locality class (`class`) vs. life priorities (`fp29`)
- Age recoding into two groups (≤35 and >35) with a cross-tabulation by sex
- Percentage breakdown of respondents by marital status
- Pearson correlation between height (`fp55`) and weight (`fp56`) for males in large cities
- Quartiles of height for female respondents

### Part 2 – Credit Risk (`Credit.xlsx`)

Binary logistic regression to model loan default:

- Response variable `y`: whether a customer paid off their loan (0 = Paid, 1 = Not Paid)
- Predictors: labour market status (`x1`), place of residence (`x2`), education (`x3`), age (`x4`), gender (`x5`)
- Model summary and coefficient extraction
- Predicted probabilities with a 0.5 classification threshold
- Confusion matrix to evaluate model performance

### Part 3 – Economic Development Analysis (`Data.xlsx`)

Multi-criteria analysis and visualisation of Polish provincial economic data (2021):

- **TOPSIS ranking**: scores each province across 12 economic indicators using equal weights, all treated as stimulants
- **Choropleth map**: spatial distribution of TOPSIS scores across provinces (requires `Wojewodztwa.shp`)
- **Histogram**: distribution of GDP per capita (`X1`)
- **Bar chart**: investment outlays per capita (`X5`) by province
- **Boxplot**: unemployment rate (`X8`) distribution
- **Descriptive statistics**: mean, median, SD, and quartiles for GDP per capita
- **Binary GDP variable**: classifies provinces above/below 50,000 PLN GDP per capita with a bar chart

## How to Run

1. Place all required data files (`Test.xlsx`, `Credit.xlsx`, `Data.xlsx`, `Wojewodztwa.shp` and associated shp file components) in the same directory as the `.Rmd` file.
2. Open the file in RStudio.
3. Install any missing packages (see Dependencies above).
4. Click **Run All** or knit to HTML via `Knit > Knit to HTML`.

## Output

The notebook produces an HTML report with inline results, tables and visualisations for each analysis section.