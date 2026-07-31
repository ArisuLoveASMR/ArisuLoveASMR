<div align="center">
 
  # ArisuLoveASMR
  [Русский](README.md) | English | [简体中文](README_ZH.md)
 
  Google Colab notebook for automatic subtitle generation and translation into any language
 
  [![Colab](https://img.shields.io/badge/Open%20in%20Colab-orange?logo=googlecolab)](https://colab.research.google.com/github/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)
  [![Notebook](https://img.shields.io/badge/Jupyter%20Notebook-100%25-lightgrey)](https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)
</div>

<img width="1612" height="908" alt="forasmr" src="https://github.com/user-attachments/assets/7c6fb1d0-f5bf-4146-98aa-9b5f96989140" />

---

## Description

**ArisuLoveASMR** is a convenient Google Colab notebook with a graphical interface that allows you to:

- Automatically recognize speech in ASMR audio and video
- Generate high-accuracy subtitles
- Translate them into any language
- Work with both media files and existing subtitles

---

## Where to get ASMR and subtitles

For convenient work, it is recommended to use:

- **[KikoFlu](https://github.com/pa-jesusf/KikoFlu)** — a convenient tool for downloading ASMR and uploading subtitles
- **[asmr.one](https://asmr.one)** — Currently, using asmr.one without an Asian VPS is not possible. This limitation can be bypassed using [KikoFlu](https://github.com/pa-jesusf/KikoFlu)

---

## Features

### Speech Recognition
- **WhisperX** (models: `large-v3`, `large-v3-turbo`, `distil-large-v3`, `large-v2`, `medium`)
- VAD filter for better segmentation
- Beam Search configuration
- Speaker diarization — can be enabled/disabled
- Support for a large number of audio and video formats

### Translation

Several translation methods are supported:

| Translator            | Type     | API Key | Offline | Note                                          |
|-----------------------|----------|---------|---------|-----------------------------------------------|
| **Google Translate**  | API      |         |         | Fast and stable                               |
| **DeepL**             | API      | ✓       |         | Requires `DEEPL_API_KEY`                      |
| **Gemini**            | API      | ✓       |         | Requires `GEMINI_API_KEY` + fallback to Google|
| **Qwen2.5**           | Local    |         | ✓       | 7B Uncensored                                 |
| **Dolphin 2.9.1**     | Local    |         | ✓       | Based on Llama-3-8B                           |

### Environment Variables

| Environment Variable | Description              | Default | Remarks                        |
|----------------------|--------------------------|---------|--------------------------------|
| `DEEPL_API_KEY`      | DeepL API Key            | `''`    | Required for DeepL             |
| `GEMINI_API_KEY`     | Gemini API Key           | `''`    | Required for Gemini            |
| `HF_TOKEN`           | Hugging Face Token       | `''`    | Required for diarization       |

### Convenience
- Beautiful Gradio interface
- Google Drive folder support
- Multiple file upload

---

## How to use

1. Open the notebook in Google Colab using the button above
2. Connect Google Drive (if you want to work with files from Drive)
3. Run the cells in order
4. In the interface:
   - Upload audio/video **or** existing subtitles
   - Select Whisper model
   - Select translator
   - Choose target language
   - Optionally add style instructions and glossary
5. Click **“Start Processing”**

Finished files will appear in the interface and will also be automatically saved to the Google Drive folder.

---

## Google Drive Folder Structure

After launching the GUI, the notebook automatically creates the following structure:

| Folder                 | Purpose                                              |
|------------------------|------------------------------------------------------|
| `input/`               | Original files to be processed                       |
| `ASMR_transcription/`  | Untranslated files in `.txt` format                  |
| `ASMR_Original/`       | Untranslated files converted to subtitle format      |
| `ASMR_Resultat/`       | Translated subtitles                                 |

Full path:  
`/content/drive/MyDrive/ASMR_ENGINEERING/`

---

### Note

- If the GUI does not detect your file, add the required format in the **3rd code block** in the `file_types=` and `supported` parameters.
- You can easily add your own local translation model by inserting its name into `AVAILABLE_MODELS`.

---

## Personal Recommendation

Want to translate manga?  
I can recommend a great tool:

- [Open in Google Colab](https://colab.research.google.com/drive/1QCxElEzcapq9Fv25Cu4NjeMVLvkhW60I?usp=sharing)
- [Manga Image Translator Repository](https://github.com/zyddnys/manga-image-translator#online-version)

---

## Questions and Suggestions

If you have any questions, suggestions for improvement, or know other useful tools for automatic translation — I would be very happy to hear them!

Create an [Issue](https://github.com/ArisuLoveASMR/ArisuLoveASMR/issues)
