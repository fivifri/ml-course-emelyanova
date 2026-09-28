# 🚢 Module 1 — Titanic: EDA + бинарная классификация

**Автор:** Емельянова Ксения, ПКТб-23-1  
**Учебный год:** 2026/2027  
**Дата:** 2026-29-09

## 📊 Результаты

| Модель | Accuracy | Precision | Recall | F1-score | ROC-AUC |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Logistic Regression** | `0.8045` | `0.7833` | `0.6812` | `0.7287` | `0.8486` |
| **Decision Tree** | `0.7821` | `0.7419` | `0.6667` | `0.7023` | `0.8132` |
| **Random Forest** | `0.8212` | `0.8491` | `0.6522` | `0.7377` | `0.8498` |
| **Gradient Boosting** | `0.8156` | `0.8333` | `0.6522` | `0.7317` | `0.8211` |

**Время обучения:** 0.0055 сек (LR), 0.0062 сек (DT), 0.2226 сек (RF), 0.2170 сек (GB)

## 🚀 Быстрый старт

```python
import joblib
import requests
from io import BytesIO

BASE_URL = "https://raw.githubusercontent.com/fivifri/ml-course-emelyanova/main/module-1-titanic"
model = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/lr_model.pkl").content))
```

## 📁 Структура
- `notebook.ipynb` — полный отчёт
- `models/` — модели и метаданные
- `data/` — датасет и описание
