<div align="center">

# ArisuLoveASMR

Русский | [English](README_EN.md) | [简体中文](README_ZH.md) | [Español](README_ES.md)

Google Colab ноутбук для автоматической генерации субтитров и их перевода на любой язык **без цензуры**

[![Colab](https://img.shields.io/badge/Open%20in%20Colab-orange?logo=googlecolab)](https://colab.research.google.com/github/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)
[![Notebook](https://img.shields.io/badge/Jupyter%20Notebook-100%25-lightgrey)](https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)

</div>

<img width="1612" height="908" alt="forasmr" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/forasmr.png" />

---

## Описание

**ArisuLoveASMR** — удобный Google Colab ноутбук с графическим интерфейсом, который позволяет:

- Автоматически распознавать речь в ASMR-аудио и видео
- Создавать субтитры в форматах **SRT / VTT / LRC**
- Определять спикеров и **автоматически давать им имена** через Groq
- Переводить на любой язык **без цензуры**
- Работать как с медиафайлами, так и с уже готовыми субтитрами
- Обрабатывать сразу несколько файлов (в том числе из папки Google Drive)

---

## Откуда брать ASMR и куда закидывать субтитры

Для удобной работы рекомендуется использовать:

- **[KikoFlu](https://github.com/pa-jesusf/KikoFlu)** — удобный инструмент для скачивания ASMR и загрузки файлов/субтитров в плеер
- **[asmr.one](https://asmr.one)** — сейчас без азиатского VPS пользоваться сложно; это ограничение можно обойти через [KikoFlu](https://github.com/pa-jesusf/KikoFlu)

---

## Возможности

### Распознавание речи

- **WhisperX** (модели: `large-v3`, `large-v3-turbo`, `distil-large-v3`, `large-v2`, `medium`)
- VAD-фильтр для лучшей сегментации
- Настройка Beam Search
- Определение спикеров (Diarization) — можно включать и выключать
- Автоматическое именование спикеров через **Groq**
- Поддержка большого количества аудио- и видеоформатов
- Можно загружать уже готовые субтитры (`.srt` / `.vtt` / `.lrc`) и сразу переводить их

### Перевод

| Переводчик | Тип | API Key | Offline | Примечание |
|------------------------------|-----------|----------|---------|----------------------------------------------|
| **Google Translate** | API | | | Быстрый и стабильный |
| **DeepL** | API | ✓ | | Требует `DEEPL_API_KEY` |
| **Gemini** | API | ✓ | | Требует `GEMINI_API_KEY` + fallback на Google |
| **Groq (Llama 3.3 70B)** | API | ✓ | | Требует `GROQ_API_KEY` |
| **Groq (Qwen 3.6 27B)** | API | ✓ | | Требует `GROQ_API_KEY` |
| **Qwen2.5** | Локальная | | ✓ | 7B Uncensored (может съесть VRAM) |
| **Dolphin 2.9.1** | Локальная | | ✓ | На базе Llama-3-8B (может съесть VRAM) |

Дополнительно:

- Инструкции по стилю перевода
- Глоссарий (термины в формате `источник = перевод`)
- Защита от пустых ответов Gemini: при цензуре автоматически переключается на Google Translate
- Имена спикеров подстраиваются под выбранный язык перевода

> ⚠️ Локальные модели не рекомендуются на Colab T4: высокий риск нехватки VRAM. Лучше использовать API (Google / DeepL / Gemini / Groq).

---

### Пример

<img width="1612" height="908" alt="kikoflu" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/screenshots_kikoflu.png" />

*Скриншот из плеера [KikoFlu](https://github.com/pa-jesusf/KikoFlu) с импортированными субтитрами, созданными с помощью этого ноутбука*

---

## Environment Variables

| Переменная | Описание | Примечание |
|------------------|-------------------------------|------------------------------------------|
| `HF_TOKEN` | Токен Hugging Face | Нужен для диаризации (спикеры) |
| `DEEPL_API_KEY` | API-ключ DeepL | Обязателен для DeepL |
| `GEMINI_API_KEY` | API-ключ Gemini | Обязателен для Gemini |
| `GROQ_API_KEY` | API-ключ Groq | Нужен для перевода через Groq и имён спикеров |

Где взять:

- HF_TOKEN → [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)  
  (и принять условия [pyannote/speaker-diarization-community-1](https://huggingface.co/pyannote/speaker-diarization-community-1))
- DEEPL_API_KEY → [deepl.com/pro-api](https://www.deepl.com/pro-api)
- GEMINI_API_KEY → [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
- GROQ_API_KEY → [console.groq.com/keys](https://console.groq.com/keys)

---

## Как пользоваться

1. Открой ноутбук в Google Colab по кнопке выше  
2. Выбери GPU: **Среда выполнения → Сменить среду выполнения → T4**  
3. Запусти ячейки по порядку  
4. Вставь нужные API-ключи  
5. Подключи Google Drive (если хочешь работать с файлами из Drive)  
6. В интерфейсе:
   - загрузи аудио/видео **или** готовые субтитры  
   - выбери модель Whisper  
   - включи/выключи диаризацию и именование спикеров  
   - выбери переводчик и язык перевода  
   - при необходимости добавь стиль и глоссарий  
7. Нажми **«Запустить обработку»**

Готовые файлы появятся в интерфейсе и сохранятся на Google Drive.

---

## Структура папок на Google Drive

После запуска GUI автоматически создаётся:

| Папка | Назначение |
|------------------------|--------------------------------------------------------|
| `input/` | Оригинальные файлы для обработки |
| `ASMR_transcription/` | Непереведённые транскрипции (`.txt`) |
| `ASMR_Original/` | Непереведённые субтитры в выбранном формате |
| `ASMR_Resultat/` | Переведённые субтитры |

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

- [Открыть в Google Colab]([https://colab.research.google.com/drive/1QCxElEzcapq9Fv25Cu4NjeMVLvkhW60I?usp=sharing](https://colab.research.google.com/github/zyddnys/manga-image-translator/blob/main/run_as_colab.ipynb))
- [Репозиторий Manga Image Translator](https://github.com/zyddnys/manga-image-translator#online-version)



## Вопросы и предложения

Если у вас есть вопросы, предложения по улучшению или вы знаете другие полезные инструменты для автоперевода — буду очень рад их услышать!

Создавайте [Issue](https://github.com/ArisuLoveASMR/ArisuLoveASMR/issues)
