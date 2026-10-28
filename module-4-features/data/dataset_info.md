# Описание датасета Online Shoppers Purchasing Intention

- **Источник:** UCI ML Repository (ID 468); Kaggle: roshansharma/online-shoppers-intention
- **Авторы:** C. O. Sakar, S. Polat, M. Katircioglu, Y. Kastro (2018)
- **Размер:** 12330 строк, 18 столбцов (17 признаков + целевая `Revenue`)
- **Пропусков:** 0
- **Дубликатов строк:** 125
- **Класс True (покупка):** 1908 (15.47%)
- **Класс False (нет покупки):** 10422 (84.53%)

## Столбцы

| Столбец | Тип в pandas |
|---|---|
| Administrative | int64 |
| Administrative_Duration | float64 |
| Informational | int64 |
| Informational_Duration | float64 |
| ProductRelated | int64 |
| ProductRelated_Duration | float64 |
| BounceRates | float64 |
| ExitRates | float64 |
| PageValues | float64 |
| SpecialDay | float64 |
| Month | str |
| OperatingSystems | int64 |
| Browser | int64 |
| Region | int64 |
| TrafficType | int64 |
| VisitorType | str |
| Weekend | bool |
| Revenue | bool |

**Особенность:** месяц июнь записан как `June`, остальные месяцы — тремя буквами (`Feb`, `Mar`, …).