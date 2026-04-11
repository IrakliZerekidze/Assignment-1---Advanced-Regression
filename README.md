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
| **Overfitting Gap** | -0.0156 |
#### Insights:
The negative Overfitting Gap (-0.0156) indicates a low variance model—it generalizes well to unseen data without memorizing noise. However, the Train R² (0.8072) confirms a high bias (underfitting) problem. By ignoring 43 categorical columns and using a rigid linear model, we are oversimplifying the housing market. Furthermore, the large gap between RMSE and MAE demonstrates that our simple mean imputation is highly sensitive to outliers, causing massive prediction errors on a few specific houses.

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
| **Overfitting Gap** | -0.0154 |

#### Insights:
Little to no changes in the metrics, changing the imputation had no important effect on the model.

### Experiment 3: Zero ImputationBaseline
- **Features Used:** 37 Numerical Columns
- **Preprocessing:** Zero Imputation & Standard Scaling
- **Model:** Linear Regression
#### Process:
Swapped mean/median imputation for a constant value of 0. This experiment tests the hypothesis that missing values (NaNs) in this dataset often represent the physical absence of a feature (e.g., no garage, no pool, or no basement) rather than a missing measurement.
#### Results:
| Metric | Training Set | Test Set |
| **R² Score** | 0.8094 | 0.8301 |
| **MAE** | $20,870.67 | $22,232.28 |
| **RMSE** | $33,715.73 | $36,102.10 |
| **RMSLE** | 0.3609 | 0.1757 |
| **Overfitting Gap**| -0.0207 |

#### Insights:
This strategy yielded our best results, proving that treating NaNs physically as zero fundamentally aligns with the data's reality. Interestingly, the Overfitting Gap dropped even further to -0.0207. This means our model's variance decreased even more, making its generalization to the test set exceptionally strong. Yet, despite breaking the 0.83 R² barrier, we are still bounded by high bias. The model has squeezed all the predictive power it can out of these 37 numerical columns and requires categorical feature diversity to break through this performance ceiling