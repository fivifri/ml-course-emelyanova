# 📉 Module 3 — Customer Churn: Ансамблевые методы

**Автор:** Емельянова Ксения Павловна, ПКТб-23-1
**Дисциплина:** Машинное обучение и ИИ
**Дата:** 2026-10-27
**Датасет:** [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) — 7043 клиента, 19 признаков, отток 26.5 %

## 🎯 Задача

Бинарная классификация: предсказать, уйдёт ли клиент телеком-оператора (`Churn`). Обучены и сравнены 4 ансамблевые модели (Random Forest, XGBoost, LightGBM, CatBoost), лучшая оптимизирована через Optuna и интерпретирована через SHAP. Дополнительно (бонус) проверен Stacking.

## 📊 Результаты (тестовая выборка: 1409 клиентов, 374 ушедших)

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC | Время обучения |
|--------|----------|-----------|--------|-----|---------|----------------|
| Random Forest | 0.760 | 0.535 | 0.743 | 0.622 | 0.839 | 0.65 сек |
| XGBoost | 0.771 | 0.554 | 0.706 | 0.620 | 0.830 | 0.30 сек |
| LightGBM | 0.759 | 0.533 | 0.751 | 0.624 | 0.838 | 0.17 сек |
| CatBoost | 0.749 | 0.519 | 0.743 | 0.611 | 0.841 | 0.93 сек |
| **LightGBM (Optuna)** ⭐ | 0.744 | 0.511 | 0.800 | 0.624 | **0.850** | — |
| Stacking (RF+XGB+LGBM+Cat) | 0.750 | 0.519 | 0.802 | 0.630 | 0.849 | 10.3 сек |

**Финальная модель — LightGBM + Optuna** (30 испытаний, 5-fold CV): CV ROC-AUC = 0.8496, test ROC-AUC = 0.8503 (+0.0126 к baseline LightGBM).

Лучшие параметры: `n_estimators=350`, `max_depth=3`, `learning_rate≈0.023`, `min_child_samples=35`, `colsample_bytree≈0.52`, `subsample≈0.62`, `reg_lambda≈7.3`, `reg_alpha≈0.003`.

## 🔍 Ключевые выводы

- Разброс ROC-AUC между 4 базовыми моделями (0.830–0.841) сопоставим с шумом одной hold-out-выборки: модели качественно эквивалентны. Прирост даёт тюнинг (+0.013), а не смена алгоритма.
- Stacking даёт лучший F1 (0.630), но по AUC не превосходит Optuna-модель и обучается ≈ в 60 раз дольше.
- **Главный фактор оттока — тип контракта** (SHAP: 0.72, в 2.6 раза больше следующего признака). Отток: month-to-month 42.7 %, годовой 11.3 %, двухлетний 2.8 %.
- Другие факторы риска: отсутствие `OnlineSecurity` и `TechSupport`, малый стаж (новые клиенты ≤ 6 мес. — 52.9 % оттока), Fiber optic (41.9 %), оплата электронным чеком (45.3 %).
- Встроенная важность LightGBM (по числу разбиений) занижает `Contract`; SHAP надёжнее.
- Баланс классов: из-за весов классов Precision ≈ 0.51 при Recall ≈ 0.80; вероятности смещены и требуют калибровки, порог 0.5 стоит подобрать под бизнес-цель.

## 🚀 Быстрый старт

```python
import joblib, requests, json
from io import BytesIO

BASE_URL = "https://raw.githubusercontent.com/fivifri/ml-course-emelyanova/main/module-3-churn"

model = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/best_model.pkl").content))
feature_cols = requests.get(f"{BASE_URL}/models/feature_cols.json").json()

# X — DataFrame с 23 признаками в том же порядке (категории закодированы label_encoders.pkl)
# proba = model.predict_proba(X[feature_cols])[:, 1]
```

## 📁 Структура модуля

```
module-3-churn/
├── README.md
├── notebook.ipynb          ← полный отчёт (14 разделов)
├── requirements.txt
├── data/
│   ├── telco_churn.csv
│   └── churn_info.md       ← описание датасета
├── models/
│   ├── best_model.pkl      ← LightGBM + Optuna
│   ├── rf_model.pkl, xgb_model.pkl, lgbm_model.pkl, cat_model.pkl
│   ├── scaler.pkl, label_encoders.pkl
│   ├── feature_cols.json
│   └── metrics.json
└── examples/
    ├── eda_plots.png, roc_curves.png, feature_importance.png
    └── shap_summary.png, shap_waterfall.png
```

## ⚙️ Воспроизведение

```bash
pip install -r requirements.txt
jupyter notebook notebook.ipynb   # Run All
```
Все пути относительные; `random_state=42` везде, результаты воспроизводимы.
