# SHIFT-OCR Recognition Symbols

Проект распознания текста на изображениях

## Структура репозитория
```bash
├───config
│   └───shift_ocr
│       ├───detector
│       ├───loader
│       ├───postprocessor
│       ├───preprocessor
│       ├───recognizer
│       └───visualizer
├───notebooks
├───scripts
│   ├───dataset_prepare
│   │   ├───ddi
│   │   ├───pdfa
│   │   └───sroie
│   └───parsing_scripts
├───shift_ocr
│   ├───detectors
│   ├───loaders
│   ├───postprocessor
│   ├───preprocessor
│   ├───recognizer
│   ├───shift_ocr
│   ├───utils
│   └───visualizers
└───tests
    ├───detector
    └───test_loaders
```

В папке __shift_ocr__ представлены все необходимые скрипты для запуска и файл __main.py__

В __config__ лежат все .yaml файлы конфигурации для Hydra.

В папке __tests__ лежат все файлы для проверки работоспособности модулей

В __scripts__ представлены полезные материалы для работы с данными, в __notebooks__ - предпросмотр изображений с разметкой и форматирование датасетов

## Установка репозитория

Для локальной установки репозитория:
```bash
git clone https://gitlab.yc.ftc.ru/shift-recognition-symbols/backend/recognition-symbols-core
cd recognition-symbols-core
```

## Среда

Для создания среды рекомендуется использовать [Anaconda](https://www.anaconda.com/). Требуемая версия python для репозитория - 3.10.16

```bash
conda create --name <ENV_NAME> python=3.10.16
conda activate <ENV_NAME>
pip install -r requirements.txt
```

## Pre-commit

Для инициализации:

```bash
pre-commit install
```

Команда для запуска:

```bash
pre-commit run
```

Для проверки всех файлов можно использовать флаг --all-files

```bash
pre-commit run --all-files
```

## Запуск

### Основной способ:

```bash
python -m shift_ocr/main.py
```

### Альтернативный способ (через Docker)

```bash
docker build -t shift_ocr ./
docker run --rm shift_ocr
```

## Пример работы

(Сюда итоговую визуализацию)
