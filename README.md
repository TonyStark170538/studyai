# StudyAI — Ollama Setup Guide
## 100% Free. No API key. Runs on your computer.

---

## Step 1 — Install Ollama

1. Go to **https://ollama.com**
2. Click **Download** and install it like any normal app
3. It runs silently in the background after install

---

## Step 2 — Download an AI model

Open a terminal (Command Prompt / PowerShell on Windows, Terminal on Mac/Linux) and run:

```
ollama pull llama3.2
```

This downloads the model (~2GB). You only do this once.

**Other free models you can use:**
| Model | Command | Good for |
|---|---|---|
| llama3.2 ⭐ | `ollama pull llama3.2` | Best overall, recommended |
| mistral | `ollama pull mistral` | Fast, good quality |
| gemma3 | `ollama pull gemma3` | Google's model |
| phi4 | `ollama pull phi4` | Lightweight, fast |

---

## Step 3 — Start Ollama with browser access enabled

This is the most important step. You must run Ollama with a special flag so the app can talk to it.

**Windows (PowerShell):**
```powershell
$env:OLLAMA_ORIGINS="*"; ollama serve
```

**Windows (Command Prompt):**
```cmd
set OLLAMA_ORIGINS=* && ollama serve
```

**Mac / Linux:**
```bash
OLLAMA_ORIGINS=* ollama serve
```

Keep this terminal window open while using StudyAI.

> ⚠️ If you skip this step, the app will show "Ollama not found" even if Ollama is installed.

---

## Step 4 — Start the local web server

Open a **second** terminal window, go to the studyai folder, and run:

**Windows:**
```powershell
cd C:\Users\YourName\Desktop\studyai
python -m http.server 8080
```

**Mac / Linux:**
```bash
cd ~/Desktop/studyai
python3 -m http.server 8080
```

Then open your browser and go to:
```
http://localhost:8080
```

---

## Step 5 — Use the app

1. The app opens and **automatically checks if Ollama is running**
2. A setup screen shows — select your model (e.g. `llama3.2`) and click **Connect**
3. Upload a **.txt file** (see note below about PDFs)
4. Use any of the 6 study tools!

---

## About PDF files

Ollama runs locally and cannot read PDF binary files directly.

**To use a PDF:**
1. Open your PDF in any PDF viewer (Adobe, browser, etc.)
2. Press `Ctrl+A` (Select All) then `Ctrl+C` (Copy)
3. Open Notepad (Windows) or TextEdit (Mac)
4. Paste and save as `mystudy.txt`
5. Upload that `.txt` file to StudyAI

---

## Troubleshooting

| Problem | Fix |
|---|---|
| "Ollama not found" | Run `OLLAMA_ORIGINS=* ollama serve` (Step 3) |
| "Failed to fetch" | You opened the HTML file directly — use `localhost:8080` (Step 4) |
| App is slow | Normal for local AI — llama3.2 takes 10–60s depending on your PC |
| Flashcards show error | Model didn't return valid JSON — click "New Set" to retry |
| Quiz doesn't generate | Try a smarter model like `llama3.2` or `mistral` |
| Model not in list | Pull it first: `ollama pull modelname` |

---

## File structure

```
studyai/
├── index.html    ← The entire app
└── README.md     ← This file
```

No installation. No npm. No API key. No cost.
Just Ollama running locally + a browser.

---

## Features

| Tab | What it does |
|---|---|
| 📄 Upload | Load a TXT or MD file |
| 📋 Summary | AI structured study notes with streaming text |
| 🃏 Flashcards | 15 flip cards — Generate New Set anytime |
| 🧩 Quiz | MCQ + True/False + Fill-in-the-blank with scoring |
| 🎓 Exam Prep | Predicted topics, practice Q&A, memory aids |
| 💡 Explain | Deep concept explanation with analogies |
| 📥 Export | Download notes as formatted HTML |
