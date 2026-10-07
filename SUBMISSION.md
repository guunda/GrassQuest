*This is a submission for the [Hacktoberfest Open-Source AI Challenge Week 1: Touch Grass](https://dev.to/challenges/hacktoberfest-week1-2026-10-05)*

# 🌿 GrassQuest AI — Touch Grass. Literally.

> *"Use open-weight local AI to get people off their screens and into the physical world."*

---

## What I Built

**GrassQuest AI** is a privacy-first, offline-capable outdoor activity generator designed for the **Hacktoberfest 2026 "Touch Grass"** challenge.

### The Core Idea
Modern software and AI tools are almost exclusively engineered for **screen retention** — drawing users deeper into endless chats, notification feeds, and digital doomscrolling. 

**GrassQuest AI** flips this paradigm on its head:
1. **Brief AI Interaction**: The user selects their available outdoor time (e.g., 10 min, 20 min, 30 min, 1 hour), activity preference (Nature, Walking, Wildlife, Photography, Gardening, Fitness), and location type.
2. **Local AI Inference**: A locally running open-weight model (via Ollama) generates 2–4 safe, actionable, screen-free observation objectives.
3. **Screen-Free Call to Action**: The quest screen prominently displays:  
   `📱 PUT YOUR PHONE AWAY`  
   `🌳 GO TOUCH GRASS`
4. **Offline Micro-Adventure**: The user pockets their phone, steps outside, launches an interactive countdown timer, and earns **Grass Points** and **Rank Levels** upon completion.

The AI is deliberately the **shortest** part of the experience. The main event happens out in the physical world.

---

## Demo

### Local Application Experience

```
[ 🌿 GrassQuest AI Generator ]
       │
       ▼
[ 🌿 YOUR GRASS QUEST: Botanical Canopy & Texture ]
 ├── Objective 1: Find two distinct leaf shapes
 ├── Objective 2: Observe a flowering plant for 60s
 └── Objective 3: Feel rough tree bark texture
       │
       ▼
[ 📱 PUT YOUR PHONE AWAY 🌳 GO TOUCH GRASS ]
       │
       ▼
[ ⏱️ Active Countdown Timer (20:00) ]
       │
       ▼
[ 🎉 QUEST COMPLETE! +100 Grass Points ] ➔ Rank: 🌿 Explorer
```

- **Frontend Application**: Running at `http://localhost:5173`
- **FastAPI Local Backend**: Running at `http://localhost:8000`
- **Hackathon Demo Mode**: Built-in toggle switch to simulate local AI inference instantly on machine setups without Ollama installed.

---

## Code

{% github your-username/grassquest-ai %}

### Project Repository Structure
- `frontend/`: React 18 + Vite + Lucide React + Custom Nature-Inspired Glassmorphic CSS System.
- `backend/`: FastAPI + Pydantic + `httpx` connecting to local Ollama API.
- `Ollama Integration`: Configurable via `.env` (`OLLAMA_MODEL=gemma3:4b`).

---

## How I Built It

GrassQuest AI is designed around an **Offline-First, Open-Weight AI Architecture**:

### 1. Open-Weight AI Inference (Ollama)
- **Engine**: [Ollama](https://ollama.com/) local inference engine.
- **Model**: Default `gemma3:4b` (also compatible with `gemma:2b`, `llama3.2:1b`, and `mistral`).
- **Prompt Design**: Structured system prompt enforcing raw JSON schema output with strict safety constraints (zero cost, safe observation, screen-free focus, 2–4 objectives).

### 2. FastAPI Backend Service (`backend/`)
- Async endpoints (`POST /generate-quest`, `GET /health`).
- Automatic JSON cleaning and error recovery for local LLM output.
- Robust status reporting for Ollama connectivity and installed models.
- Deterministic fallback quest generator for offline Demo Mode.

### 3. React + Vite Frontend (`frontend/`)
- **Zero Heavy UI Libraries**: Built using a custom, high-performance vanilla CSS design system featuring nature-inspired tokens (forest greens, mint highlights, glassmorphism, responsive cards).
- **Interactive Timer**: Built-in quest countdown timer with pause, resume, and quick completion.
- **Gamified Level Progression**:
  - `0 – 499 pts`: 🌱 **Seedling**
  - `500 – 999 pts`: 🌿 **Explorer**
  - `1000 – 1999 pts`: 🌳 **Nature Walker**
  - `2000+ pts`: 🌲 **Grass Master**

### 4. Browser LocalStorage (Zero Server Tracking)
- Points, completed outdoor minutes, and quest history are saved 100% on the user's browser device via `LocalStorage`.

---

## Why Does Open Innovation Matter?

Building **GrassQuest AI** on open-weight AI and local inference unlocked critical capabilities that closed, proprietary cloud APIs could never provide:

1. **True Privacy Guarantee**: Wellness and outdoor routine data should never be collected or monetized. Because inference runs locally, zero user data leaves the machine.
2. **Offline Resilience**: Outdoor adventures often happen in remote parks or areas with poor internet connection. Local AI means GrassQuest AI works seamlessly with Wi-Fi disabled.
3. **Zero Per-Request Cost**: Users can generate unlimited quests without worrying about cloud API tokens, rate limits, or monthly subscription paywalls.
4. **Model Freedom**: Users retain full control to swap models (`OLLAMA_MODEL=gemma3:4b` vs `llama3.2:1b`) based on their hardware capabilities.

### Closed Cloud AI vs. GrassQuest AI

| Dimension | Proprietary Cloud AI | GrassQuest AI (Open Innovation) |
| :--- | :--- | :--- |
| **Data Path** | User ➔ Internet ➔ Cloud Server ➔ AI | User ➔ Local Host ➔ Ollama Engine |
| **Offline Functionality** | ❌ Fails without Internet | ✅ Works 100% Offline |
| **API Costs** | ❌ Metered token fees | ✅ 100% Free & Open Source |
| **User Privacy** | ⚠️ Centralized data retention | 🔒 Strict On-Device LocalStorage |

---

## My Agent Session

This project was pair-programmed and built using autonomous AI agent capabilities with step-by-step local validation, end-to-end testing, and automated build verification.

---

## Prize Categories

- **Hacktoberfest Week 1: Touch Grass Challenge**
- **Local AI & Open-Weight Innovation**
