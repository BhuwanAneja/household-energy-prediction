# Household Energy Prediction: Ridge and Lasso Regression

Predicting annual household electricity use (kWh) from house size, occupants, insulation, solar, heat pumps and other features, and comparing model-selection methods.

## Data
1,800 households with 14 predictors. Train/test split: 1,350 / 450.

## Methods
- Log-transformed the right-skewed response (annual kWh)
- Checked multicollinearity between size variables (floor area, bedrooms, heated area)
- **Feature engineering:** home age squared, heated area without a heat pump, floor area × occupants, log income
- Compared four approaches:
  - stepwise selection by AIC
  - best-subset selection with 10-fold cross-validation
  - **ridge regression**
  - **lasso regression** (glmnet, λ chosen by cross-validation)

## Results
| Model | Test RMSE (log scale) | Test RMSE (kWh) |
| --- | --- | --- |
| Best subset (10-fold CV) | 0.193 | 755 |
| Ridge | 0.189 | 742 |
| Lasso | 0.188 | 741 |

- **Lasso performed best** and still shows which predictors matter.
- The engineered features reduced lasso's cross-validated error by about **6%**.

## Tools
R, tidyverse, glmnet, leaps, MASS

## Files
- `analysis.Rmd` – code
- `report.html` – full report (download and open in a browser)

> Note: the random seed was changed for this public version, so re-running the code may give slightly different numbers.
