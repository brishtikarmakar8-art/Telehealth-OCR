# 🏥 TeleHealth-OCR

> **AI-powered prescription and medical report intelligence using Gemma 4 for safer, smarter telehealth.**

TeleHealth-OCR is a multimodal clinical assistant that converts handwritten prescriptions and medical reports into structured, patient-friendly intelligence. By pairing **Gemma 4 multimodal vision** with **Google Search Grounding**, the platform transcribes complex handwriting, generates daily medication schedules, and retrieves real-time clinical safety and visual pill descriptions.

Built under the **Agent Skill Open Standard (`SKILL.md`)** for seamless interoperability with open-source AI agent ecosystems.

---

## 🚀 Problem

Handwritten prescriptions and medical reports are notoriously difficult to read, leading to preventable medical errors and patient confusion.

* 📝 **Illegible Cursive Handwriting:** Sloppy medical shorthand (e.g., *"Tab. Amoxicillin 500mg TDS x 5 days"*).
* 💊 **Dosage & Timing Ambiguity:** Confusion over meal timings and daily intake frequency.
* ⚠️ **Missing Drug Safety Facts:** Lack of immediate warnings regarding common side effects and clinical benefits.
* 🌐 **Opaque Physical Identifiers:** Patients often do not know what their prescribed pill or capsule actually looks like.

---

## 💡 System Architecture & Pipeline

```text
📷 Upload Prescription Photo
           ↓
🤖 Multimodal OCR & Schema Parsing (Gemma 4 + Pydantic)
           ↓
🌐 Live Grounded Search (Gemma 4 + Google Search Tool)
           ↓
💊 Structured Schedule Cards & Visual Reference URLs
           ↓
📱 Next.js Patient Dashboard & Agent Skill Export
```

---

## ✨ Key Features

* 📷 **Multimodal Prescription OCR:** Reads handwritten doctor notes, cursive scripts, and lab report tables using `gemma-4-31b-it`.
* 📊 **Strict Pydantic Schema Enforcement:** Guarantees database-ready structured output (`drug_name`, `dosage`, `frequency`, `timing`, `duration_days`).
* 🌐 **Grounded Search Intelligence:** Chains Gemma 4 with Google Search to fetch verified clinical benefits, side effects, and visual pill descriptions.
* 💊 **Patient Schedule Cards:** Displays clear morning, afternoon, and night intake indicators in plain English.
* ⚙️ **Agent Skill Open Standard Compliant:** Includes `.agents/skills/telehealth-ocr/SKILL.md` for tool integration into open-source agent platforms.
* 🛡️ **Fail-Safe Demo Resilience:** Features automatic retry logic and fallback mechanisms to ensure 100% demo stability during judge evaluations.

---

## 🧠 Technology Stack

* **Frontend:** Next.js, React, Tailwind CSS, TypeScript
* **Backend Service:** FastAPI, Uvicorn, Pydantic, Python 3.10+
* **AI Engine & Multimodal OCR:** Google `gemma-4-31b-it` / `gemma-4-26b-a4b-it` via official Google GenAI SDK
* **Web Intelligence:** Gemma 4 Google Search Grounding Tool Call Engine
* **Standards:** Agent Skill Open Standard (`SKILL.md`)

---

## 📂 Project Structure

```text
TeleHealth-OCR/
│
├── .agents/
│   └── skills/
│       └── telehealth-ocr/
│           └── SKILL.md           # Agent Skill Open Standard Manifest
│
├── frontend/                      # Next.js UI Application (Member A)
│   ├── src/
│   │   ├── components/
│   │   └── pages/
│   └── package.json
│
├── main.py                        # FastAPI Backend & Gemma 4 Pipeline (Member B)
├── requirements.txt               # Python Dependencies
├── .env.example                   # Environment Template
├── README.md                      # Project Documentation (Member C)
└── LICENSE                        # MIT Open-Source License
```

---

## ⚙️ Quickstart & Local Setup

### 1. Prerequisites

* Python 3.10+
* Node.js 18+
* Active `GEMINI_API_KEY` from Google AI Studio

### 2. Backend Setup (FastAPI)

```bash
# Clone repository
git clone https://github.com/YOUR-USERNAME/TeleHealth-OCR.git
cd TeleHealth-OCR

# Install Python dependencies
pip install -r requirements.txt

# Configure environment variables
echo "GEMINI_API_KEY=your_google_ai_studio_api_key_here" > .env

# Run backend server
uvicorn main:app --reload --port 8000
```

Backend Interactive Swagger Docs will be available at: `http://127.0.0.1:8000/docs`

### 3. Frontend Setup (Next.js)

```bash
cd frontend
npm install
npm run dev
```

Open `http://localhost:3000` in your browser.

---

## 🔑 Environment Variables

Create a `.env` file in the root directory:

```env
GEMINI_API_KEY=your_gemini_api_key_here
FRONTEND_URL=http://localhost:3000
```

---

## 👥 Team & Roles

| Member | Role | Key Deliverables |
| --- | --- | --- |
| **Member A** | Frontend Lead | Next.js UI, custom medication schedule cards, drug intelligence side drawer, demo state. |
| **Member B** | AI & Backend Lead | FastAPI engine, Gemma 4 OCR schema parsing, Google Search grounding pipeline, retry logic. |
| **Member C** | Agent Architect & Open Source | `SKILL.md` manifest specification, repository structure, documentation, MIT license setup. |

---

## ⚠️ Medical Disclaimer

*Important: TeleHealth-OCR provides AI-generated informational guidance and does not replace advice from a qualified healthcare professional. Always verify prescription details with your physician or pharmacist before taking medications.*

---

## 📜 License

This project is open-source and licensed under the **MIT License**. See the `LICENSE` file for details.
