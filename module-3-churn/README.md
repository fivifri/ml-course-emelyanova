# 📉 Module 3 — Customer Churn: Ансамблевые методы

## 📊 Результаты (тестовая выборка)

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|---|
| Random Forest | 0.76 | 0.535 | 0.743 | 0.622 | 0.839 |
| XGBoost | 0.771 | 0.553 | 0.706 | 0.62 | 0.83 |
| LightGBM | 0.759 | 0.533 | 0.751 | 0.624 | 0.838 |
| CatBoost | 0.749 | 0.519 | 0.743 | 0.611 | 0.841 |
| LightGBM (Optuna) | 0.744 | 0.511 | 0.799 | 0.624 | 0.85 |
| Stacking (RF+XGB+LGBM+Cat) | 0.75 | 0.519 | 0.802 | 0.63 | 0.849 |

## 🚀 Быстрый старт

```python
import joblib, requests
from io import BytesIO
BASE_URL = "https://raw.githubusercontent.com/<username>/ml-course-<фамилия>/main/module-3-churn"
model = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/best_model.pkl").content))
```

## 📁 Структура
- `notebook.ipynb` — полный отчёт
- `models/` — модели, scaler, кодировщики, метрики
- `data/` — датасет и описание
- `examples/` — графики EDA, SHAP, Feature Importance, ROC
