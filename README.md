# Voice-Driven AI Assistant — Real-Time Conversational System 🎙️🤖

Imagine speaking naturally to an AI, and it answers you back instantly — no typing, no delay, just conversation. This project is a voice-first, real-time interface to a language model, allowing seamless, two-way spoken interaction with artificial intelligence.

I built this system to experiment with human-like conversation using state-of-the-art voice processing and language modeling.

---

## 🧠 How It Works

This is a modular, streaming-based system engineered for responsiveness and clarity. Here's how a conversation flows:

1. **Mic Input:** The browser listens and sends short chunks of your voice.
2. **Streaming Transport:** Audio is delivered to the backend through WebSockets.
3. **Transcription Engine:** Incoming audio is transcribed to text immediately.
4. **Language Model Response:** The text is processed by a selected AI model to generate a response.
5. **Voice Synthesis:** The reply is converted into audio in real time.
6. **Playback:** Audio is returned and played in the browser without lag.
7. **Interruption Support:** You can interrupt at any time — the system smoothly handles it.

---

## ✨ Core Capabilities

- Fully voice-based interaction — speak freely, listen naturally
- Low-latency speech recognition and synthesis
- Live transcription display as you talk
- Smart turn-taking based on silence detection
- Easily switch AI models or voice engines
- Browser-based client, no extra apps needed
- Docker support for reliable deployment

---

## 🛠️ Technology Overview

**Languages & Frameworks:**

- Python (FastAPI backend)
- JavaScript (Vanilla, Web Audio API on frontend)

**Main Components:**

- Speech-to-text (Realtime Whisper backend)
- AI processing (supports multiple LLMs)
- Text-to-speech (Coqui, Kokoro, Orpheus)
- Audio processing (`numpy`, `scipy`)
- Communication: WebSockets
- Containerized with Docker and Docker Compose

---

## 🧪 System Requirements

- Python 3.9+
- A modern web browser with microphone access
- GPU recommended (CUDA-enabled NVIDIA preferred) for fast STT/TTS
- Docker (optional but simplifies setup)
- Ollama or OpenAI credentials (if using these AI models)

---

## ⚙️ Setup Instructions

### Option 1: Docker Setup

This is the fastest way to get everything running:

```bash
# Build containers
docker compose build

# Start the application
docker compose up -d

# Pull the AI model inside the Ollama container
docker compose exec ollama ollama pull [model-name]
```

Use `docker compose down` to stop, or `docker compose logs -f app` to view logs.

---

### Option 2: Manual Installation

Ideal for development and fine-grained control.

```bash
# Create a virtual environment
python -m venv venv
source venv/bin/activate   # Windows: .\venv\Scripts\activate

# Navigate to the code directory
cd code

# Install dependencies
pip install -r requirements.txt

# Install PyTorch (ensure CUDA version matches if using GPU)
pip install torch torchaudio torchvision
```

To launch:

```bash
python server.py
```

Then open your browser and navigate to the local server address.

---

## 🧰 Customization Guide

You can adapt nearly every part of the system:

- **Voice Engine & Settings:** See `audio_module.py` and `server.py`
- **Language Model Choice:** Configured in `llm_module.py` and `server.py`
- **Prompt Style:** Modify `system_prompt.txt`
- **STT Behavior:** Tweak transcription model and silence thresholds in `transcribe.py`
- **Turn Handling:** Control pause sensitivity in `turndetect.py`
- **Secure Access:** Add HTTPS support with certificates in `server.py`

---

## 🤝 Contribution & Use

This project was created as a personal exploration into voice/AI systems, but feedback, improvements, and forks are welcome. It’s released under the MIT License. Check licensing terms of any third-party components or models you integrate.
