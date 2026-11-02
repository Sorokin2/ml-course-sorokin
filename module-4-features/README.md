# 🛒 Module 4 — Online Shoppers: Инженерия признаков

**Автор:** Иванов И.И., ПКТб-23-1  
**Дисциплина:** Машинное обучение и ИИ  
**Модуль 4:** Инженерия признаков и работа с нестандартными данными  
**Датасет:** [Online Shoppers Purchasing Intention](https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset)  
**Дата сдачи:** 2026-XX-XX

---

## 📊 Результаты

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC | Время |
|--------|----------|-----------|--------|-----|---------|-------|
| Random Forest | 0.8646 | 0.5430 | 0.7932 | 0.6447 | 0.9287 | 0.430 сек |
| XGBoost | 0.8788 | 0.5885 | 0.7225 | 0.6486 | 0.9214 | 0.280 сек |
| LightGBM | 0.8755 | 0.5701 | 0.7984 | 0.6652 | 0.9260 | 0.151 сек |
| CatBoost | 0.8731 | 0.5640 | 0.7958 | 0.6602 | 0.9289 | 0.578 сек |
| **CatBoost (Optuna)** | **0.8609** | **0.5326** | **0.8351** | **0.6504** | **0.9316** | — |

**Лучшая модель:** CatBoost с подобранными через Optuna гиперпараметрами.  
**Прирост ROC-AUC:** +0.29% к baseline CatBoost.

---

## 🚀 Быстрый старт

### Загрузка модели из репозитория

```python
import joblib
import requests
from io import BytesIO

BASE_URL = "https://raw.githubusercontent.com/Sorokin2/ml-course-sorokin/main/module-4-features"

# Загрузка лучшей модели
model = joblib.load(
    BytesIO(requests.get(f"{BASE_URL}/models/best_model.pkl").content)
)

# Загрузка списка признаков
feature_cols = requests.get(f"{BASE_URL}/models/feature_cols.json").json()

# Предсказание (X_test должен содержать признаки из feature_cols в том же порядке)
y_pred = model.predict(X_test)
y_proba = model.predict_proba(X_test)[:, 1]