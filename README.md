
---

````md
# AI Lip Sync with Whisper, TTS & Wav2Lip

This project synchronizes lip movements in a video with generated speech audio using AI models like **Whisper**, **TTS**, and **Wav2Lip**.  
It also supports translation and optional sign-language video generation.

---

## Features

- **Speech Generation:** Converts text or translated text into natural-sounding speech using [TTS](https://github.com/coqui-ai/TTS).
- **Speech Recognition:** Uses [Whisper](https://github.com/openai/whisper) to transcribe or translate spoken audio.
- **Lip Synchronization:** Aligns generated or translated audio with lip movements in the target video using [Wav2Lip](https://github.com/Rudrabha/Wav2Lip).
- **Language Translation:** Integrates [Google Translator API](https://pypi.org/project/deep-translator/) for multilingual audio synthesis.
- **Optional Sign Language Output:** Converts speech to basic sign-language video sequences (if configured).
- **GPU Support:** Automatically uses CUDA when available for faster inference.

---

## Requirements

- **Python 3.10**
- **GPU (NVIDIA recommended)** for faster processing
- Dependencies listed below

---

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/ai-lipsync.git
   cd ai-lipsync
````

2. **Create and activate a virtual environment**

   ```bash
   python -m venv venv
   venv\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

---

## Example `requirements.txt`

Below is a tested and stable combination for your working environment:

```txt
torch==2.4.1
torchaudio==2.4.1
moviepy==1.0.3
numpy==1.22.0
scipy==1.11.2
pandas==1.5.3
pillow==10.3.0
gradio==4.44.0
tts==0.21.1
deep-translator==1.11.4
whisper==1.1.10
ffmpeg-python==0.2.0
transformers==4.36.2
huggingface-hub==0.19.4
```

---

## Run the App

```bash
python app.py
```

Then open the **Gradio** web interface in your browser:

```
http://127.0.0.1:7860
```

---

## Example Workflow

1. Upload or record a video (face visible).
2. Enter text or upload an audio file.
3. Select a translation language (optional).
4. Click **Generate** — your lip-synced output appears below.

---

## Output Files

| File                         | Description                           |
| ---------------------------- | ------------------------------------- |
| `output_synth.wav`           | Generated or translated speech audio  |
| `output_synth_converted.wav` | Audio resampled to 16 kHz for Wav2Lip |
| `lip_synced_video.mp4`       | Final output with lip-sync            |
| `sign_output.mp4`            | Generated sign-language animation     |

---

## GPU Check

If you have CUDA installed, the script automatically detects it:

```python
import torch
print("GPU Available:", torch.cuda.is_available())
```

---

## Models Used

| Component          | Model            | Library         |
| ------------------ | ---------------- | --------------- |
| Speech Recognition | Whisper          | OpenAI          |
| Speech Synthesis   | XTTS / TTS       | Coqui-AI        |
| Lip Sync           | Wav2Lip          | Rudrabha et al. |
| Translation        | GoogleTranslator | Deep Translator |

---

## Troubleshooting

| Issue                                  | Solution                               |
| -------------------------------------- | -------------------------------------- |
| `PIL.Image has no attribute ANTIALIAS` | Install Pillow 10.3.0                  |
| `numpy version conflict`               | Use `numpy==1.22.0` for TTS            |
| `FileNotFoundError [WinError 2]`       | Ensure `ffmpeg` is in PATH             |
| `CUDA not used`                        | Check `torch.cuda.is_available()`      |
| `Slow execution`                       | Enable GPU and use smaller input video |

---

## Author

**David Benjamin**
MSc Artificial Intelligence | AI Engineer
[LinkedIn](https://www.linkedin.com/in/david-benjamin-74a1a6280)

---

## License

MIT License © 2025 — Developed by **David Benjamin**

```