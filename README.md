<div align="center">
  
  # ArisuLoveASMR

 Русский | [English](README_EN.md) | [简体中文](README_ZH.md)
  
  Google Colab ноутбук для автоматической генерации субтитров и их перевода на любой язык
  
  [![Colab](https://img.shields.io/badge/Open%20in%20Colab-orange?logo=googlecolab)](https://colab.research.google.com/github/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)
  [![Notebook](https://img.shields.io/badge/Jupyter%20Notebook-100%25-lightgrey)](https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)
</div>

<img width="1612" height="908" alt="forasmr" src="https://github.com/user-attachments/assets/7c6fb1d0-f5bf-4146-98aa-9b5f96989140" />

---
## Описание

**ArisuLoveASMR** — это удобный Google Colab ноутбук с графическим интерфейсом, который позволяет:

- Автоматически распознавать речь в ASMR-аудио и видео
- Генерировать субтитры с высокой точностью
- Переводить их на любой язык
- Работать как с медиафайлами, так и с уже готовыми субтитрами
---
## Откуда брать ASMR и субтитры

Для удобной работы рекомендуется использовать:

- **[KikoFlu](https://github.com/pa-jesusf/KikoFlu)** — удобный инструмент для скачивания ASMR и загрузки субтитров  
- **[asmr.one](https://asmr.one)** — На данный момент пользоваться асмрваном без азиатского впс нету возможности. Это ограничение можно обойти с помощью [KikoFlu](https://github.com/pa-jesusf/KikoFlu) 

## Возможности

### Распознавание речи
- **WhisperX** (модели: `large-v3`, `large-v3-turbo`, `distil-large-v3`, `large-v2`, `medium`)
- VAD-фильтр для лучшей сегментации
- Настройка Beam Search
- Определение спикеров (Diarization) — можно включать/выключать
- Поддержка огромного количества аудио и видео форматов

### Перевод
Поддерживаются несколько способов перевода:

### Перевод

Поддерживаются несколько способов перевода:

| Переводчик              | Тип       | API Key              | Offline | Примечание                                      |
|-------------------------|-----------|----------------------|---------|-------------------------------------------------|
| **Google Translate**    | API       |                      |         | Быстрый и стабильный                            |
| **DeepL**               | API       | ✓                    |         | Требует `DEEPL_API_KEY`                         |
| **Gemini**              | API       | ✓                    |         | Требует `GEMINI_API_KEY` + fallback на Google   |
| **Qwen2.5**             | Локальная |                      | ✓       | 7B Uncensored                                   |
| **Dolphin 2.9.1**       | Локальная |                      | ✓       | На базе Llama-3-8B                              |

### Environment Variables

| Environment Variable   | Description                     | Default | Remarks                          |
|------------------------|---------------------------------|---------|----------------------------------|
| `DEEPL_API_KEY`        | DeepL API Key                   | `''`    | Обязателен для DeepL             |
| `GEMINI_API_KEY`       | Gemini API Key                  | `''`    | Обязателен для Gemini            |
| `HF_TOKEN`             | Hugging Face Token              | `''`    | Нужен для диаризации (спикеры)   |


### Удобство
- Красивый Gradio-интерфейс
- Работа с папкой Google Drive
- Множественная загрузка файлов

---

## Как пользоваться

1. Открой ноутбук в Google Colab по кнопке выше
2. Подключи Google Drive (если хочешь работать с файлами из Drive)
3. Запусти ячейки по порядку
4. В интерфейсе:
   - Загрузи аудио/видео **или** готовые субтитры
   - Выбери модель Whisper
   - Выбери переводчик
   - Укажи язык перевода
   - При необходимости добавь стиль и глоссарий
5. Нажми **«Запустить обработку»**

Готовые файлы появятся в интерфейсе и автоматически сохранятся в папку на Google Drive.

---

## Структура папок на Google Drive

После запуска GUI ноутбук автоматически создаёт следующую структуру:

| Папка                    | Назначение                                          |
|--------------------------|-----------------------------------------------------|
| `input/`                 | Оригинальные файлы, которые пойдут на обработку     |
| `ASMR_transcription/`    | Непереведённые файлы в формате `.txt`               |
| `ASMR_Original/`         | Непереведённые файлы, подстроенные под формат субтитров |
| `ASMR_Resultat/`         | Переведённые субтитры                               |

Полный путь:  
`/content/drive/MyDrive/ASMR_ENGINEERING/`

---

### Примечание

- Если GUI не видит ваш файл, добавьте нужный формат в **3-м блоке кода** в параметрах `file_types=` и `supported`.
- Вы можете легко добавить свою локальную модель для перевода, вставив её название в `AVAILABLE_MODELS`.

---

## Личная рекомендация

Хотите перевести мангу?  
Могу посоветовать отличный инструмент:

- [Открыть в Google Colab](https://colab.research.google.com/drive/1QCxElEzcapq9Fv25Cu4NjeMVLvkhW60I?usp=sharing)
- [Репозиторий Manga Image Translator](https://github.com/zyddnys/manga-image-translator#online-version)



## Вопросы и предложения

Если у вас есть вопросы, предложения по улучшению или вы знаете другие полезные инструменты для автоперевода — буду очень рад их услышать!

Создавайте [Issue](https://github.com/ArisuLoveASMR/ArisuLoveASMR/issues)
