## 📊 Baseline Model Performance

The table below summarizes the performance of various baseline models evaluated on the test set. Metrics include R², RMSE, MAE, RMSLE, and the overfitting gap (difference between train and test R²).

| Model | Train R² | Test R² | Train RMSE | Test RMSE | Train MAE | Test MAE | Train RMSLE | Test RMSLE | Overfitting Gap |
|------|---------|--------|-----------|----------|----------|---------|------------|-----------|----------------|
| Linear Regression | 0.9401 | 0.4433 | 18903.42 | 65344.90 | 12109.42 | 21108.74 | 0.1023 | 0.7236 | 0.4968 |
| Ridge Regression | 0.9369 | 0.8958 | 19393.89 | 28265.25 | 12538.98 | 18201.72 | 0.1046 | 0.1653 | 0.0411 |
| Lasso Regression | 0.XXXX | 0.XXXX | XXXXX.XX | XXXXX.XX | XXXXX.XX | XXXXX.XX | 0.XXXX | 0.XXXX | 0.XXXX |
| Elastic Net | 0.XXXX | 0.XXXX | XXXXX.XX | XXXXX.XX | XXXXX.XX | XXXXX.XX | 0.XXXX | 0.XXXX | 0.XXXX |
| Decision Tree | 0.XXXX | 0.XXXX | XXXXX.XX | XXXXX.XX | XXXXX.XX | XXXXX.XX | 0.XXXX | 0.XXXX | 0.XXXX |
| Random Forest | 0.XXXX | 0.XXXX | XXXXX.XX | XXXXX.XX | XXXXX.XX | XXXXX.XX | 0.XXXX | 0.XXXX | 0.XXXX |
| XGBoost | 0.9943 | 0.8978 | 5840.53 | 27995.43 | 4272.81 | 17610.82 | 0.0415 | 0.1484 | 0.0965 |
