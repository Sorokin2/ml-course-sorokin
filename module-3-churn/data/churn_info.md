# Churn Info — описание датасета telco_churn.csv

## Общая информация

- Формат: CSV, разделитель — запятая
- Объём: 7043 строки, 21 столбец
- Объект: клиент телеком-компании
- Целевая переменная: Churn (факт оттока)
- Задача: бинарная классификация (churn prediction)
- Распределение Churn: No — ~5174 (73.5%), Yes — ~1869 (26.5%) — умеренный дисбаланс
- Пропуски: в TotalCharges ~11 значений-пробелов (у клиентов с tenure = 0)

---

## Столбцы

1. customerID — string — уникальный идентификатор клиента. Не признак, удаляется перед обучением.
2. gender — categorical — пол: Male, Female.
3. SeniorCitizen — binary (0/1) — признак пожилого клиента: 0 — нет, 1 — да.
4. Partner — categorical — наличие партнёра: Yes, No.
5. Dependents — categorical — наличие иждивенцев: Yes, No.
6. tenure — numeric (int) — стаж клиента в месяцах, 0–72.
7. PhoneService — categorical — подключена ли телефония: Yes, No.
8. MultipleLines — categorical — несколько телефонных линий: Yes, No, No phone service.
9. InternetService — categorical — тип интернет-подключения: DSL, Fiber optic, No.
10. OnlineSecurity — categorical — онлайн-безопасность: Yes, No, No internet service.
11. OnlineBackup — categorical — онлайн-бэкап: Yes, No, No internet service.
12. DeviceProtection — categorical — защита устройства: Yes, No, No internet service.
13. TechSupport — categorical — техподдержка: Yes, No, No internet service.
14. StreamingTV — categorical — стриминг ТВ: Yes, No, No internet service.
15. StreamingMovies — categorical — стриминг фильмов: Yes, No, No internet service.
16. Contract — categorical — тип контракта: Month-to-month, One year, Two year.
17. PaperlessBilling — categorical — электронный счёт: Yes, No.
18. PaymentMethod — categorical — способ оплаты: Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic).
19. MonthlyCharges — numeric (float) — ежемесячная плата, ~18–119.
20. TotalCharges — numeric (float, в исходнике строка) — суммарные начисления, ~19–8700; есть пропуски.
21. Churn — target (binary) — отток: Yes, No.