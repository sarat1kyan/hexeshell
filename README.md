# HEXESHELL

> **AI-Powered Terminal Assistant for Linux**  
> *Speak or type your way through powerful system operations—offline or with ChatGPT.*  

![hexeshell-banner](https://github.com/user-attachments/assets/18cf0f6e-119e-4467-b700-f323eb03a6e9)

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="MIT License"></a>
  <img src="https://img.shields.io/badge/version-0.3.7.a-blue.svg" alt="Version 0.3.7.a">  <a href="https://discord.gg/3GUEXHmTKc">
  <img src="https://img.shields.io/discord/1377434810863321170?color=blue&label=chat&logo=discord" alt="Discord"></a>
  <img src="https://img.shields.io/badge/status-alpha-orange?style=flat-square" alt="Project Status: Alpha">
</p>

## ⚠️ **Note:** HEXESHELL is currently in **Alpha**. Expect rapid changes, incomplete features, and frequent updates. We welcome feedback and contributors!

---
## 🎯 What is HEXESHELL?

HEXESHELL is a smart, voice-ready terminal assistant that understands natural language—locally or through ChatGPT.  
Manage your Linux system, debug scripts, send messages, or explore logs, just by talking or typing.

> 💡 It’s like your terminal grew a brain (and a microphone).

---

## 🔥 Features at a Glance

### 🧠 Smart & Flexible
- Local command parsing for security & speed
- ChatGPT/Gemini fallback for reasoning & debugging

### 🗣️ Voice Control
- SoX-based voice input with CLI fallback

### ⚙️ System Mastery
- Monitor system health, manage packages, network, power

### 🔌 Plugin Architecture
- Drop-in Python/Shell plugins
- Autoloaded with hot-reload roadmap

---

## ⚙️ Installation

### Prerequisites

Ubuntu/Debian:
```bash
sudo apt install sox python3-pip
pip install -r requirements.txt
```

Arch-based:
```bash
sudo pacman -S sox python-pip
pip install -r requirements.txt
```

### Quick Setup

```bash
git clone https://github.com/sarat1kyan/hexeshell.git
cd hexeshell
./install.sh
```

### Docker

```bash
docker run -it --rm sarat1kyan/hexeshell
```

---

## 🧠 Usage Examples

```bash
hexeshell                      # Launch assistant
hexeshell --voice             # Start with voice
hexeshell "find large files"  # Run intelligent task
```

---

## 💡 Command Ideas

| 💬 Type        | 🧠 Example                                               |
|----------------|----------------------------------------------------------|
| System Check   | “Show CPU and memory usage”                              |
| File Ops       | “Delete large files in /Downloads”                       |
| Packages       | “Install neofetch and htop”                              |
| Networking     | “Restart Wi-Fi and check connection speed”               |
| Logs           | “Tail last 100 lines of journalctl”                      |
| Scripting Help | “Fix this Python error in script.py”                     |
| Messaging      | “Tell Rudo ‘Avoz gonna call us soon’ on WhatsApp”              |
| Audio/Media    | “Play lofi beats from Liked playlist in Spotify”         |

---

## 🏗️ Architecture

```
             +-----------------------------+
             |     Natural Language UI     |
             |      (CLI / Voice)          |
             +--------------+--------------+
                            |
                 +----------v----------+
                 | Command Interpreter |
                 +----------+----------+
                            |
             +--------------v--------------+
             |     Action Dispatch Layer   |
             +--+-----------+-------------++
                |           |              |
      +---------v+   +------v-----+   +----v------+
      | SystemAPI |   | AI Modules |   | Plugins  |
      +-----------+   +------------+   +----------+
```

- **SystemAPI**: Safe, permission-aware access to OS commands.
- **AI Modules**: For reasoning, explanation, and response generation.
- **Plugins**: Modular scripts and integrations.

---

## 🧩 Create Your Plugin

Browse: [Community Plugins](https://github.com/search?q=repo%3Asarat1kyan%2Fhexeshell+path%3Amodules&type=code)

```python
# modules/uptime.py
trigger = ["uptime"]
description = "Report system uptime"

def handle(input_text):
    import subprocess
    return subprocess.getoutput("uptime -p")
```

- Save in `modules/`
- Tested with `pytest`
- Auto-loads at launch

---

## 🛠️ Configuration

Edit `~/.config/hexeshell/config.yaml`:

```yaml
voice_enabled: true
use_openai: true
openai_api_key: "your-key"
language: en
```

---

## 🧩 Troubleshooting

| Issue                  | Fix                                           |
|------------------------|-----------------------------------------------|
| `sox` missing          | Install: `sudo apt install sox`              |
| No mic detected        | Use `--no-voice` or check input device       |
| Plugin fails           | Inspect logs in `~/.hexeshell/logs/`         |
| OpenAI key missing     | Add to YAML or `export OPENAI_API_KEY=...`   |

---

## 🗺️ Roadmap

| Feature                     | Status | ETA     | Priority |
|-----------------------------|--------|---------|----------|
| Local NLP Parser            | ✅     | Done    | High     |
| Voice CLI                   | ✅     | Done    | High     |
| Plugin System               | ✅     | Done    | High     |
| Auto-updater                | ✅     | Done    | High     |
| LLM Fine-tuning             | 🛠️     | Q3 2025 | High     |
| Desktop GUI                 | 🛠️     | Q4 2025 | Medium   |
| Community Plugins           | 🛠️     | Q1 2026 | Medium   |
| Web Dashboard               | 🛠️     | Q2 2026 | Low      |
| Mobile/WebSocket Support    | 🛠️     | Q3 2026 | Medium   |

📍 [Track development](https://github.com/sarat1kyan/hexeshell/projects/1)

---

## 🤝 Contributing

1. Fork the repo  
2. Branch out: `feature/my-feature`  
3. Commit with context  
4. Open a pull request

📘 See [`CONTRIBUTING.md`](CONTRIBUTING.md)

---

## 🌐 Join the Community

- 💬 [Discord](https://discord.gg/3GUEXHmTKc)
- 🐦 [@hexeshell](https://twitter.com/hexeshell)
- 🌍 [hexeshell.com](https://hexeshell.com)
- 🪲 [Submit an Issue](https://github.com/sarat1kyan/hexeshell/issues)

---

## 🏷️ Tags

bash assistant, ai terminal, linux voice, devops ai, openai shell, cli automation, hybrid agent
