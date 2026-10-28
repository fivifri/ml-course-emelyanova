# 🛒 Module 4 — Online Shoppers: Инженерия признаков

**Автор:** [ФИО], [группа]
**Дата:** 2026-10-28

## 📊 Результаты (тестовая выборка)

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC | Время, сек |
|---|---|---|---|---|---|---|
| Random Forest | 0.867 | 0.549 | 0.801 | 0.652 | 0.927 | 0.80 |
| XGBoost | 0.881 | 0.597 | 0.717 | 0.652 | 0.922 | 0.59 |
| LightGBM | 0.875 | 0.570 | 0.775 | 0.657 | 0.928 | 0.23 |
| CatBoost | 0.870 | 0.556 | 0.793 | 0.654 | 0.928 | 1.31 |
| **LightGBM (Optuna)** | **0.868** | **0.548** | **0.830** | **0.660** | **0.933** | — |

Лучший базовый ансамбль по ROC-AUC: **LightGBM**. Настроенная модель — LightGBM (Optuna, 30 trials).

## 🚀 Быстрый старт

```python
import joblib, requests, json
from io import BytesIO

BASE_URL = 'https://raw.githubusercontent.com/<username>/<repo>/main/module-4-features'
model = joblib.load(BytesIO(requests.get(f'{BASE_URL}/models/best_model.pkl').content))
features = requests.get(f'{BASE_URL}/models/feature_cols.json').json()
```

## 📁 Структура

- `notebook.ipynb` — полный отчёт (14 разделов)
- `models/` — модели `.pkl`, `scaler.pkl`, `feature_cols.json`, `metrics.json`, `model_metadata.json`
- `data/` — датасет и `dataset_info.md`
- `examples/` — графики (EDA, ROC, важность признаков, SHAP)
- `requirements.txt` — зависимости
