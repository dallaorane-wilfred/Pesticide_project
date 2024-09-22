# Pesticide Project

## Authors
- Sofian, Baptiste, Wilfred, Souleiman

## Date
- March 6, 2024

## Project Overview
This project aims to predict the quantities of active substances (pesticides) purchased in France, based on various attributes such as classification, foreign purchases, Acceptable Daily Intake (ADI), and climate data (minimum temperatures). The analysis uses econometric modeling to understand the relationship between these factors and the amounts of active substances used.

### Objectives
- Estimate the quantity of active substances purchased based on their attributes and climatological data.
- Use regression models to identify key drivers, including temperature and ADI, that influence pesticide purchases.


### Intuitions:
- **Temperature-Related Parameters:** Higher minimum temperatures reduce frost and increase the need for phytosanitary products.
- **Toxicity-Related Parameters:** A higher ADI allows for more ingestion without harmful effects, leading to more purchases.

## Data
The project uses data on pesticide purchases and climate information. Data sources include:
- **Agricultural Product Purchases in France (2021)**: Summarized in the `BNVD_TRACABILITE_20221018_ACHAT_DPT_SUBSTANCE_2021.csv` file.
- **Climate Data**: Minimum temperature data from October to December 2021, and the entire year.
- **Acceptable Daily Intake (ADI)**: Toxicity information from the `adi.xlsx` file.

### Data Sources
The dataset contains:
- **108,822 observations** of agricultural product purchases.
- Climate data for **2021** across different departments in France.
- Toxicity information (ADI) for active substances.

### Data Files:
- `data/BNVD_TRACABILITE_20221018_ACHAT_DPT_SUBSTANCE_2021.csv`
- `data/meteo.csv`
- `data/adi.xlsx`
- `data/SAU.xlsx`

### Data Processing:
1. Transform categorical variables (classification, foreign purchase, etc.) into numeric format.
2. Extract minimum temperatures for October-December and the entire year.
3. Merge ADI data with substance data to include toxicity in the analysis.

## Model Description
The project uses Ordinary Least Squares (OLS) regression models to predict the log of the quantity of substances purchased. Key explanatory variables include:
- **ADI (dose journalière admissible)**
- **Minimum temperature** (both annual and for the months of October to December)

### Variables:
- **DJA (ADI)**: The amount of a substance that can be ingested daily without harm.
- **Minimum temperature**: The average minimum temperature by department, taken from 2021 data.

## Statistical Analysis
We use several models to test the relationship between the explanatory variables and the log of the quantity of substances purchased:
- Model 1: Uses October-December temperature data.
- Model 2: Uses annual temperature data.

### Key Results:
- The R² of the model using October-December temperature is **12.4%**, while the model using annual temperature has an R² of **7.8%**.
- The relationship between temperature and pesticide purchase quantities shows that higher temperatures increase purchases up to a certain threshold, after which the effect diminishes.

## Hypothesis Testing
Several tests are conducted to verify the models:
- **Shapiro Test** for normality of residuals.
- **Breusch-Pagan Test** for homoscedasticity.
- **Correlation Tests** between residuals and independent variables to check for multicollinearity.

## Project Folder Structure

```plaintext
Pesticide_project/
│
├── data/
│   ├── BNVD_TRACABILITE_20221018_ACHAT_DPT_SUBSTANCE_2021.csv
│   ├── meteo.csv
│   ├── adi.xlsx
│   └── SAU.xlsx
│
├── Pesticide_project.Rmd    # RMarkdown file for analysis
├── Pesticide_project.html   # HTML output from RMarkdown
└── README.md                # This README file
