# Модуль 1 – Titanic: EDA + бинарная классификация

**Автор:** Сорокин М.А., ПКТ6-23-1
**Дата:** 2026-09-30

## Результаты

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|---|
| Logistic Regression | 0.8045 | 0.7833 | 0.6812 | 0.7287 | 0.8486 |
| Decision Tree | 0.7821 | 0.7419 | 0.6667 | 0.7023 | 0.8132 |
| Random Forest | 0.8212 | 0.8491 | 0.6522 | 0.7377 | 0.8498 |

**Время обучения:** ~0.004 сек (LR), ~0.003 сек (DT), ~0.077 сек (RF)

**Лучшая модель:** Random Forest (ROC-AUC = 0.8498)

## Быстрый старт

Вы можете загрузить обученную модель и использовать её для предсказаний без переобучения.

```python
import joblib
import requests
from io import BytesIO
import pandas as pd

# URL к папке с моделями в репозитории
BASE_URL = "https://raw.githubusercontent.com/Sorokin2/ml-course-sorokin/main/module-1-titanic"

# Загрузка модели Logistic Regression
model_url = f"{BASE_URL}/models/lr_model.pkl"
model = joblib.load(BytesIO(requests.get(model_url).content))

# Загрузка scaler'а (для LR)
scaler_url = f"{BASE_URL}/models/scaler.pkl"
scaler = joblib.load(BytesIO(requests.get(scaler_url).content))

# Загрузка списка признаков
features_url = f"{BASE_URL}/models/feature_cols.json"
feature_cols = requests.get(features_url).json()

print("Модель, scaler и признаки успешно загружены!")

# Пример предсказания для нового пассажира
# (убедитесь, что данные прошли тот же Feature Engineering, что и при обучении)
