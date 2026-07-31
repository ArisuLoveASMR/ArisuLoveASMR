<div align="center">
 
  # ArisuLoveASMR
  [Русский](README.md) | [English](README_EN.md) | 简体中文
 
  用于自动生成字幕并将其翻译成任何语言的 Google Colab 笔记本
 
  [![Colab](https://img.shields.io/badge/Open%20in%20Colab-orange?logo=googlecolab)](https://colab.research.google.com/github/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR_ZH.ipynb)
  [![Notebook](https://img.shields.io/badge/Jupyter%20Notebook-100%25-lightgrey)](https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR_ZH.ipynb)
</div>

<img width="1612" height="908" alt="forasmr" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/forasmr.png" />

---

## 简介

**ArisuLoveASMR** 是一款方便的 Google Colab 笔记本，带有图形界面，可以：

- 自动识别 ASMR 音频和视频中的语音
- 生成高精度字幕
- 将字幕翻译成任何语言
- 同时支持媒体文件和已有字幕文件

---

## 从哪里获取 ASMR 和字幕

推荐使用以下工具：

- **[KikoFlu](https://github.com/pa-jesusf/KikoFlu)** — 方便的 ASMR 下载和字幕上传工具
- **[asmr.one](https://asmr.one)** 

---

## 功能特点

### 语音识别
- **WhisperX**（支持模型：`large-v3`、`large-v3-turbo`、`distil-large-v3`、`large-v2`、`medium`）
- VAD 过滤器，提升分段效果
- Beam Search 参数调节
- 说话人分离（Diarization）——可开启/关闭
- 支持大量音频和视频格式

### 翻译

支持多种翻译方式：

| 翻译器               | 类型     | API Key | Offline | 说明                                           |
|----------------------|----------|---------|---------|------------------------------------------------|
| **Google Translate** | API      |         |         | 快速稳定                                       |
| **DeepL**            | API      | ✓       |         | 需要 `DEEPL_API_KEY`                           |
| **Gemini**           | API      | ✓       |         | 需要 `GEMINI_API_KEY`，失败时自动回退到 Google |
| **Qwen2.5**          | 本地     |         | ✓       | 7B Uncensored                                  |
| **Dolphin 2.9.1**    | 本地     |         | ✓       | 基于 Llama-3-8B                                |

### 环境变量

| 环境变量           | 说明                     | 备注                         |
|--------------------|--------------------------|------------------------------|
| `DEEPL_API_KEY`    | DeepL API 密钥           | DeepL 必需                   |
| `GEMINI_API_KEY`   | Gemini API 密钥          | Gemini 必需                  |
| `HF_TOKEN`         | Hugging Face Token       | 说话人分离功能需要           |

### 使用便利性
- 美观的 Gradio 界面
- 支持 Google Drive 文件夹
- 支持多文件上传

---

## 使用方法

1. 点击上方按钮在 Google Colab 中打开笔记本
2. 连接 Google Drive（如果需要使用云盘文件）
3. 按顺序运行单元格
4. 在界面中：
   - 上传音频/视频 **或** 已有字幕
   - 选择 Whisper 模型
   - 选择翻译器
   - 选择目标语言
   - 可选择添加翻译风格和术语表
5. 点击 **「开始处理」**

完成后，文件会显示在界面中，并自动保存到 Google Drive 对应文件夹。

---

## Google Drive 文件夹结构

启动 GUI 后，笔记本会自动创建以下结构：

| 文件夹                   | 用途                                       |
|--------------------------|--------------------------------------------|
| `input/`                 | 待处理的原始文件                           |
| `ASMR_transcription/`    | 未翻译的 `.txt` 文本文件                   |
| `ASMR_Original/`         | 未翻译但已转换为字幕格式的文件             |
| `ASMR_Resultat/`         | 已翻译的字幕文件                           |

完整路径：  
`/content/drive/MyDrive/ASMR_ENGINEERING/`

---
### 注意事项

- 如果 GUI 无法识别您的文件，请在**第 3 个代码块**中的 `file_types=` 和 `supported` 参数里添加所需格式。
- 您可以轻松添加自己的本地翻译模型，只需将其名称插入到 `AVAILABLE_MODELS` 中。

---

## 个人推荐

想翻译漫画吗？  
推荐这个优秀的工具：

- [在 Google Colab 中打开](https://colab.research.google.com/drive/1QCxElEzcapq9Fv25Cu4NjeMVLvkhW60I?usp=sharing)
- [Manga Image Translator 仓库](https://github.com/zyddnys/manga-image-translator#online-version)

---

## 问题与建议

如果您有任何问题、改进建议，或者知道其他有用的自动翻译工具，非常欢迎告诉我！

请提交 [Issue](https://github.com/ArisuLoveASMR/ArisuLoveASMR/issues)
