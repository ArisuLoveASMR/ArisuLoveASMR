<div align="center">
 
  # ArisuLoveASMR
 [Русский](README.md) | English | [简体中文](README_ZH.md)
 
  Google Colab notebook for automatic subtitle generation and uncensored translation into any language
 
  [![Colab](https://img.shields.io/badge/Open%20in%20Colab-orange?logo=googlecolab)](https://colab.research.google.com/github/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)
  [![Notebook](https://img.shields.io/badge/Jupyter%20Notebook-100%25-lightgrey)](https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)
</div>
<img width="1612" height="908" alt="forasmr" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/forasmr.png" />

---

## Description
**ArisuLoveASMR** is a convenient Google Colab notebook with a graphical interface that allows you to:
- Automatically transcribe speech from any ASMR audio or video
- Generate subtitles in SRT, VTT, and LRC formats
- Assign speakers
- Translate them into any language without censorship
- Process multiple files at once

---

## Where to Get ASMR and How to Use Subtitles
For a more convenient workflow, we recommend using:
- **[KikoFlu](https://github.com/pa-jesusf/KikoFlu)** — a handy tool for downloading ASMR and loading both ASMR files and subtitles into a player
- **[asmr.one](https://asmr.one)** — currently, accessing asmr.one without an Asian VPS is not possible. This restriction can be bypassed using [KikoFlu](https://github.com/pa-jesusf/KikoFlu)

## Features

### Speech Recognition
- **WhisperX** (models: `large-v3`, `large-v3-turbo`, `distil-large-v3`, `large-v2`, `medium`)
- VAD filter for better segmentation
- Adjustable Beam Search
- Speaker diarization (can be enabled/disabled)
- Support for a wide range of audio and video formats
- Protection against empty Gemini responses: when censorship is triggered, it automatically falls back to Google Translate

### Translation
Several translation methods are supported:

| Translator          | Type     | API Key | Offline | Notes                                      |
|---------------------|----------|---------|---------|--------------------------------------------|
| **Google Translate**| API      |         |         | Fast and stable                            |
| **DeepL**           | API      | ✓       |         | Requires `DEEPL_API_KEY`                   |
| **Gemini**          | API      | ✓       |         | Requires `GEMINI_API_KEY` + Google fallback|
| **Qwen2.5**         | Local    |         | ✓       | 7B Uncensored                              |
| **Dolphin 2.9.1**   | Local    |         | ✓       | Based on Llama-3-8B                        |

### Environment Variables

| Environment Variable | Description              | Notes                          |
|----------------------|--------------------------|--------------------------------|
| `DEEPL_API_KEY`      | DeepL API key            | Required for DeepL             |
| `GEMINI_API_KEY`     | Gemini API key           | Required for Gemini            |
| `HF_TOKEN`           | Hugging Face token       | Needed for diarization (speakers) |

---

## How to Use
1. Open the notebook in Google Colab using the button above
2. Mount Google Drive (if you want to work with files from Drive)
3. Run the cells in order
4. In the interface:
   - Upload audio/video **or** ready-made subtitles
   - Select the Whisper model
   - Choose a translator
   - Specify the target language
   - Optionally add style instructions and a glossary
5. Click **“Start Processing”**

Finished files will appear in the interface and will also be automatically saved to a folder on Google Drive.

---

## Google Drive Folder Structure
After launching the GUI, the notebook automatically creates the following structure:

| Folder                 | Purpose                                              |
|------------------------|------------------------------------------------------|
| `input/`               | Original files to be processed                       |
| `ASMR_transcription/`  | Untranslated files in `.txt` format                  |
| `ASMR_Original/`       | Untranslated files formatted as subtitles            |
| `ASMR_Resultat/`       | Translated subtitles                                 |

Full path:  
`/content/drive/MyDrive/ASMR_ENGINEERING/`

---

### Notes
- If the GUI does not detect your file, add the required format in the **3rd code block** under the `file_types=` and `supported` parameters.
- You can easily add your own local translation model by inserting its name into `AVAILABLE_MODELS`.

---

## Personal Recommendation
Want to translate manga?  
Here’s an excellent tool I can recommend:
- [Open in Google Colab](https://colab.research.google.com/drive/1QCxElEzcapq9Fv25Cu4NjeMVLvkhW60I?usp=sharing)
- [Manga Image Translator Repository](https://github.com/zyddnys/manga-image-translator#online-version)

## Questions and Suggestions
If you have any questions, improvement ideas, or know other useful tools for automatic translation — I’d be very happy to hear them!  
Feel free to create an [Issue](https://github.com/ArisuLoveASMR/ArisuLoveASMR/issues)
