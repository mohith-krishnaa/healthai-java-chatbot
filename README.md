# HealthAI Pro+

An educational full-stack health-information assistant with a lightweight Java HTTP backend and browser frontend. The project combines a local knowledge fallback, Google Gemini integration, request controls and an in-memory cache.

**Live demo:** https://mohith-krishnaa.github.io/healthai-java-chatbot/

> **Medical disclaimer:** This is educational software, not a medical device or substitute for professional medical care. Do not use it to diagnose, treat, or make urgent medical decisions.

## Architecture

```text
Browser
   ↓ POST /ask
Java HTTP server
   ↓
Cache
   ↓ miss
Local knowledge
   ↓ miss
Gemini API
   ↓
Response
```

## Features

### Backend

- Java HTTP server with `POST /ask`
- Gemini API integration
- Local knowledge fallback
- 6-hour in-memory response cache
- Request-size limit
- HTTP timeouts and error handling
- CORS handling
- API key loaded from `GEMINI_API_KEY`

### Frontend

- Browser chat interface
- LocalStorage conversation persistence
- Web Speech API voice input
- Dark/light theme
- Copy and export actions

## Local setup

Requirements:

- Java 17+
- `org.json` dependency
- Gemini API key for AI-backed responses

Clone the repository:

```bash
git clone https://github.com/mohith-krishnaa/healthai-java-chatbot.git
cd healthai-java-chatbot
```

Set the API key as an environment variable. Never hard-code a real key.

Windows PowerShell:

```powershell
$env:GEMINI_API_KEY="your_api_key_here"
```

Linux/macOS:

```bash
export GEMINI_API_KEY="your_api_key_here"
```

Keep the compatible `org.json` JAR outside source control and compile/run using your local Java setup.

## Project structure

```text
.
├── HealthAIProPlus.java
├── index.html
├── .env.example
├── .gitignore
├── README.md
└── LICENSE
```

## Safety and privacy

This project is **not clinically validated**. Model-generated health information may be incomplete or incorrect, and the local knowledge base is intentionally limited.

Production use would require stronger authentication, privacy controls, source citations, model evaluation, restricted CORS, secure secret management and careful treatment of browser-stored conversation data.

Do not use this project for emergencies or as a replacement for qualified medical care.

## License

MIT License. See `LICENSE` for details.

## Author

**Mohith Krishnaa** — [@mohith-krishnaa](https://github.com/mohith-krishnaa)
