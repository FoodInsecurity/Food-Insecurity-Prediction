# Food-Insecurity-Prediction
Predicting acute food insecurity and humanitarian crises using machine learning models trained on IPC (Integrated Food Security Phase Classification) data

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
