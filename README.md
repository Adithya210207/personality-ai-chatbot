# 🎭 Anime Personality AI Chatbot

A feature-rich desktop AI chatbot application built with Python and Tkinter, powered by local LLMs (Ollama) featuring distinct anime character personalities, custom UI themes, real-time streaming, chat history management, and multi-character interaction ("Trio Chat").

---

## 🌟 Key Features

- **Distinct Character Personalities**:
  - 🎤 **Hatsune Miku**: Energetic, musical, supportive vocaloid persona.
  - 💙 **Rem**: Loyal, gentle, and devoted maid persona from Re:Zero.
  - ✨ **Yuhee**: Cheerful, expressive, and engaging AI companion.
  - ⚔️ **Kirito**: Calm, tactical, and determined gamer/swordsman persona from Sword Art Online.
  - ♟️ **Lelouch**: Strategic, dramatic, and intellectual commander persona from Code Geass.
  - 👥 **Trio Chat**: Multi-character interaction hub featuring simultaneous dialogue with Yuhee and Miku.

- **🎨 Modern UI & Customization**:
  - Character-themed visual interfaces with custom avatar banners and dark/light palettes.
  - Adjustable model parameters (Max Tokens, Temperature, Top-P, Repeat Penalty).
  - Maximized and minimized UI display modes.

- **⚡ Local LLM Backend**:
  - Operates locally via **Ollama** (`http://localhost:11434`), ensuring complete privacy and fast local inference.
  - Optimized for **L3-8B-Stheno-v3.2** (or any compatible GGUF/Ollama model).

- **💾 History & Management**:
  - Full chat history retention, export capabilities, and interactive history navigation.

---

## 📁 Repository Structure

```
.
├── Anime_personallity_Ai_chatbox.py    # Main launcher GUI
├── Miku_ai_chatbot.py                  # Hatsune Miku Chatbot interface
├── Rem_ai_Chatbot.py                   # Rem Chatbot interface
├── Yuhee_ai_chatbot.py                 # Yuhee Chatbot interface
├── kirito_ai_chatbot.py                # Kirito Chatbot interface
├── lelouch_ai_chatbot.py               # Lelouch Chatbot interface
├── Trio_chat_yuhee_and_miku.py         # Multi-character Trio Chat GUI
├── Anime_Personality_AI_Chatbox_Logo.ico
├── Documentary/                        # Architecture guides, docs & screenshots
├── requirements.txt                    # Python dependencies
└── README.md                           # Project documentation
```

---

## 🚀 Quick Start

### 1. Prerequisites

- **Python 3.8+**
- **Ollama**: Download and install from [ollama.com](https://ollama.com).

### 2. Setup Local LLM Model

Make sure Ollama is running and load your preferred model (e.g. `L3-8B-Stheno-v3.2`):

```bash
ollama serve
```

*(Refer to `Documentary/Stheno_Ollama_Setup_Guide_for_my_Chatbots_backend (2).pptx` or `Documentary/Modelfile` for Ollama model setup).*

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the Application

Launch the main unified app launcher:

```bash
python Anime_personallity_Ai_chatbox.py
```

Or run any character chatbot individually:

```bash
python Miku_ai_chatbot.py
python Rem_ai_Chatbot.py
python Yuhee_ai_chatbot.py
python kirito_ai_chatbot.py
python lelouch_ai_chatbot.py
python Trio_chat_yuhee_and_miku.py
```

---

## 🛠️ Tech Stack

- **GUI Framework**: Python `tkinter` & `ttk`
- **Image Processing**: `Pillow` (PIL)
- **Local AI Engine**: [Ollama REST API](https://github.com/ollama/ollama)
- **Model**: `L3-8B-Stheno-v3.2` / Llama 3 8B fine-tunes

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
