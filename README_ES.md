<div align="center">

# ArisuLoveASMR

[Русский](README.md) | [English](README_EN.md) | [简体中文](README_ZH.md) | Español

Google Colab notebook para la generación automática de subtítulos y su traducción a cualquier idioma **sin censura**

[![Colab](https://img.shields.io/badge/Open%20in%20Colab-orange?logo=googlecolab)](https://colab.research.google.com/github/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR_ES.ipynb)
[![Notebook](https://img.shields.io/badge/Jupyter%20Notebook-100%25-lightgrey)](https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR_ES.ipynb)

</div>

<img width="1612" height="908" alt="forasmr" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/forasmr_es.png" />

---

## Descripción

**ArisuLoveASMR** es un cómodo notebook de Google Colab con interfaz gráfica que permite:

- Reconocer automáticamente el habla en audio y vídeo ASMR
- Crear subtítulos en formatos **SRT / VTT / LRC**
- Detectar hablantes y **asignarles nombres automáticamente** con Groq
- Traducir a cualquier idioma **sin censura**
- Trabajar tanto con archivos multimedia como con subtítulos ya existentes
- Procesar varios archivos a la vez (también desde una carpeta de Google Drive)

---

## De dónde sacar ASMR y dónde poner los subtítulos

Para trabajar cómodamente se recomienda usar:

- **[KikoFlu](https://github.com/pa-jesusf/KikoFlu)** — herramienta práctica para descargar ASMR y cargar archivos/subtítulos en el reproductor
- **[asmr.one](https://asmr.one)** — actualmente es difícil usarlo sin un VPS asiático; esta limitación se puede evitar con [KikoFlu](https://github.com/pa-jesusf/KikoFlu)

---

## Funciones

### Reconocimiento de voz

- **WhisperX** (modelos: `large-v3`, `large-v3-turbo`, `distil-large-v3`, `large-v2`, `medium`)
- Filtro VAD para una mejor segmentación
- Ajuste de Beam Search
- Detección de hablantes (Diarization) — se puede activar y desactivar
- Asignación automática de nombres a los hablantes mediante **Groq**
- Soporte para una gran cantidad de formatos de audio y vídeo
- Se pueden cargar subtítulos ya hechos (`.srt` / `.vtt` / `.lrc`) y traducirlos directamente

### Traducción

| Traductor | Tipo | API Key | Offline | Nota |
|------------------------------|-----------|----------|---------|----------------------------------------------|
| **Google Translate** | API | | | Rápido y estable |
| **DeepL** | API | ✓ | | Requiere `DEEPL_API_KEY` |
| **Gemini** | API | ✓ | | Requiere `GEMINI_API_KEY` + fallback a Google |
| **Groq (Llama 3.3 70B)** | API | ✓ | | Requiere `GROQ_API_KEY` |
| **Groq (Qwen 3.6 27B)** | API | ✓ | | Requiere `GROQ_API_KEY` |
| **Qwen2.5** | Local | | ✓ | 7B Uncensored (puede consumir mucha VRAM) |
| **Dolphin 2.9.1** | Local | | ✓ | Basado en Llama-3-8B (puede consumir mucha VRAM) |

Además:

- Instrucciones de estilo de traducción
- Glosario (términos en formato `origen = traducción`)
- Protección ante respuestas vacías de Gemini: si hay censura, cambia automáticamente a Google Translate
- Los nombres de los hablantes se adaptan al idioma de destino elegido

> ⚠️ No se recomiendan los modelos locales en Colab T4: alto riesgo de quedarse sin VRAM Es mejor usar API (Google / DeepL / Gemini / Groq).

---

### Ejemplo

<img width="1612" height="908" alt="kikoflu" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/screenshots_kikoflu.png" />

*Captura del reproductor [KikoFlu](https://github.com/pa-jesusf/KikoFlu) con subtítulos importados creados con este notebook*

---

## Variables de entorno

| Variable | Descripción | Nota |
|------------------|-------------------------------|------------------------------------------|
| `HF_TOKEN` | Token de Hugging Face | Necesario para la diarización (hablantes) |
| `DEEPL_API_KEY` | Clave API de DeepL | Obligatoria para DeepL |
| `GEMINI_API_KEY` | Clave API de Gemini | Obligatoria para Gemini |
| `GROQ_API_KEY` | Clave API de Groq | Necesaria para la traducción con Groq y los nombres de hablantes |

Dónde obtenerlas:

- HF_TOKEN → [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)  
  (y aceptar las condiciones de [pyannote/speaker-diarization-community-1](https://huggingface.co/pyannote/speaker-diarization-community-1))
- DEEPL_API_KEY → [deepl.com/pro-api](https://www.deepl.com/pro-api)
- GEMINI_API_KEY → [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
- GROQ_API_KEY → [console.groq.com/keys](https://console.groq.com/keys)

---

## Cómo usarlo

1. Abre el notebook en Google Colab con el botón de arriba  
2. Elige GPU: **Entorno de ejecución → Cambiar tipo de entorno de ejecución → T4**  
3. Ejecuta las celdas en orden  
4. Introduce las claves API necesarias  
5. Conecta Google Drive (si quieres trabajar con archivos desde Drive)  
6. En la interfaz:
   - sube audio/vídeo **o** subtítulos ya hechos  
   - elige el modelo Whisper  
   - activa/desactiva la diarización y el nombrado de hablantes  
   - elige el traductor y el idioma de destino  
   - si hace falta, añade estilo y glosario  
7. Pulsa **«Iniciar procesamiento»**

Los archivos listos aparecerán en la interfaz y se guardarán en Google Drive.

---

## Estructura de carpetas en Google Drive

Tras iniciar la GUI se crea automáticamente:

| Carpeta | Función |
|------------------------|--------------------------------------------------------|
| `input/` | Archivos originales para procesar |
| `ASMR_transcription/` | Transcripciones no traducidas (`.txt`) |
| `ASMR_Original/` | Subtítulos no traducidos en el formato elegido |
| `ASMR_Resultat/` | Subtítulos traducidos |

Ruta completa:
`/content/drive/MyDrive/ASMR_ENGINEERING/`

---

### Nota

- Si la GUI no ve tu archivo, añade el formato necesario en el **bloque 3 del código** en los parámetros `file_types=` y `supported`.
- Puedes añadir fácilmente tu propio modelo local de traducción insertando su nombre en `AVAILABLE_MODELS`.

---

## Recomendación personal

¿Quieres traducir manga?  
Te puedo recomendar una excelente herramienta:

- [Abrir en Google Colab](https://colab.research.google.com/drive/1QCxElEzcapq9Fv25Cu4NjeMVLvkhW60I?usp=sharing)
- [Repositorio Manga Image Translator](https://github.com/zyddnys/manga-image-translator#online-version)

## Preguntas y sugerencias

Si tienes preguntas, sugerencias de mejora o conoces otras herramientas útiles para la autotraducción, ¡estaré muy contento de oírlas!

Crea un [Issue](https://github.com/ArisuLoveASMR/ArisuLoveASMR/issues)
