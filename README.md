
# 📝 Meeting Minutes Generator

A Python-based AI tool that automatically generates structured meeting minutes from audio recordings using state-of-the-art speech recognition and large language models.

## 🚀 Features

- 🎙️ **Speech-to-Text** transcription using OpenAI Whisper and Hugging Face Transformers.
- 🧠 **AI-powered summarization** of meeting transcripts into:
  - Summary (with location, attendees, and date)
  - Key discussion points
  - Takeaways
  - Action items with responsible parties
- 🖥️ **Gradio web interface** for uploading `.mp3` or `.wav` files and receiving markdown-formatted outputs.
- ⚡ Uses efficient 4-bit quantized models for low memory usage and fast performance.

## 🛠️ Installation

Make sure you have Python 3.8+ and `pip` installed.

Install the required packages:

```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu124
pip install requests bitsandbytes transformers accelerate openai librosa gradio
```

> Note: GPU with CUDA support is recommended for best performance.

## 🎧 How It Works

1. Upload a meeting audio file (`.mp3` or `.wav`).
2. The audio is transcribed using OpenAI's Whisper or Hugging Face's speech-to-text models.
3. The transcript is passed to a chat-based language model (e.g., Qwen2-7B-Instruct) that generates well-formatted meeting minutes in markdown.
4. Output includes summaries, key points, and action items.

## 📦 Models Used

- `openai/whisper-medium` and `whisper-1` for transcription
- `Qwen/Qwen2-7B-Instruct` for generating structured summaries
- Quantized via `BitsAndBytes` for efficient inference

## 💡 Example Output

```markdown
### Summary
- **Date**: July 10, 2025
- **Location**: Denver Council Hall
- **Attendees**: Council Members A, B, C...

### Key Discussion Points
- Budget allocation for 2025 projects
- Public transport expansion proposal

### Takeaways
- Final budget draft to be approved by next session

### Action Items
- [ ] Prepare budget revisions — **John D.**
- [ ] Collect public feedback — **Sarah L.**
```

## 🌐 Interface

The app uses **Gradio** for a simple, user-friendly interface:

```python
gr.Interface(...).launch()
```

You can upload your audio, and get markdown-formatted meeting notes instantly.

## 📁 File Structure

- `meeting_minutes.py`: Main application logic
- `/content/denver_extract.mp3`: Example input (user-supplied)

## 🧠 Notes

- Requires OpenAI API key if using Whisper-1 (set via Google Colab's `userdata`).
- Ensure your GPU has sufficient VRAM (>= 12GB recommended).

