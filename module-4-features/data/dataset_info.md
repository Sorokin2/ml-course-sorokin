**Источник:** https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset

**Структура:**
- Всего примеров: 12 330
- Признаков: 17 (+ целевая `Revenue`)
- Числовых признаков: 10
- Категориальных признаков: 7 (включая `Month`)

**Описание ключевых столбцов:**
| Столбец | Тип | Описание | Пропуски |
|---------|-----|----------|----------|
| Administrative | int | Число посещённых админ. страниц | 0% |
| Administrative_Duration | float | Время на админ. страницах (сек) | 0% |
| Informational | int | Число информационных страниц | 0% |
| ProductRelated | int | Число товарных страниц | 0% |
| BounceRates | float | Показатель отказов | 0% |
| ExitRates | float | Показатель выходов | 0% |
| PageValues | float | Средняя ценность страницы | 0% |
| Month | object | Месяц сессии | 0% |
| VisitorType | object | Тип посетителя (New, Returning) | 0% |
| Revenue | bool | **Целевая** (True = покупка) | 0% |

**Распределение классов:**
- False (нет покупки): 10 422 (84.5%)
- True (покупка): 1 908 (15.5%)
