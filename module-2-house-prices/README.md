# 🏠 Module 2 — House Prices: предобработка и регрессия

**Автор:** Емельянова К.П., ПКТб-23-1  
**Дата:** 2026-06-10

## 📊 Результаты

| Модель | RMSE (log) | MAE (log) | R² | RMSE (USD) |
|---|---:|---:|---:|---:|
| Gradient Boosting | 0.1249 | 0.0816 | 0.9012 | 20,019.98 |
| Lasso | 0.1258 | 0.0860 | 0.8998 | 20,373.85 |
| ElasticNet | 0.1259 | 0.0860 | 0.8996 | 20,379.96 |
| Ridge | 0.1294 | 0.0896 | 0.8940 | 21,250.03 |
| Linear Regression | 0.1297 | 0.0896 | 0.8935 | 21,351.68 |
| Random Forest | 0.1457 | 0.0981 | 0.8656 | 24,416.12 |

**Лучшая модель:** Gradient Boosting  
**R²:** 0.9012  
**RMSE:** 20,019.98 USD

**Время обучения:**
- Linear Regression — 0.151 сек
- Ridge — 0.008 сек
- Lasso — 0.197 сек
- ElasticNet — 0.094 сек
- Random Forest — 2.057 сек
- Gradient Boosting — 10.237 сек

## 🚀 Быстрый старт

```python
import joblib
import requests
from io import BytesIO

BASE_URL = "https://raw.githubusercontent.com/fivifri/ml-course-emelyanova/main/module-2-house-prices"

# Лучшая модель
model = joblib.load(
    BytesIO(
        requests.get(
            f"{BASE_URL}/models/gradient_boosting_model.pkl"
        ).content
    )
)

# Scaler необходим для линейных моделей
scaler = joblib.load(
    BytesIO(
        requests.get(
            f"{BASE_URL}/models/scaler.pkl"
        ).content
    )
)
