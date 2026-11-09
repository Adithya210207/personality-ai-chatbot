# 🎭 Anime Personality AI Chatbot

A feature-rich desktop AI chatbot application built with Python and Tkinter, powered by local LLMs (Ollama) featuring distinct anime character personalities, custom UI themes, real-time streaming, chat history management, and multi-character interaction ("Trio Chat").

---

## 🌟 Key Features

- **Distinct Character Personalities**:
  - 🎤 **Miku Nakano**: Shy, loyal, supportive persona.
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
  - Runs on the GPU through Ollama's built-in **Vulkan** backend, including Intel Arc integrated graphics.
  - Optimized for **L3-8B-Stheno-v3.2** (Q8_0), pulled straight from Hugging Face with one `ollama pull`.

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
- **Ollama**: install the official build with `winget install Ollama.Ollama`, or download it from [ollama.com](https://ollama.com).
- About **10 GB** of free disk space for the model.

### 2. Turn On Intel Arc GPU Support (Intel integrated graphics only)

By default, Ollama finds an Intel integrated GPU such as the Arc 140V **but skips it** and runs on the CPU. Run this once in PowerShell. The settings are saved permanently:

```powershell
$vars = "OLLAMA_IGPU_ENABLE",          # use the integrated GPU
        "OLLAMA_VULKAN",               # Vulkan GPU backend
        "GGML_VK_DISABLE_COOPMAT",     # prevents garbled output on Arc 140V
        "GGML_VK_DISABLE_COOPMAT2",
        "OLLAMA_MAX_LOADED_MODELS"     # one model in memory at a time
$vars | ForEach-Object { [Environment]::SetEnvironmentVariable($_, "1", "User") }
```

Then quit Ollama from the system tray and reopen PowerShell. NVIDIA and AMD discrete GPUs don't need this step.

### 3. Pull the Stheno Model

Download Stheno straight from Hugging Face (~8.5 GB), then give it the short name `stheno` that every character uses:

```powershell
ollama pull hf.co/bartowski/L3-8B-Stheno-v3.2-GGUF:Q8_0
ollama cp hf.co/bartowski/L3-8B-Stheno-v3.2-GGUF:Q8_0 stheno
```

No manual GGUF download or Modelfile is needed. `ollama cp` only adds a second name, so it doesn't use extra disk space. For a smaller download, replace `:Q8_0` with `:Q6_K` (~6.6 GB) or `:Q4_K_M` (~4.9 GB), in both commands.

Check it's running on the GPU:

```powershell
ollama run stheno "Say hello in one sentence."
ollama ps        # PROCESSOR should read 100% GPU
```

*(The full walkthrough is in `Documentary/Stheno_Ollama_Setup_Guide_for_my_Chatbots_backend (2).pptx`.)*

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Run the Application

Launch the main unified app launcher. It starts Ollama automatically if it isn't already running:

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

## 🩺 Troubleshooting

| Problem | Fix |
|---|---|
| Characters reply with scrambled characters | The model file is probably damaged. Run `ollama rm stheno` and `ollama rm hf.co/bartowski/L3-8B-Stheno-v3.2-GGUF:Q8_0`, then repeat step 3. `ollama pull` checks the download, so a fresh pull fixes it. |
| `ollama ps` shows CPU instead of 100% GPU | Set `OLLAMA_IGPU_ENABLE=1` (step 2), then quit and restart Ollama. |
| "model 'stheno' not found" | Run the `ollama cp … stheno` command from step 3. |
| `ollama ps` shows only ~1.5 GB | Normal on GPUs that share system memory. Check **Task Manager → Performance → GPU → Shared GPU memory** for the real figure. |

---

## 🛠️ Tech Stack

- **GUI Framework**: Python `tkinter` & `ttk`
- **Image Processing**: `Pillow` (PIL)
- **Local AI Engine**: [Ollama REST API](https://github.com/ollama/ollama), GPU-accelerated through Vulkan
- **Model**: `L3-8B-Stheno-v3.2` Q8_0 (`hf.co/bartowski/L3-8B-Stheno-v3.2-GGUF:Q8_0`), a Llama 3 8B fine-tune

---

## 📄 Copyright & Terms of Use

**© 2026 Adithya V. All Rights Reserved.**

This repository is published for portfolio, demonstration, and educational viewing purposes only. You are welcome to view the source code to understand the implementation.

### You may NOT:

- Copy or reproduce substantial portions of this project.
- Redistribute, republish, or mirror this repository.
- Use this code in commercial projects without prior written permission.
- Submit this code, or substantially similar code, as your own for academic purposes.
- Remove copyright notices or claim this work as your own.

If you would like to use any part of this project, please contact me first for permission.
