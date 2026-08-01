<div align="center">
 
  # ArisuLoveASMR
 [Русский](README.md) | [English](README_EN.md) | 简体中文
 
  用于自动生成字幕并无审查地翻译成任何语言的 Google Colab 笔记本
 
  [![Colab](https://img.shields.io/badge/Open%20in%20Colab-orange?logo=googlecolab)](https://colab.research.google.com/github/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)
  [![Notebook](https://img.shields.io/badge/Jupyter%20Notebook-100%25-lightgrey)](https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/ArisuLoveASMR.ipynb)
</div>
<img width="1612" height="908" alt="forasmr" src="https://github.com/ArisuLoveASMR/ArisuLoveASMR/blob/main/screenshots/forasmr.png" />

---

## 简介
**ArisuLoveASMR** 是一款方便的 Google Colab 笔记本，带有图形界面，支持：
- 自动识别任何 ASMR 音频和视频中的语音
- 生成 SRT、VTT、LRC 格式的字幕
- 分配说话人
- 无审查地翻译成任何语言
- 同时处理多个文件

---

## 从哪里获取 ASMR 以及如何使用字幕
为了更方便地使用，推荐：
- **[KikoFlu](https://github.com/pa-jesusf/KikoFlu)** — 方便下载 ASMR 并将 ASMR 和字幕加载到播放器中的工具
- **[asmr.one](https://asmr.one)** — 目前不使用亚洲 VPS 无法正常访问 asmr.one。可通过 [KikoFlu](https://github.com/pa-jesusf/KikoFlu) 绕过此限制

## 功能

### 语音识别
- **WhisperX**（模型：`large-v3`、`large-v3-turbo`、`distil-large-v3`、`large-v2`、`medium`）
- VAD 过滤器，实现更优的分段
- 可调节 Beam Search
- 说话人分离（Diarization）——可开启/关闭
- 支持大量音频和视频格式
- 防止 Gemini 返回空结果：当触发审查时，自动切换到 Google Translate

### 翻译
支持多种翻译方式：

| 翻译器              | 类型     | API Key | 离线 | 备注                                       |
|---------------------|----------|---------|------|--------------------------------------------|
| **Google Translate**| API      |         |      | 快速且稳定                                 |
| **DeepL**           | API      | ✓       |      | 需要 `DEEPL_API_KEY`                       |
| **Gemini**          | API      | ✓       |      | 需要 `GEMINI_API_KEY` + 回退到 Google      |
| **Qwen2.5**         | 本地     |         | ✓    | 7B 无审查版本                              |
| **Dolphin 2.9.1**   | 本地     |         | ✓    | 基于 Llama-3-8B                            |

### 环境变量

| 环境变量             | 说明                     | 备注                           |
|----------------------|--------------------------|--------------------------------|
| `DEEPL_API_KEY`      | DeepL API 密钥           | DeepL 必需                     |
| `GEMINI_API_KEY`     | Gemini API 密钥          | Gemini 必需                    |
| `HF_TOKEN`           | Hugging Face 令牌        | 用于说话人分离（Diarization）  |

---

## 使用方法
1. 通过上方按钮在 Google Colab 中打开笔记本
2. 挂载 Google Drive（如果想使用 Drive 中的文件）
3. 按顺序运行单元格
4. 在界面中：
   - 上传音频/视频 **或** 已有字幕
   - 选择 Whisper 模型
   - 选择翻译器
   - 指定目标语言
   - 如有需要可添加风格说明和术语表
5. 点击 **「开始处理」**

处理完成的文件会显示在界面中，并自动保存到 Google Drive 的文件夹中。

---

## Google Drive 文件夹结构
启动 GUI 后，笔记本会自动创建以下结构：

| 文件夹                 | 用途                                               |
|------------------------|----------------------------------------------------|
| `input/`               | 待处理的原始文件                                   |
| `ASMR_transcription/`  | 未翻译的 `.txt` 格式文件                           |
| `ASMR_Original/`       | 未翻译但已转换为字幕格式的文件                     |
| `ASMR_Resultat/`       | 已翻译的字幕                                       |

完整路径：  
`/content/drive/MyDrive/ASMR_ENGINEERING/`

---

### 注意事项
- 如果 GUI 无法识别你的文件，请在**第 3 个代码块**的 `file_types=` 和 `supported` 参数中添加所需格式。
- 你可以轻松添加自己的本地翻译模型，只需将其名称写入 `AVAILABLE_MODELS` 即可。

---

## 个人推荐
想翻译漫画吗？  
推荐一个优秀的工具：
- [在 Google Colab 中打开](https://colab.research.google.com/drive/1QCxElEzcapq9Fv25Cu4NjeMVLvkhW60I?usp=sharing)
- [Manga Image Translator 仓库](https://github.com/zyddnys/manga-image-translator#online-version)

## 问题与建议
如果你有任何问题、改进建议，或者知道其他有用的自动翻译工具，非常欢迎告诉我！  
请创建 [Issue](https://github.com/ArisuLoveASMR/ArisuLoveASMR/issues)
