````md
# AI Lip Sync with Whisper, TTS & Wav2Lip

This project synchronizes lip movements in a video with generated speech audio using AI models like **Whisper**, **TTS**, and **Wav2Lip**. It also supports translation and optional sign-language video generation.

---

## Features

* **Speech Generation:** Converts text or translated text into natural-sounding speech (via [TTS](https://github.com/coqui-ai/TTS)).
* **Speech Recognition:** Uses [Whisper](https://github.com/openai/whisper) to transcribe or translate spoken audio.
* **Lip Synchronization:** Aligns generated or translated audio with lip movements in the target video using [Wav2Lip](https://github.com/Rudrabha/Wav2Lip).
* **Language Translation:** Integrates [Google Translator API](https://pypi.org/project/deep-translator/) for multilingual audio synthesis.
* **Optional Sign Language Output:** Converts speech to basic sign-language video sequences (if configured).

---

## Requirements

* **Python 3.10**
* **GPU (NVIDIA recommended)** for faster processing
* Dependencies listed below:

---

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/ai-lipsync-cpu.git
   cd ai-lipsync-cpu
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

Here’s a tested, stable combination for your working environment:

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

### 4. Setup the Wav2Lip Environment

```bash
cd Wav2Lip
python -m venv venv_wav
venv_wav\Scripts\activate
```

Create `Wav2Lip/requirements.txt`:

```txt
torch==2.2.2
torchvision==0.17.2
numpy==1.23.5
opencv-python==4.9.0.80
dlib==19.24.2
ffmpeg-python==0.2.0
librosa==0.9.2
tqdm==4.66.1
numba==0.56.4
```

Then install:

```bash
pip install -r requirements.txt
```

### 5. Download Pretrained Model

```bash
mkdir checkpoints
```

Download [wav2lip_gan.pth (Google Drive)](https://drive.google.com/file/d/1BXd6BC5_Jg_pAke9U74FY-jBmMUIHZpY/view?usp=drive_link)
and place it in:

```
Wav2Lip/checkpoints/wav2lip_gan.pth
```

### 6. Run Wav2Lip Test (Optional)

```bash
cd Wav2Lip
venv_wav\Scripts\activate
python inference.py \
  --checkpoint_path checkpoints/wav2lip_gan.pth \
  --face "sample.mp4" \
  --audio "sample.wav" \
  --outfile "result.mp4"
```

### 7. Run the Full Project

```bash
cd ..
myenv\Scripts\activate
python app.py
```

Then open the **Gradio** web interface (usually at [http://127.0.0.1:7860](http://127.0.0.1:7860)).

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
| `Slow execution`                       | Enable GPU and use smaller input video |

---

## Demo Files

* Demo Video: [Watch Demo on Google Drive](https://drive.google.com/file/d/1VQG50wmcMo6g5af7uhRa5HzysQldBrqk/view?usp=sharing)
* Input Video: [Watch Input Video on Google Drive](https://drive.google.com/file/d/1iT1uPnZeivwCxRWVi2fG1JOLFEtn2ZLP/view?usp=sharing)
* Output Video: [Watch Output Video on Google Drive](https://drive.google.com/file/d/1-pADari6wTKjQixkJ80k6poHtTY6mYHr/view?usp=sharing)

---

## Author

David
MSc Artificial Intelligence | AI Engineer
[LinkedIn](https://www.linkedin.com/in/david-benjamin-74a1a6280)

---

## License

MIT License © 2025 — Developed by **David Benjamin**

````