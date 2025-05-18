# Colab Whisper 本地檔語音轉文字

在 Google Colab 直接把音檔丟進左邊 **Files** 面板即可啟動流程：  
自動轉成 16 kHz WAV → 離線 Whisper 辨識（繁體中文）→ 產生 `*.txt` 並自動下載。

---

## 功能特色

- **通吃所有音檔**：MP3、M4A、OGG、WAV… 只要 ffmpeg 能讀就行。  
- **一鍵轉檔**：`pydub` 自動轉 16 kHz、單聲道、16-bit PCM。  
- **離線 Whisper**：tiny~large 任選，不需 API Key，完全離線。  
- **簡體 ➜ 繁體**：辨識結果自動以 OpenCC 轉繁體。  
- **自動匯出**：同名 `*_transcript.txt` 立即下載，亦顯示於 Files 面板。  

---

## 快速使用

1. 於 Colab 開啟 `notebook.ipynb`。  
2. 將音檔拖曳到左側 Files 或從 Google Drive 複製至 `/content/`。  
3. （可選）修改程式中 `src_path`，或保留「自動尋找第一個音檔」。  
4. **Runtime → Run all**。完成後 `.txt` 會自動下載，也可在 Files 面板找到。  

---

## 模型與效能（以 T4 GPU 為例）

| 模型 | 體積 | 速度倍數 | RAM |
|------|------|----------|-----|
| tiny | 41 MB | 100× | 0.5 GB |
| base | 74 MB | 50×  | 1 GB |
| small| 244 MB| 20×  | 2 GB |
| medium|1.4 GB| 10×  | 6 GB |
| large |2.8 GB| 5–8× | 12 GB |

倍數代表相對於「語音長度」的轉錄速度。

---

## 授權

MIT License ©

---

# Colab Whisper Local-File Transcriber

A one-stop Google Colab notebook that **reads any audio file already present in `/content/`** (e.g. drag-and-drop in the Files pane or copy from Google Drive), converts it to 16 kHz mono WAV, runs an **offline Whisper model** for zh-TW transcription, converts Simplified → Traditional Chinese, and exports a UTF-8 TXT transcript that is both auto-downloaded and visible in the Files pane.

---

## Features

| ✔ | Description |
|---|-------------|
| Universal audio input | MP3, M4A, OGG, WAV … anything `ffmpeg` can read. |
| Automatic conversion | 16 kHz · mono · 16-bit PCM WAV via **pydub**. |
| Offline Whisper | Choose `tiny` → `large` models with **no API key**. |
| zh-TW output | OpenCC post-processing for Simplified ➜ Traditional. |
| Auto export & download | Saves `*_transcript.txt`, triggers browser download, and appears in Colab’s Files tree. |

---

## Quick Start

1. **Open** the notebook in Google Colab.  
2. Put your audio file into **`/content/`**  
   - Drag it into the left “Files” sidebar **or** `!cp /path/to/drive/file.mp3 /content/`.  
3. Edit the `src_path` variable in the last code cell **or** keep the default auto-scan.  
4. **Run → Run all**. You’ll get a `.txt` transcript in seconds-to-minutes.

### Example cell

# If you want to hard-code a filename:
src_path = "/content/Foreign - 星期六 16-42 (1).m4a"
Or let the notebook pick the first audio file it sees.

## Model Table (T4 GPU)
| Model  | Size   | \~RTF\* | RAM    |
| ------ | ------ | ------- | ------ |
| tiny   | 41 MB  | 100×    | 0.5 GB |
| base   | 74 MB  | 50×     | 1 GB   |
| small  | 244 MB | 20×     | 2 GB   |
| medium | 1.4 GB | 10×     | 6 GB   |
| large  | 2.8 GB | 5–8×    | 12 GB  |

* RTF = speed-up factor vs. real-time audio length.

## Folder Structure

colab-whisper-localfile/
├─ notebook.ipynb
├─ docs/
│  └─ colab-workflow.png
└─ LICENSE

## License
MIT ©
