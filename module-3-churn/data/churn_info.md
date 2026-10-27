# Telco Customer Churn — описание датасета

**Источник:** https://www.kaggle.com/datasets/blastchar/telco-customer-churn

- Всего примеров: 7043
- Столбцов: 21 (customerID + 19 признаков + целевая `Churn`)
- Числовые признаки: tenure, MonthlyCharges, TotalCharges (+ SeniorCitizen как 0/1)
- Остальные признаки — категориальные

## Распределение классов
- No (остался): 5174 (73.5%)
- Yes (ушёл): 1869 (26.5%)

## Группы признаков
- Демографические: gender, SeniorCitizen, Partner, Dependents
- Услуги: PhoneService, MultipleLines, InternetService, OnlineSecurity, OnlineBackup,
  DeviceProtection, TechSupport, StreamingTV, StreamingMovies
- Аккаунт: Contract, PaperlessBilling, PaymentMethod, MonthlyCharges, TotalCharges, tenure
