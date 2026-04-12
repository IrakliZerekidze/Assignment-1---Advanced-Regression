## 📊 Baseline Model Performance

The table below summarizes the performance of various baseline models evaluated on the test set. Metrics include R², RMSE, MAE, RMSLE, and the overfitting gap (difference between train and test R²).

| Model | Train R² | Test R² | Train RMSE | Test RMSE | Train MAE | Test MAE | Train RMSLE | Test RMSLE | Overfitting Gap |
|------|---------|--------|-----------|----------|----------|---------|------------|-----------|----------------|
| Linear Regression | 0.9401 | 0.4433 | 18903.42 | 65344.90 | 12109.42 | 21108.74 | 0.1023 | 0.7236 | 0.4968 |
| Linear Regression (log target) | 0.9492 | 0.9328 | 17400.36 | 22701.53 | 11004.25 | 15063.08 | 0.0917 | 0.1308 | 0.0164 |
| Ridge Regression | 0.9369 | 0.8958 | 19393.89 | 28265.25 | 12538.98 | 18201.72 | 0.1046 | 0.1653 | 0.0411 |
| Lasso Regression | 0.9339 | 0.8990 | 19856.75 | 27829.36 | 12731.28 | 17067.50 | 0.1056 | 0.1488 | 0.0348 |
| Decision Tree | 0.8402 | 0.7605 | 30877.19 | 42857.32 | 21913.60 | 28341.01 | 0.1722 | 0.2110 | 0.0796 |
| Random Forest | 0.9696 | 0.8943 | 13475.76 | 28471.05 | 7247.05 | 17088.90 | 0.0697 | 0.1516 | 0.0752 |
| XGBoost | 0.9861 | 0.9226 | 9098.03 | 24366.17 | 6755.96 | 15316.08 | 0.0605 | 0.1292 | 0.0635 |
