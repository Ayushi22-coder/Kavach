[README.md](https://github.com/user-attachments/files/29504346/README.md)
# 🛡️ KAVACH — Citizen Fraud Shield

### AI-Powered Digital Public Safety Platform

> Submission for: **AI for Digital Public Safety — Defeating Counterfeiting, Fraud & Digital Arrest Scams**
> Theme: Smart Cities · Public Safety · Digital Trust · Geospatial Law Enforcement
> Module Built: **Citizen Fraud Shield (Multi-channel)**

---

## 📌 Table of Contents

- [Problem Statement](#-problem-statement)
- [Our Solution](#-our-solution)
- [Live Demo](#-live-demo)
- [Features](#-features)
- [How It Works](#-how-it-works)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Scam Signals Detected](#-scam-signals-detected)
- [Project Structure](#-project-structure)
- [Setup & Installation](#-setup--installation)
- [Evaluation Metrics](#-evaluation-metrics)
- [Judging Criteria Mapping](#-judging-criteria-mapping)
- [Roadmap](#-roadmap)
- [Legal & Compliance](#-legal--compliance)
- [Team / Credits](#-team--credits)

---

## 🎯 Problem Statement

India registered **1.14 million cybercrime complaints in 2023** — up 60% from 2022, and the trend has only steepened. The Ministry of Home Affairs reported that "digital arrest" scams — where fraudsters impersonating CBI, ED, or Customs officers trap victims in multi-day psychological hostage situations over video call — defrauded citizens of over **₹1,776 crore** in just the first nine months of 2024.

These are not opportunistic crimes. They are industrialised operations run from fraud compounds, often across borders, using spoofed numbers, AI-generated voices, and fake government portals.

**The core gap:** Law enforcement has evidence *after* the crime. What's missing is real-time intelligence *before* mass victimisation occurs — and a reliable tool to detect threats at the point of contact, not the point of complaint.

---

## 💡 Our Solution

**KAVACH** (कवच, Sanskrit for "armour") is a real-time, AI-powered, multilingual fraud detection assistant accessible to every Indian citizen — no matter their device, language, or technical literacy.

A citizen describes a suspicious call, WhatsApp message, or situation. KAVACH's AI engine analyses it against known digital arrest scam patterns and returns a clear verdict — **🔴 HIGH / 🟡 MEDIUM / 🟢 LOW risk** — along with exact next steps, in under 3 seconds, in their own language.

This shifts the response model from **reactive case investigation** to **proactive threat neutralisation** — stopping the scam before the money moves.

---

## 🖥️ Live Demo

The prototype is a single self-contained file: **`KAVACH_App.html`**

No installation, no server, no API key required to run the demo — just open it in any browser.

It includes **4 interactive sections** in one app:

| Tab | What it demonstrates |
|---|---|
| 💬 **Live Shield** | The core working chatbot — real-time risk meter, scam flag detection, evidence log, quick-scenario buttons |
| 📱 **WhatsApp** | A WhatsApp-style interface showing the same AI engine on a second citizen-facing channel |
| 🏗️ **Architecture** | Full system architecture, tech stack, and performance metrics |
| 📊 **Pitch Deck** | A built-in 6-slide deck covering problem, solution, judging criteria, and roadmap |

---

## ✨ Features

- **Real-time risk verdict** — HIGH / MEDIUM / LOW with clear reasoning, in under 3 seconds
- **8-signal scam detection engine** — authority impersonation, digital arrest threats, payment demands, secrecy instructions, video call pressure, missing ID, urgency pressure, fake portals
- **Multilingual by design** — UI and architecture built for 12 Indian languages (Hindi, Bengali, Tamil, Telugu, Marathi, Gujarati, Kannada, Malayalam, Punjabi, Odia, Assamese, Urdu)
- **Multi-channel** — Web app, WhatsApp, and IVR (1930 helpline) by design, ensuring zero-smartphone-required access
- **Live evidence log** — session ID, timestamps, and alert counter, designed for court-admissible export
- **One-click escalation** — simulated MHA/NCRB portal escalation with hash-signed evidence packet
- **Quick scenario library** — 5 pre-built real-world scam scenarios for instant demonstration
- **Zero cost to citizen** — designed as free government-funded public infrastructure, similar to the 1930 helpline

---

## ⚙️ How It Works

```
1. Citizen describes situation  →  via Web / WhatsApp / Voice call
2. AI engine analyses           →  8 scam-signal classifier + risk scorer
3. Verdict delivered            →  HIGH / MEDIUM / LOW + action steps, <3 seconds
4. Evidence logged              →  Session ID, timestamp, hash-signed record
5. (If HIGH) Auto-escalated     →  Nearest cyber cell alerted within 60 seconds
```

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    CITIZEN INPUT CHANNELS                    │
│   Web App        WhatsApp Bot       IVR (1930)    Mobile App │
└──────────────────────┬────────────────────────────────────────┘
                       │
┌──────────────────────▼────────────────────────────────────────┐
│                   API GATEWAY (FastAPI)                       │
│   Rate limiting · Session auth · Language detection/routing   │
└──────────────────────┬────────────────────────────────────────┘
                       │
┌──────────────────────▼────────────────────────────────────────┐
│                  KAVACH AI ENGINE                              │
│  ┌──────────────────┐    ┌──────────────────────┐             │
│  │  LLM Classifier   │    │   Rule Engine         │            │
│  │  (Claude API)     │    │   8 scam signal rules  │           │
│  └────────┬──────────┘    └──────────┬────────────┘           │
│           └─────────────┬────────────┘                        │
│                         ▼                                     │
│              ┌────────────────────────┐                       │
│              │     Fusion Scorer       │                      │
│              │  → HIGH / MEDIUM / LOW  │                      │
│              └────────────┬─────────────┘                     │
└───────────────────────────┼──────────────────────────────────┘
                            │
┌───────────────────────────▼──────────────────────────────────┐
│                    OUTPUT LAYER                               │
│  Citizen Verdict (in language)  │  MHA Alert API (HIGH→60s)   │
│  Evidence Package (SHA-256+IPFS)│  cybercrime.gov.in submit   │
└─────────────────────────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| AI Engine | Claude (Anthropic API) | Core scam classification & conversational reasoning |
| Language | IndicTrans2 (AI4Bharat) | 12 Indian language translation |
| Speech | Deepgram STT | Speech-to-text for IVR channel |
| Backend | FastAPI (Python) | REST API gateway |
| Database | PostgreSQL | Session logs, complaint records |
| Cache | Redis | Real-time session state, rate limiting |
| Evidence | IPFS + SHA-256 | Immutable, tamper-proof evidence chain |
| WhatsApp | Twilio Business API | WhatsApp channel integration |
| Voice | Twilio Voice | IVR channel via 1930 |
| Frontend | HTML / CSS / JavaScript | Zero-dependency, deployable anywhere |
| Mobile | React Native | Android / iOS app (planned) |
| Infra | Docker + Kubernetes | Containerised, horizontally scalable |
| Hosting | AWS (ap-south-1) | Data sovereignty / DPDP compliant |

**Current prototype status:** The frontend, UI/UX, conversation engine logic, and full system design are built and demonstrated. The prototype currently runs on a curated, pattern-matched response library (validated against real scam transcripts) to guarantee 100% demo reliability; the architecture is designed to plug directly into the live Claude API for production deployment.

---

## 🚩 Scam Signals Detected

| Signal | Pattern | Weight |
|---|---|---|
| Authority impersonation | Caller claims to be CBI / ED / Customs / Police | High |
| Digital arrest threat | "You are under digital arrest" | Critical |
| Payment demand | Transfer money to "clear name" / avoid arrest | Critical |
| Secrecy instruction | "Don't tell your family or friends" | High |
| Video call pressure | Forced to remain on-screen / under "custody" | High |
| No verifiable ID | Caller cannot produce badge or official letter | Medium |
| Urgency pressure | "Act within X minutes or be arrested" | Medium |
| Fake government portal | Spoofed WhatsApp message, email, or website | Medium |

---



## 🚀 Setup & Installation

### Quickest way
Double-click `KAVACH_App.html` — opens directly in your browser. No install needed.

### Recommended way (VS Code + Live Server)
1. Open the project folder in VS Code
2. Install the **Live Server** extension (`Ctrl+Shift+X` → search "Live Server" by Ritwick Dey)
3. Right-click `KAVACH_App.html` → **Open with Live Server**

Full details in [`SETUP.md`](./SETUP.md).

---


## ⚖️ Legal & Compliance

- **DPDP Act 2023** compliant — no personally identifiable conversation data stored without explicit consent
- **IT Act 2000** compliant — evidence chain designed for legal admissibility
- Data residency restricted to **AWS India (ap-south-1)** region
- All sessions encrypted in transit (TLS 1.3)
- Evidence submission is **opt-in** — citizen controls what gets escalated

---

## 👥 Team / Credits

Built for the **AI for Digital Public Safety** hackathon track.
Powered by **Claude (Anthropic)** for natural language scam pattern classification.

📞 **Cyber Crime Helpline: 1930**
🌐 **cybercrime.gov.in**

---

*KAVACH (कवच) — Sanskrit for "armour". Because every Indian deserves protection.*
