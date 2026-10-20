# Модуль 2 – House Prices: предобработка и регрессия

**Автор:** Сорокин М.А., ПКТ6-23-1
**Дата:** 2026-10-19

## Результаты

| Модель | RMSE (log) | MAE (log) | R² | RMSE ($) |
|---|---|---|---|---|
| Linear Regression | 0.1240 | 0.0841 | 0.8913 | $18 894 |
| Ridge | 0.1240 | 0.0842 | 0.8912 | $18 923 |
| Lasso | 0.1217 | 0.0826 | 0.8953 | $18 374 |
| ElasticNet | 0.1218 | 0.0826 | 0.8951 | $18 382 |
| XGBoost | 0.1211 | 0.0789 | 0.8962 | $19 242 |

**Время обучения:** ~0.019 сек (LR), ~0.007 сек (Ridge), ~0.134 сек (Lasso), ~0.116 сек (ElasticNet), ~0.442 сек (XGBoost)

**Лучшая модель:** XGBoost (R² = 0.8962, MAE = 0.0789)

> Lasso обнулил 49 из 222 признаков, оставив 173 значимых.

## Быстрый старт

Вы можете загрузить обученную модель и использовать её для предсказаний без переобучения.

```python
import joblib
import requests
from io import BytesIO
import json

# URL к папке с моделями в репозитории
BASE_URL = "https://raw.githubusercontent.com/Sorokin2/ml-course-sorokin/main/module-2-house-prices"

# Загрузка модели XGBoost (лучшая)
model_url = f"{BASE_URL}/models/xgb_model.pkl"
model = joblib.load(BytesIO(requests.get(model_url).content))

# Загрузка scaler'а (для линейных моделей)
scaler_url = f"{BASE_URL}/models/scaler.pkl"
scaler = joblib.load(BytesIO(requests.get(scaler_url).content))

# Загрузка списка признаков
features_url = f"{BASE_URL}/models/feature_cols.json"
feature_cols = requests.get(features_url).json()

print("Модель, scaler и признаки успешно загружены!")

# Пример предсказания для нового дома
# (убедитесь, что данные прошли тот же Feature Engineering, что и при обучении)
```

## Структура

- `notebook.ipynb` — полный отчёт (14 разделов)
- `data/` — датасет (`train.csv`, `test.csv`) и описание (`house_prices_info.md`)
- `models/` — модели, scaler, список признаков, метрики
- `examples/` — графики EDA, остатков и предсказаний
- `requirements.txt` — зависимости

## Графики

- `examples/eda_plots.png` — сетка из 6 EDA-визуализаций
- `examples/predictions_scatter.png` — реальные vs предсказанные цены
- `examples/residuals.png` — анализ остатков XGBoost

## Метрики

Полные метрики всех моделей сохранены в `models/metrics.json`.