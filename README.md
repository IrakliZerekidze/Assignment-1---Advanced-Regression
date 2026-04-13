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

### ✅ Insights

The results show that both linear and tree-based models can perform well on this dataset when properly configured. Linear Regression benefits greatly from a log transformation of the target variable, achieving the highest Test R² and lowest error among all models.

Among tree-based approaches, XGBoost outperformed Random Forest and Decision Tree by effectively balancing bias and variance through boosting and regularization techniques.

Overall, the best performance was achieved by combining appropriate preprocessing (such as log transformation) with well-tuned models, highlighting the importance of both data transformation and model selection.

## მონაცემთა გაწმენდა და დამუშავება (Cleaning & Preprocessing)
### 1. უსარგებლო სვეტების მოცილება
- წავაშალე 'Id' სვეტი, რადგან არანაირ ინფორმაციას არ ატარებს და მხოლოდ იდენფიტიკატორია

### 2. გამოტოვებული მნიშვნელობების (NA) მქონე სვეტების დადროპვ
- სვეტებს რომლებსაც 80%-ზე მეტი NA მნიშვნელობა ჰქონდათ ამოვშალეთ
- ასეთი სეტვები იყო: 'Alley', 'PoolQC', 'Fence', 'MiscFeature`. ასეთი სეტვები არასაკმარის ინფორმაციას იძლევიან
  და მათი შევსება მეტ noise-ს იწვევს. ვცადე სხვა ზღვრებიც, უფრო გავზარდე 93, 97 % მდე რაც ამცირებდა წაშლილი
  სვეტების რაოდენობას თუმცა შედეგი დიდად არ შეცვლილა, ოდნავ გაუარესდა კიდეც. ვცადე ზღვრის დაბლა დაწევაც,
  60-50% მდე, ამან შედეგის გაუმჯობესება გამოწვია, თუმცა ჩავთვალე რომ 50% ზედმეტად აგრესიული და დაბალი იქნებოდა.
  <img width="1115" height="465" alt="image" src="https://github.com/user-attachments/assets/73f9c0a0-6102-455d-9d9e-daf70d287de3" />


### 3. NA მნიშვნელობების შევსების სტრატეგია
#### რიცხვითი მნიშვნელობები
- რიცხვითი მნიშვნელობის მქონე სეტვებში, გამოტოვებული ინფორმაცია მედიანებით შევავსე.
#### კატეგორიული მნიშვნელობები
- შევავსეთ მოდით. ვინაიდან ეს ტექსტური მონაცემია, ყველაზე ლოგიკურია, გამოტოვებული ადგილი შევავსოთ იმ მნიშვნელობით,
  რომელიც ყველაზე ხშირად გვხვდება მონაცემთა ბაზაში..

### 4. მაღალი დომინანტურობის სვეტების წაშლა
- ზღვრად ავიღე 95%, ის სვეტები რომლებშიც რომელიმე მნიშვნელობა 95% მეტს იკავებდა წავშალე, რადგან სვეტი არაინფორმატიული
  იქნებოდა, ვცადე სხვა მნიშვნელობებიც (90, 97, 99) თუმცა ოპტიმალური 95 აღმოჩნდა.
  
  <img width="1109" height="469" alt="image" src="https://github.com/user-attachments/assets/98912a39-5bed-47af-81d6-3a4aef33ad1f" />

## მოდელები
### Linear Regression
| Experiment | Train R² | Test R² | Train RMSE | Test RMSE | Train MAE | Test MAE | Train RMSLE | Test RMSLE | Overfitting Gap |
|------|---------|--------|-----------|----------|----------|---------|------------|-----------|----------------|
| Baseline | 0.8995 | 0.8640 | 24482.56 | 32293.27 | 15425.41 | 21043.45 | 0.1247 | 0.1677 | 0.0355 |
| Baseline (log target) | 0.9080 | 0.9079 | 23424.36 | 26577.14 | 13768.38 | 17413.99 | 0.1100 | 0.1326 | 0.0001 |
| Lasso Regression Baseline | 0.8653 | 0.9121 | 28340.52 | 25966.95 | 14835.74 | 16364.30 | 0.1209 | 0.1309 | -0.0468 |

### Decision Tree
| Experiment | Train R² | Test R² | Train RMSE | Test RMSE | Train MAE | Test MAE | Train RMSLE | Test RMSLE | Overfitting Gap |
|------|---------|--------|-----------|----------|----------|---------|------------|-----------|----------------|
| Baseline | 0.8402 | 0.7624 | 30877.19 | 42691.47 | 21913.60 | 28177.85 | 0.1722 | 0.2104 | 0.0778 |

### Random Forest
| Experiment | Train R² | Test R² | Train RMSE | Test RMSE | Train MAE | Test MAE | Train RMSLE | Test RMSLE | Overfitting Gap |
|------|---------|--------|-----------|----------|----------|---------|------------|-----------|----------------|

