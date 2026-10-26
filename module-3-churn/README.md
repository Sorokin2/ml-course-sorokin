# 📉 Module 3 — Customer Churn: Ансамблевые методы

**Автор:** Сорокин Михаил Анатольевич, ПКТ6-23-1
**Дисциплина:** Машинное обучение и искусственный интеллект
**Модуль 3:** Ансамблевые методы (Базовый и продвинутый уровень)
**Датасет:** [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
**Дата сдачи:** 2026-10-20

---

## 📊 Результаты

### Сравнение baseline-моделей

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC | Время обучения |
|--------|----------|-----------|--------|-----|---------|----------------|
| Random Forest | 0.7615 | 0.5365 | 0.7460 | 0.6242 | 0.8388 | 0.295 сек |
| XGBoost | 0.7608 | 0.5383 | 0.6952 | 0.6068 | 0.8285 | 0.135 сек |
| LightGBM | 0.7601 | 0.5345 | 0.7460 | 0.6228 | 0.8384 | 0.086 сек |
| CatBoost | 0.7488 | 0.5187 | 0.7433 | 0.6110 | **0.8409** | 0.461 сек |

### Итоговая модель (CatBoost + Optuna)

| Модель | Accuracy | Precision | Recall | F1 | ROC-AUC |
|--------|----------|-----------|--------|-----|---------|
| **CatBoost (Optuna)** | 0.7410 | 0.5077 | **0.7968** | 0.6202 | **0.8461** |

**Прирост ROC-AUC:** +0.0052 (+0.62%) к baseline CatBoost.

**Ключевая метрика:** ROC-AUC = **0.8461**, Recall (Ушёл) = **0.797** — модель ловит ~80% уходящих клиентов, что соответствует бизнес-приоритету (стоимость пропуска ушедшего клиента >> стоимость ложного срабатывания).

---

## 🎯 Цель работы

Освоить ансамблевые методы машинного обучения на примере задачи прогнозирования оттока клиентов:
- обучение 4 ансамблевых моделей (RF, XGBoost, LightGBM, CatBoost);
- сравнение по метрикам и скорости;
- байесовская оптимизация гиперпараметров через Optuna;
- интерпретация модели через SHAP.

---

## 🚀 Быстрый старт

### Загрузка модели из репозитория

```python
import joblib
import requests
from io import BytesIO

BASE_URL = "https://raw.githubusercontent.com/Sorokin2/ml-course-sorokin/main/module-3-churn"

# Загрузка лучшей модели
model = joblib.load(BytesIO(requests.get(f"{BASE_URL}/models/best_model.pkl").content))

# Загрузка списка признаков
feature_cols = requests.get(f"{BASE_URL}/models/feature_cols.json").json()

# Предсказание (X_test должен содержать признаки из feature_cols в том же порядке)
y_pred = model.predict(X_test)
y_proba = model.predict_proba(X_test)[:, 1]