# Food-Insecurity-Prediction

## Project Overview
This project develops machine learning models to predict IPC (Integrated Food Security Phase Classification) severity levels (1–5) using multi-dimensional data, including socio-economic indicators, conflict data, agricultural metrics, and climate factors.


# Technical Stack

## Data Processing
- pandas >= 1.5.0
- numpy >= 1.24.0

## Machine Learning
- scikit-learn >= 1.3.0
- tensorflow >= 2.13.0 #

## Visualization
- matplotlib >= 3.6.0
- seaborn >= 0.12.0

# Dataset

## Overview
This project utilizes a **unique, multi-source real-world dataset** on food insecurity, combining several authoritative international datasets to build a comprehensive predictive model of food insecurity severity.

## Data Sources

| Source | Provider | Variables |
|--------|----------|-----------|
| **IPC (Integrated Food Security Phase Classification)** | Humanitarian Data Exchange (HDX) | Target variable (IPC Phases 1–5) |
| **World Bank Development Indicators** | World Bank | Socio-economic variables (population, GDP, poverty rates) |
| **FAOSTAT** | Food and Agriculture Organization of the UN | Agricultural production (maize, rice, wheat, sorghum, millet yields & production), climate indicators (temperature change, variability) |
| **UCDP** | Uppsala Conflict Data Program | Conflict-related fatalities (battle-related deaths, one-sided violence against civilians) |

## Dataset Characteristics

- Temporal Coverage: 20+ years (2003–2024)
- Geographic Scope: Multiple countries, focusing on food-insecure regions with IPC assessments
- Dataset Size: 927–1,200 country-year observations
- Features: Dozens of explanatory variables per observation
- Adequacy: Dataset size is sufficient for robust machine learning experimentation

## Data Integration
The dataset represents a careful integration of multiple authoritative sources, providing a comprehensive view of factors contributing to food insecurity across different dimensions:
- Food Security Assessment** (IPC classifications)
- Economic Indicators** (World Bank metrics)
- Agricultural Production** (FAO statistics)
- Conflict Data** (UCDP records)


## Data Dictionary: Final IPC-All Clean Dataset

This document describes the variables included in the cleaned dataset used for food insecurity prediction.

| Column | Description |
|--------|-------------|
| `iso3` | Country 3-letter ISO code |
| `country` | Country name |
| `year` | Year of observation |
| `phase_type` | IPC analysis type: current, proj1 (first projection), proj2 (second projection) |
| `ipc_phase` | IPC Phase classification (1=Minimal, 2=Stressed, 3=Crisis, 4=Emergency, 5=Famine) |
| `population_total` | Total population (World Bank, SP.POP.TOTL) |
| `gdp_current_usd` | Gross Domestic Product in current US dollars (World Bank, NY.GDP.MKTP.CD) |
| `poverty_rate` | Poverty headcount ratio at $2.15/day (% of population, World Bank, SI.POV.DDAY) |
| `brd_deaths` | Battle-related deaths (UCDP Battle-related deaths dataset) |
| `one_sided_deaths` | One-sided violence deaths (UCDP One-sided violence dataset) |
| `Crop: Maize (corn) - Production` | Maize (corn) total production (tonnes) |
| `Crop: Maize (corn) - Yield` | Maize (corn) yield (hg/ha) |
| `Crop: Rice - Production` | Rice total production (tonnes) |
| `Crop: Rice - Yield` | Rice yield (hg/ha) |
| `Crop: Wheat - Production` | Wheat total production (tonnes) |
| `Crop: Wheat - Yield` | Wheat yield (hg/ha) |
| `Crop: Millet - Production` | Millet total production (tonnes) |
| `Crop: Millet - Yield` | Millet yield (hg/ha) |
| `Crop: Sorghum - Production` | Sorghum total production (tonnes) |
| `Crop: Sorghum - Yield` | Sorghum yield (hg/ha) |
| `Climate: Standard Deviation` | Climate indicator: Standard Deviation |
| `Climate: Temperature change` | Climate indicator: Temperature change |


## Target Variable

ipc_phase: Severity classification (1-5)

- 1: Minimal food insecurity
- 2: Stressed
- 3: Crisis (acute food insecurity)
- 4: Emergency (humanitarian emergency)
- 5: Famine (humanitarian catastrophe)


## Key Identifiers

- iso3: Country ISO3 code
- country: Country name
- year: Assessment year
- phase_type: Assessment type/period


## Team Members & Section Assignments

| Section                        | Team Members                | Key Responsibilities                                   |
|--------------------------------|-----------------------------|-------------------------------------------------------|
| 1. Data Description & Sources  | Elizabeth, Mable, Immaculate | Dataset overview, feature documentation, data dictionary |
| 2. Data Cleaning & Missing Values | Conrad, Denis             | Data preprocessing, missingness handling, clean dataset creation |
| 3. Exploratory Data Analysis   | Mable, Nicholas             | Univariate/multivariate analysis, visualization, patterns |
| 4. Classical ML Models         | Charles, Nicholas           | Traditional ML implementation, baseline models, evaluation |
| 5. Neural Network Models       | Conrad, Immaculate          | Deep learning implementation, advanced modeling        |
| 6. Findings & Conclusions      | Charles, Denis, Conrad      | Results synthesis, presentation, final documentation   |


# Project Workflow

## Section 1: Data Description & Sources (Elizabeth, Mable, Immaculate)
Objectives:

 -Brief the target: ipc_phase (1–5) classification
 -Identify the key identifiers: iso3, country, year, phase_type
 -Describe feature categories: socio-economic, conflict, agriculture, climate
 -Create comprehensive data dictionary with feature definitions
 -Document data sources and collection methodology


 # Data Cleaning & Missing Values (Conrad, Denis)
Cleaning Steps:

 -Inspect missingness - Calculate percentage missing per column
 -Drop high-missingness columns - Remove columns with >70% missing values
 
Imputation strategy:

- Numeric features: Median imputation
- Conflict deaths: Fill NaN with 0 (assume no reported fatalities)


 - Optional time-series imputation: Per-country forward-fill for GDP/population
 - Save cleaned dataset - Export df_model.csv for modeling & EDA

# Exploratory Data Analysis (Mable, Nicholas)

## Univariate Analysis:

 -Target distribution: Bar chart of ipc_phase frequencies
 -Feature distributions: Histograms of GDP, poverty, population, climate indicators
 -Summary statistics: Central tendency and spread measures
 -Outlier detection: Identify extreme values per feature

## Multivariate Analysis:

 -Correlation matrix: Numeric feature relationships heatmap
 -Target relationships: Scatter plots of GDP vs ipc_phase, Poverty vs ipc_phase
 -Conflict analysis: Conflict deaths vs ipc_phase visualization
 -Feature comparisons: Boxplots of ipc_phase vs key numeric features
 -Geographic patterns: Country-level analysis and mapping

# Classical ML Models (Charles, Nicholas)
## Model Development:

 -Data preparation: Stratified train/test split by ipc_phase
 
 Baseline models:

-Logistic Regression (multiclass)
-Random Forest Classifier
-SVM


-Feature engineering: Create relevant derived features

 Model evaluation:

-Primary metrics: Accuracy, Macro-F1 score
-Secondary metrics: Precision, Recall per class
-Confusion matrices: Detailed classification analysis

# Neural Network Models (Conrad, Immaculate)

Deep Learning Implementation:

 - Architecture design: Simple MLP (Multi-Layer Perceptron) classifier
 - Output layer: Softmax activation for multiclass classification
 - Model training: Optimization and regularization techniques
 - Performance evaluation: Compare against classical models using Macro-F1
 - Model interpretation: Feature importance and prediction analysis


# Findings & Conclusions (Charles, Denis, Conrad)

Analysis Questions:

 -Feature importance: Which features mattered most for predictions?
 -Model comparison: Which model performed best and why?
 -Risk assessment: IPC coverage limitations, data missingness, potential bias
 -Practical implications: Real-world application feasibility
 -Future improvements: Next steps and recommendations


## How to run the project

- Click on this Google Colab link: [https://colab.research.google.com/drive/1I0MBIFvNsYu-vMGSQAsUVIOn2ZNOGyqI]
- Sign in to your Google account if prompted
- If the dataset isn't automatically loaded, upload the CSV file:
- Click on the folder icon in the left sidebar
- Click "Upload" and select your CSV dataset file
- Click "Runtime" → "Run all" to execute all cells
Or run cells individually by clicking the play button on each cell


## Authored By Immaculate,Conrad,Mable,Nicholas,Denis,Elizabeth,Charles
