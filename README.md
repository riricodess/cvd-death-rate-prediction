# cvd-death-rate-prediction
ML pipeline for predicting US county-level cardiovascular disease death rates (2010–2020) using CDC data — includes EDA and comparison of 4 regression models (Random Forest achieves R² = 0.993).

# Cardiovascular Disease Death Rate Prediction

Exploratory data analysis and machine learning models to predict county-level cardiovascular disease (CVD) death rates in the US, using CDC data from 2010–2020.

## Dataset

**Source:** CDC — *Cardiovascular Disease Death Rates, Trends, and Excess Death Rates Among US Adults (35+), by County and Age Group, 2010–2020*

Each row represents a US county, year, and age group, with the age-standardized CVD death rate (per 100,000 people) along with confidence intervals and geographic coordinates.

## Contents

| File | Description |
|---|---|
| `Cardiovascular_Disease_Death_Rates.csv` | Raw dataset |
| `EDA.ipynb` | Exploratory data analysis — distribution, trends over time, age-group comparisons, outlier detection |
| `CVD_Death_Rate_ML_Models.ipynb` | Feature engineering, model training, and evaluation |

## Approach

1. **Data cleaning** — filtered to the *Age-Standardized, Spatially Smoothed Rate* category and dropped missing target values.
2. **EDA** — examined distribution (positively skewed, bimodal), yearly trend (2010–2020), and age-group differences (35–64 vs. 65+).
3. **Feature engineering** — `Year`, encoded `State`, encoded `Age Group`, and geographic coordinates (`X_long`, `Y_lat`).
4. **Modeling** — trained and compared 4 regression models:
   - Linear Regression
   - Random Forest
   - Gradient Boosting
   - Support Vector Regression (RBF kernel)
5. **Evaluation** — compared models using MAE, RMSE, and R².

## Results

| Rank | Model | MAE | RMSE | R² |
|---|---|---|---|---|
| 1 | Random Forest | 34.44 | 63.55 | **0.993** |
| 2 | Gradient Boosting | 79.19 | 127.57 | 0.971 |
| 3 | SVR (RBF) | 99.67 | 162.41 | 0.953 |
| 4 | Linear Regression | 125.00 | 191.91 | 0.935 |

**Random Forest** performed best, capturing the non-linear variation in CVD death rates across states, age groups, and time far better than a linear model.

## Tech Stack

- Python
- pandas, numpy
- scikit-learn
- matplotlib

## How to Run

```bash
git clone https://github.com/riricodess/cvd-death-rate-prediction.git
cd cvd-death-rate-prediction
pip install pandas numpy scikit-learn matplotlib jupyter
jupyter notebook
```

Run `EDA.ipynb` first, then `CVD_Death_Rate_ML_Models.ipynb`.

## Author

Sriya Raj
