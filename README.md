**PROJECT TITLE**
**REPOSITORY STRUCTURE**

## PHASE 1: Baseline (Numerical Only)
We have established a baseline using only numerical features and a simple Linear Regression model to understand the "floor" of our performance.

### Experiment 1: Mean Imputation Baseline
- **Features Used:** 37 Numerical Columns
- **Preprocessing:** Mean Imputation & Standard Scaling
- **Model:** Linear Regression

#### Process:
We chose only the numerical columns, and filled Na values with mean values. We used Linear Regression Model and R², MAE, RMSE and RMSLE merics.

#### Results:
| Metric | Training Set | Test Set |
| **R² Score** | 0.8072 | 0.8227 |
| **MAE** | $21,082.24 | $23,003.78 |
| **RMSE** | $33,912.62 | $36,873.24 |
| **RMSLE** | 0.3755 | 0.1895 |

#### Insights:
Test r2 is larger than train r2, this imposes that we are not overfitting, but we are underfitting for sure, out of 80 columns we used 37 and ignored the other 43 and we used simple linear regression model. Our RMSE is significantly higher than MAE, this confirms the model is making larger errors on specific houses. RMSLE shows that the model is relatively stable accross different price brackets.

### Experiment 2: Median Imputation Baseline
- **Features Used:** 37 Numerical Columns
- **Preprocessing:** Median Imputation & Standard Scaling
- **Model:** Linear Regression

#### Process:
Literally same experiment just a different imputation, used median instead of mean values.

#### Results:
| Metric | Training Set | Test Set |
| **R² Score** | 0.8072 | 0.8226 |
| **MAE** | $21,073.86 | $23,001.73 |
| **RMSE** | $33,905.23 | $36,873.24 |
| **RMSLE** | 0.3740 | 0.1892 |

#### Insights:
Little to no changes in the metrics, changing the imputation had no important effect on the model.