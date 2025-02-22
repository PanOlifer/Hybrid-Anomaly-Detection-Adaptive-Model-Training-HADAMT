# Hybrid-Anomaly-Detection-Adaptive-Model-Training-HADAMT-

📌 README: Архитектура проекта HADAMT

Hybrid Anomaly Detection and Mitigation Tool (HADAMT) – модуль для выявления и защиты от атак data poisoning с использованием гибридных алгоритмов GAN + VAN + LOF.

📂 Структура проекта
```
HADAMT/                     # 📂 Главная папка проекта
│── data/                    # 📂 Данные (поддержка любых датасетов)
│   ├── raw/                 # 📂 Исходные (необработанные) данные
│   ├── processed/           # 📂 Обработанные данные после предобработки
│   ├── results/             # 📂 Финальные результаты после обучения
│── models/                  # 📂 Сохранённые модели
│   ├── base_model.h5        # 🤖 Базовая модель (до атак)
│   ├── poisoned_model.h5    # ☠️ Модель после отравления данных
│   ├── filtered_model.h5    # 🔍 Модель после фильтрации (защита)
│   ├── augmented_model.h5   # 🛡️ Модель с защитой через аугментацию
│── logs/                    # 📂 Логирование экспериментов
│   ├── mlflow/              # 📝 Логи MLflow (эксперименты, параметры)
│   ├── tensorboard/         # 📊 Логи TensorBoard (графики обучения)
│── notebooks/               # 📂 Jupyter-ноутбуки для экспериментов
│   ├── 1_data_analysis.ipynb   # 📊 Анализ данных
│   ├── 2_train_baseline.ipynb  # 🏗️ Обучение базовой модели
│   ├── 3_data_poisoning.ipynb  # ☠️ Атака Data Poisoning
│   ├── 4_defense_mechanisms.ipynb  # 🔍 Методы защиты
│── scripts/                 # 📂 Python-скрипты для обучения
│   ├── preprocess.py        # 🏗️ Предобработка данных (очистка, нормализация)
│   ├── train_baseline.py    # 🤖 Обучение базовой модели
│   ├── train_poisoned.py    # ☠️ Обучение модели после атаки
│   ├── detect_anomalies.py  # 🔍 Выявление отравленных данных (LOF + VAN)
│   ├── train_defended.py    # 🛡️ Обучение защищённой модели
│   ├── log_mlflow.py        # 📝 Логирование экспериментов через MLflow
│   ├── log_tensorboard.py   # 📊 Логирование через TensorBoard
│── configs/                 # 📂 Конфигурационные файлы
│   ├── config.yaml          # ⚙️ Основные параметры обучения
│   ├── mlflow.yaml          # ⚙️ Настройки MLflow
│── results/                 # 📂 Готовые результаты и отчёты
│   ├── final_metrics.csv    # 📊 Таблица с метриками всех моделей
│   ├── final_plots/         # 📊 Графики потерь, точности, recall
│── tests/                   # 📂 Тестирование кода
│   ├── test_preprocessing.py  # 🔬 Тестирование предобработки
│   ├── test_models.py         # 🔬 Тестирование моделей
│── README.md                 # 📖 Описание проекта
│── requirements.txt           # 📦 Зависимости (установка пакетов)
│── setup.py                   # ⚙️ Установка проекта
│── LICENSE                    # 📜 Лицензия проекта
```
📌 Описание папок и файлов

🔹 1. data/ – данные

📂 Здесь хранятся все данные проекта, включая исходные, обработанные и результаты обучения.
✔ raw/ – исходные датасеты (поддерживается любой датасет!)
✔ processed/ – нормализованные и очищенные данные
✔ results/ – файлы после обучения моделей

🔹 2. models/ – сохранённые модели

📂 Обученные модели на каждом этапе эксперимента.
✔ base_model.h5 – базовая модель (до атак)
✔ poisoned_model.h5 – модель после атак data poisoning
✔ filtered_model.h5 – модель после защиты Isolation Forest + LOF + VAN
✔ augmented_model.h5 – модель с защитой аугментацией данных

🔹 3. logs/ – логирование и мониторинг

📂 Все эксперименты автоматически логируются через MLflow и TensorBoard.
✔ mlflow/ – параметры, метрики, версии моделей
✔ tensorboard/ – визуализация обучения

🔹 4. notebooks/ – эксперименты

📂 Jupyter-ноутбуки для анализа и тестирования.
✔ 1_data_analysis.ipynb – анализ данных
✔ 2_train_baseline.ipynb – обучение базовой модели
✔ 3_data_poisoning.ipynb – моделирование атаки data poisoning
✔ 4_defense_mechanisms.ipynb – тестирование методов защиты

🔹 5. scripts/ – основные Python-скрипты

📂 Код для работы с моделями и данными.
✔ preprocess.py – очистка данных, нормализация
✔ train_baseline.py – обучение базовой модели
✔ train_poisoned.py – обучение модели после атаки
✔ detect_anomalies.py – обнаружение атакованных данных LOF + VAN
✔ train_defended.py – обучение защищённой модели

🔹 6. configs/ – конфигурационные файлы

📂 Настройки обучения (редактируем параметры, не меняя код).
✔ config.yaml – гиперпараметры моделей, пути к данным
✔ mlflow.yaml – настройки логирования

🔹 7. results/ – финальные отчёты

📂 Все финальные результаты и графики метрик.
✔ final_metrics.csv – таблица с метриками Accuracy, Recall, Precision
✔ final_plots/ – графики потерь, точности, F1-score

🔹 8. tests/ – тестирование

📂 Код для автоматического тестирования
✔ test_preprocessing.py – проверка предобработки данных
✔ test_models.py – проверка моделей

🚀 Установка проекта
	1.	Установите зависимости:
```
pip install -r requirements.txt
```
 2.	Запустите предобработку данных:
```
python scripts/preprocess.py
```
  3.	Обучите базовую модель:
```
python scripts/train_baseline.py
```
  4.	Запустите атаку data poisoning:
```
python scripts/train_poisoned.py
```
  5.	Запустите защиту от атак:
```
python scripts/detect_anomalies.py
python scripts/train_defended.py
```
  6.	Просмотр логов и метрик:
	•	MLflow UI: mlflow ui
	•	TensorBoard: tensorboard --logdir=logs/tensorboard/

📌 Описание гибридной архитектуры HADAMT

HADAMT использует гибридный метод детекции атак, включающий:
✅ VAN (Variational Autoencoder Network) – выявляет нестандартные распределения данных
✅ GAN (Generative Adversarial Network) – моделирует аномальные атаки
✅ LOF (Local Outlier Factor) – оценивает локальные выбросы
✅ Isolation Forest – фильтрует вредоносные данные

📌 Система объединяет несколько методов для точного выявления атак и защиты моделей!

🔹 Что дальше?

📌 Добавить поддержку Weights & Biases (W&B) для мониторинга?
📌 Добавить автоматическое обновление модели при детекции дрейфа?
📌 Дополнить проект API-интерфейсом? 🚀

HADAMT – гибридный модуль для защиты моделей от атак data poisoning. 🛡️🤖
🚀 Начинаем тестировать! 🚀
