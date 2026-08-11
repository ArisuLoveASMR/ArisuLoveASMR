<div align="center">

# ArisuLoveASMR

[Русский](README.md) | English | [简体中文](README_ZH.md) | [Español](README_ES.md)

Google Colab notebook for automatic subtitle generation and translation into any language **without censorship**

[![Colab](https://img.shields.io/badge/Open%20in%20Colab-orange?logo=googlecolab)](https://colab.research.google.com/github/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR_EN.ipynb)
[![Notebook](https://img.shields.io/badge/Jupyter%20Notebook-100%25-lightgrey)](https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR_EN.ipynb)

</div>

<img width="1612" height="908" alt="forasmr" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/forasmr_en.png" />

---

## Description

**ArisuLoveASMR** is a convenient Google Colab notebook with a graphical interface that allows you to:

- Automatically recognize speech in ASMR audio and video
- Create subtitles in **SRT / VTT / LRC** formats
- Detect speakers and **automatically assign names** via Groq
- Translate into any language **without censorship**
- Work with both media files and ready-made subtitles
- Process multiple files at once (including from a Google Drive folder)

---

## Where to get ASMR and where to put subtitles

For convenient use, we recommend:

- **[KikoFlu](https://github.com/pa-jesusf/KikoFlu)** — a handy tool for downloading ASMR and loading files/subtitles into the player
- **[asmr.one](https://asmr.one)** — currently difficult to use without an Asian VPS; this limitation can be bypassed with [KikoFlu](https://github.com/pa-jesusf/KikoFlu)

---

## Features

### Speech recognition

- **WhisperX** (models: `large-v3`, `large-v3-turbo`, `distil-large-v3`, `large-v2`, `medium`)
- VAD filter for better segmentation
- Beam Search configuration
- Speaker detection (Diarization) — can be enabled or disabled
- Automatic speaker naming via **Groq**
- Support for a wide range of audio and video formats
- You can upload ready-made subtitles (`.srt` / `.vtt` / `.lrc`) and translate them directly

### Translation

| Translator | Type | API Key | Offline | Notes |
|------------------------------|-----------|----------|---------|----------------------------------------------|
| **Google Translate** | API | | | Fast and stable |
| **DeepL** | API | ✓ | | Requires `DEEPL_API_KEY` |
| **Gemini** | API | ✓ | | Requires `GEMINI_API_KEY` + fallback to Google |
| **Groq (Llama 3.3 70B)** | API | ✓ | | Requires `GROQ_API_KEY` |
| **Groq (Qwen 3.6 27B)** | API | ✓ | | Requires `GROQ_API_KEY` |
| **Qwen2.5** | Local | | ✓ | 7B Uncensored (may consume a lot of VRAM) |
| **Dolphin 2.9.1** | Local | | ✓ | Based on Llama-3-8B (may consume a lot of VRAM) |

Additionally:

- Translation style instructions
- Glossary (terms in the format `source = translation`)
- Protection against empty Gemini responses: if content is censored, it automatically falls back to Google Translate
- Speaker names are adapted to the selected target language

> ⚠️ Local models are not recommended on Colab T4: high risk of running out of VRAM. Prefer APIs (Google / DeepL / Gemini / Groq).

---

### Example

<img width="1612" height="908" alt="kikoflu" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/screenshots_kikoflu.png" />

*Screenshot from the [KikoFlu](https://github.com/pa-jesusf/KikoFlu) player with imported subtitles created by this notebook*

---

## Environment Variables

| Variable | Description | Notes |
|------------------|-------------------------------|------------------------------------------|
| `HF_TOKEN` | Hugging Face token | Required for diarization (speakers) |
| `DEEPL_API_KEY` | DeepL API key | Required for DeepL |
| `GEMINI_API_KEY` | Gemini API key | Required for Gemini |
| `GROQ_API_KEY` | Groq API key | Required for Groq translation and speaker naming |

Where to get them:

- HF_TOKEN → [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)  
  (and accept the terms for [pyannote/speaker-diarization-community-1](https://huggingface.co/pyannote/speaker-diarization-community-1))
- DEEPL_API_KEY → [deepl.com/pro-api](https://www.deepl.com/pro-api)
- GEMINI_API_KEY → [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
- GROQ_API_KEY → [console.groq.com/keys](https://console.groq.com/keys)

---

## How to use

1. Open the notebook in Google Colab using the button above
2. Select a GPU: **Runtime → Change runtime type → T4**
3. Run the cells in order
4. Paste the required API keys
5. Connect Google Drive (if you want to work with files from Drive)
6. In the interface:
   - upload audio/video **or** ready-made subtitles
   - choose the Whisper model
   - enable/disable diarization and speaker naming
   - choose the translator and target language
   - optionally add style instructions and a glossary
7. Click **“Start processing”**

Finished files will appear in the interface and will be saved to Google Drive.

---

## Google Drive folder structure

After launching the GUI, the following structure is created automatically:

| Folder | Purpose |
|------------------------|--------------------------------------------------------|
| `input/` | Original files for processing |
| `ASMR_transcription/` | Untranslated transcriptions (`.txt`) |
| `ASMR_Original/` | Untranslated subtitles in the selected format |
| `ASMR_Resultat/` | Translated subtitles |

Full path:

`/content/drive/MyDrive/ASMR_ENGINEERING/`

---

### Notes

- If the GUI does not detect your file, add the required format in the **3rd code cell** in the `file_types=` and `supported` parameters.
- You can easily add your own local translation model by inserting its name into `AVAILABLE_MODELS`.

---

## Personal recommendation

Want to translate manga?

Here is a great tool:

- [Open in Google Colab](https://colab.research.google.com/github/zyddnys/manga-image-translator/blob/main/run_as_colab.ipynb)
- [Manga Image Translator repository](https://github.com/zyddnys/manga-image-translator#online-version)

## Questions and suggestions

If you have questions, improvement ideas, or know other useful tools for automatic translation — I would be very happy to hear them!

Create an [Issue](https://github.com/ArisuLoveASMR/ArisuLoveASMR/issues)
