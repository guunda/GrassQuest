# 🌿 GrassQuest AI — Hacktoberfest 2026 "Touch Grass"

> **"Touch Grass. Literally."**  
> *A privacy-first, offline-capable outdoor quest generator powered by local open-weight AI.*

---

## 📌 Project Concept

**GrassQuest AI** is a privacy-first outdoor activity generator built specifically for the **Hacktoberfest 2026 "Touch Grass"** challenge.

The goal is simple:  
Use open-source and open-weight AI to encourage people to spend **LESS time on their screens** and **MORE time outdoors** in nature.

Unlike conventional AI tools that draw users deeper into infinite screen scrolling and digital chats, **GrassQuest AI** uses AI as a brief launchpad. It generates a personalized real-world micro-quest (e.g., 20 minutes of nature observation or a mindful walking walk) and then **explicitly instructs you to put your phone away and step outside**.

The AI interaction is the shortest part of your experience.

---

## 🎯 The Problem & Solution

### The Problem
Modern AI applications and social media platforms are optimized for screen retention, endless doomscrolling, and perpetual device engagement, leading to digital fatigue and disconnect from physical nature.

### The Solution
GrassQuest AI inverts the modern app paradigm:
1. **Input**: Select your available time (e.g., 10m, 20m, 30m, 1h), activity type, and environment.
2. **Generate**: A local open-weight AI model generates 2–4 safe, actionable outdoor observation objectives.
3. **Touch Grass**: Prominent UX banners tell you **"📱 PUT YOUR PHONE AWAY 🌳 GO TOUCH GRASS"**.
4. **Disconnect & Explore**: Pocket your phone, head outside, run the countdown timer, and earn **Grass Points** upon completion.

---

## 🚀 Core Features

- 🟢 **Local Open-Weight AI Core**: Runs 100% locally using [Ollama](https://ollama.com/) (e.g., `gemma3:4b`, `gemma:2b`, `llama3.2:1b`, `mistral`).
- 🔒 **Privacy-First Architecture**: Zero external API calls, zero server-side user tracking.
- ✈️ **Offline Capable**: Works without an active internet connection once dependencies and model are downloaded.
- 📱 **Screen-Free UX Focus**: Explicit banners and notifications encouraging users to pocket their devices.
- ⏱️ **Interactive Outdoor Quest Timer**: Built-in countdown timer with pause/resume and quick finish.
- 🎉 **Grass Points & Level Progression**:
  - `0 – 499 pts`: 🌱 **Seedling**
  - `500 – 999 pts`: 🌿 **Explorer**
  - `1000 – 1999 pts`: 🌳 **Nature Walker**
  - `2000+ pts`: 🌲 **Grass Master**
- 📊 **Local Quest History**: Tracks completed outdoor minutes and past missions strictly inside browser `LocalStorage`.
- 🟡 **Hackathon Demo Mode**: Built-in simulated local AI toggle so judges can test the full app experience instantly even if Ollama is not installed!

---

## 🛠️ Technology Stack

| Layer | Technology | Purpose |
| :--- | :--- | :--- |
| **Frontend** | React 18 + Vite | Fast, modern, responsive UI |
| **Icons** | Lucide React | Nature-inspired clean vector icons |
| **Styling** | Vanilla CSS Design System | Glassmorphism, custom tokens, zero heavy frameworks |
| **Backend** | Python + FastAPI | High-performance async API server |
| **Local AI** | Ollama API | Inference engine for open-weight models |
| **Storage** | Browser `LocalStorage` | Zero-tracking local data persistence |

---

## 📐 System Architecture

```mermaid
flowchart TD
    User([👤 User]) -->|1. Select Time & Activity| ReactUI[🌿 React + Vite Frontend]
    ReactUI -->|2. POST /generate-quest| FastAPI[⚡ FastAPI Backend]
    FastAPI -->|3. Local HTTP API| Ollama[🦙 Ollama Local Engine]
    Ollama -->|4. Inference| Model[🤖 Gemma / Open-Weight AI]
    Model -->|5. Structured JSON| FastAPI
    FastAPI -->|6. Quest Payload| ReactUI
    ReactUI -->|7. "📱 Put Phone Away"| User
    User -->|8. Go Outdoors & Touch Grass| Outdoor[🌳 Physical Nature]
```

---

## 🔓 Why Open Innovation Matters

In an era dominated by centralized, proprietary cloud AI APIs, **GrassQuest AI** stands for open innovation:

1. **User Privacy**: Your outdoor habits, location context, and routine are never transmitted to third-party ad networks or cloud servers.
2. **Model Freedom**: Swap models freely (`OLLAMA_MODEL=gemma3:4b` to `llama3.2:1b`) without vendor lock-in.
3. **Zero Per-Request Cost**: Run unlimited quests locally without API tokens or subscription paywalls.
4. **Offline Resilience**: Essential outdoor wellness tools should remain functional in remote parks, forests, or internet outages.
5. **Community Control**: Transparent, customizable prompts and open-source codebase.

### Cloud AI vs. GrassQuest AI

| Feature | Closed Cloud AI (Traditional) | GrassQuest AI (Open Innovation) |
| :--- | :--- | :--- |
| **Data Flow** | User ➔ Internet ➔ Cloud API ➔ AI | User ➔ Local Machine ➔ Local AI |
| **Internet Required?** | ❌ Yes (Always) | ✅ No (Runs 100% Offline) |
| **API Costs** | ❌ Per-token charges | ✅ Free forever |
| **Model Swappability** | ❌ Locked to provider | ✅ Swappable via `.env` |
| **User Privacy** | ⚠️ Remote data logging | 🔒 100% On-Device |

---

## ⚡ Quickstart & Installation (Windows Guide)

### 1. Prerequisites
Ensure you have installed:
- **Node.js**: v18+ ([Download](https://nodejs.org/))
- **Python**: v3.10+ ([Download](https://www.python.org/))
- **Ollama**: ([Download Ollama for Windows](https://ollama.com/download))

### 2. Ollama Setup
Start Ollama and pull your preferred open-weight model:
```powershell
# Start Ollama service (if not already running as background service)
ollama serve

# Download the lightweight Gemma open-weight model
ollama pull gemma3:4b
```

### 3. Clone Repository
```powershell
git clone https://github.com/guunda/GrassQuest
cd grassquest-ai
```

### 4. Setup Backend (FastAPI)
```powershell
cd backend

# Create Python virtual environment
py -3 -m venv venv

# Activate virtual environment
.\venv\Scripts\Activate.ps1

# Install requirements
pip install -r requirements.txt

# Create .env from template
Copy-Item .env.example .env

# Run FastAPI backend
uvicorn main:app --reload --port 8000
```
*Backend runs at `http://localhost:8000`*

### 5. Setup Frontend (React + Vite)
Open a new terminal window:
```powershell
cd grassquest-ai/frontend

# Install dependencies
npm install

# Start development server
npm run dev
```
*Frontend runs at `http://localhost:5173`*

---

## ✈️ How to Test Offline Mode

1. Ensure Ollama and FastAPI are running, and model `gemma3:4b` is downloaded.
2. Open `http://localhost:5173` in your web browser.
3. Click **🌿 GENERATE MY QUEST** to verify local AI generation works.
4. **Disconnect your computer from Wi-Fi / Ethernet**.
5. Select a different duration (e.g., 30 min) and click **🌿 GENERATE MY QUEST** again.
6. Observe that quest generation succeeds seamlessly without internet!

---

## 🟡 Hackathon Demo Mode

If you are running the project on a machine where Ollama is not installed or the model is still downloading, simply click the **Demo Mode** toggle switch in the top header.

GrassQuest AI will generate rich, deterministic outdoor quests simulated locally, allowing judges to test the entire quest workflow, countdown timer, points, and rank progression immediately!

---

## 🔮 Future Roadmap

- 📷 **Local Vision Model Integration**: Identify local leaves and birds using local multimodal open models (e.g. `llava`).
- 🌤️ **Offline Weather Adaptability**: Adjust activity intensity based on local temperature or sunlight.
- ⌚ **Wearable Integration**: Sync completed outdoor minutes with offline smartwatch trackers.
- 🗺️ **Community Quest Presets**: Share screen-free quest prompt templates via open-source contribution.

---

## 📜 License

This project is open-source software licensed under the [MIT License](LICENSE).  
Built with ❤️ for **Hacktoberfest 2026 "Touch Grass" Challenge**.
