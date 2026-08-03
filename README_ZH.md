<div align="center">

# ArisuLoveASMR

[Русский](README.md) | [English](README_EN.md) | 简体中文

用于自动生成字幕并翻译成任意语言的 Google Colab 笔记本，**无审查**

[![Colab](https://img.shields.io/badge/Open%20in%20Colab-orange?logo=googlecolab)](https://colab.research.google.com/github/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)
[![Notebook](https://img.shields.io/badge/Jupyter%20Notebook-100%25-lightgrey)](https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)

</div>

<img width="1612" height="908" alt="forasmr" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/forasmr.png" />

---

## 简介

**ArisuLoveASMR** 是一款带图形界面的 Google Colab 笔记本，可以：

- 自动识别 ASMR 音频和视频中的语音
- 生成 **SRT / VTT / LRC** 格式字幕
- 识别说话人，并通过 **Groq** **自动命名**
- 翻译成任意语言，**无审查**
- 既可处理媒体文件，也可直接处理现成字幕
- 一次处理多个文件（包括来自 Google Drive 文件夹的文件）

---

## ASMR 从哪里获取，字幕往哪里放

为方便使用，推荐：

- **[KikoFlu](https://github.com/pa-jesusf/KikoFlu)** — 方便下载 ASMR，并把文件/字幕导入播放器
- **[asmr.one](https://asmr.one)** — 目前没有亚洲 VPS 较难使用；可通过 [KikoFlu](https://github.com/pa-jesusf/KikoFlu) 绕过此限制

---

## 功能

### 语音识别

- **WhisperX**（模型：`large-v3`、`large-v3-turbo`、`distil-large-v3`、`large-v2`、`medium`）
- VAD 过滤，提升分段效果
- 可配置 Beam Search
- 说话人分离（Diarization）— 可开可关
- 通过 **Groq** 自动命名说话人
- 支持大量音频和视频格式
- 可直接上传现成字幕（`.srt` / `.vtt` / `.lrc`）并翻译

### 翻译

| 翻译器 | 类型 | API Key | 离线 | 说明 |
|------------------------------|-----------|----------|---------|----------------------------------------------|
| **Google Translate** | API | | | 快速稳定 |
| **DeepL** | API | ✓ | | 需要 `DEEPL_API_KEY` |
| **Gemini** | API | ✓ | | 需要 `GEMINI_API_KEY`，失败时回退到 Google |
| **Groq (Llama 3.3 70B)** | API | ✓ | | 需要 `GROQ_API_KEY` |
| **Groq (Qwen 3.6 27B)** | API | ✓ | | 需要 `GROQ_API_KEY` |
| **Qwen2.5** | 本地 | | ✓ | 7B Uncensored（可能占用大量显存） |
| **Dolphin 2.9.1** | 本地 | | ✓ | 基于 Llama-3-8B（可能占用大量显存） |

额外功能：

- 翻译风格说明
- 术语表（格式：`原文 = 译文`）
- Gemini 空回复保护：遇到审查时自动切换到 Google 翻译
- 说话人名字会适配所选目标语言

> ⚠️ 不建议在 Colab T4 上使用本地模型：显存不足风险很高。优先使用 API（Google / DeepL / Gemini / Groq）。

---

### 示例

<img width="1612" height="908" alt="kikoflu" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/screenshots_kikoflu.png" />

*来自 [KikoFlu](https://github.com/pa-jesusf/KikoFlu) 播放器的截图，字幕由本笔记本生成并导入*

---

## 环境变量

| 变量 | 说明 | 备注 |
|------------------|-------------------------------|------------------------------------------|
| `HF_TOKEN` | Hugging Face 令牌 | 说话人分离（Diarization）需要 |
| `DEEPL_API_KEY` | DeepL API 密钥 | DeepL 必需 |
| `GEMINI_API_KEY` | Gemini API 密钥 | Gemini 必需 |
| `GROQ_API_KEY` | Groq API 密钥 | Groq 翻译和说话人命名需要 |

获取方式：

- HF_TOKEN → [huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)  
  （并接受 [pyannote/speaker-diarization-community-1](https://huggingface.co/pyannote/speaker-diarization-community-1) 的使用条款）
- DEEPL_API_KEY → [deepl.com/pro-api](https://www.deepl.com/pro-api)
- GEMINI_API_KEY → [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
- GROQ_API_KEY → [console.groq.com/keys](https://console.groq.com/keys)

---

## 使用方法

1. 通过上方按钮在 Google Colab 中打开笔记本
2. 选择 GPU：**运行时 → 更改运行时类型 → T4**
3. 按顺序运行单元格
4. 填入所需的 API 密钥
5. 连接 Google Drive（如果要从网盘读取文件）
6. 在界面中：
   - 上传音频/视频 **或** 现成字幕
   - 选择 Whisper 模型
   - 开启/关闭说话人分离与命名
   - 选择翻译器和目标语言
   - 如需可添加风格说明和术语表
7. 点击 **「开始处理」**

完成后文件会出现在界面中，并保存到 Google Drive。

---

## Google Drive 文件夹结构

启动 GUI 后会自动创建：

| 文件夹 | 用途 |
|------------------------|--------------------------------------------------------|
| `input/` | 待处理的原始文件 |
| `ASMR_transcription/` | 未翻译的转写文本（`.txt`） |
| `ASMR_Original/` | 未翻译、但已整理为字幕格式的文件 |
| `ASMR_Resultat/` | 已翻译的字幕 |

完整路径：

`/content/drive/MyDrive/ASMR_ENGINEERING/`

---

### 注意事项

- 如果 GUI 识别不到你的文件，请在 **第 3 个代码单元格** 的 `file_types=` 和 `supported` 参数中添加对应格式。
- 你可以轻松添加自己的本地翻译模型，只需把模型名称写入 `AVAILABLE_MODELS`。

---

## 个人推荐

想翻译漫画吗？

推荐这个工具：

- [在 Google Colab 中打开](https://colab.research.google.com/drive/1QCxElEzcapq9Fv25Cu4NjeMVLvkhW60I?usp=sharing)
- [Manga Image Translator 仓库](https://github.com/zyddnys/manga-image-translator#online-version)

## 问题与建议

如果你有问题、改进建议，或知道其他有用的自动翻译工具 — 非常欢迎告诉我！

请创建 [Issue](https://github.com/ArisuLoveASMR/ArisuLoveASMR/issues)
