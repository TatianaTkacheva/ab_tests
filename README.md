# A/B Testing

## 📌 Описание проекта
В этом репозитории представлены мои проекты по анализу A/B-тестов.

## 📊 Данные
- Источник: ClickHouse, таблица feed_actions
- Период: 2025-11-14 — 2025-11-20

## 🔍 Ход анализа
1. Загрузка данных через pandahouse
2. Расчёт CTR = likes / views
3. Проверка распределений
4. Mann-Whitney U test
5. Визуализация

## 📈 Результаты
- CTR (группа 0): 20.02%
- CTR (группа 1): 20.96%
- p-value = 2.4e-50 (статистически значимо)
- ✅ Тест успешен

## 🛠 Технологии
- Python 3.10
- pandas, numpy
- scipy.stats
- pandahouse
- matplotlib, seaborn

## 🚀 Запуск
1. Скопировать `.env.example` в `.env` и заполнить свои данные
2. Установить зависимости: `pip install -r requirements.txt`
3. Запустить Jupyter: `jupyter notebook`

## 📁 Файлы
- `ab_test_analysis.ipynb` — основной ноутбук
- `.env.example` — шаблон для подключения к БД
- `requirements.txt` — зависимости
EOF