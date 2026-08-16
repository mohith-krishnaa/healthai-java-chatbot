# HealthAI Pro+

HealthAI Pro+ is an educational full-stack health-information assistant with a lightweight Java HTTP backend and browser frontend. It combines a local knowledge fallback with Google Gemini API integration and an in-memory cache.

**Live Demo:** https://mohith-krishnaa.github.io/healthai-java-chatbot/

> **Medical disclaimer:** This project is educational software, not a medical device or substitute for professional medical care. Do not use it to diagnose, treat, or make urgent medical decisions.

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

- Java HTTP server
- `POST /ask` endpoint
- Gemini API integration
- Local health-information fallback
- In-memory cache with a 6-hour TTL
- Request size limit
- HTTP timeouts and error handling
- CORS handling
- API key loaded from `GEMINI_API_KEY`

### Frontend

- Browser-based chat interface
- LocalStorage chat persistence
- Voice input through Web Speech API
- Dark/light theme
- Copy and export chat actions

## Live usage

Open the live demo above to evaluate the browser interface. AI-backed functionality depends on the configured deployment environment and Gemini API availability.

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

## Requirements for local backend execution

- Java 17 or newer
- `org.json` dependency required by the Java source
- A Gemini API key for AI-backed responses

## Local setup

Clone the repository:

```bash
git clone https://github.com/mohith-krishnaa/healthai-java-chatbot.git
cd healthai-java-chatbot
```

Download a compatible `org.json` JAR and keep the JAR outside source control.

Set the API key as an environment variable. **Do not put a real key in source code.**

Windows PowerShell:

```powershell
$env:GEMINI_API_KEY="your_api_key_here"
```

Linux/macOS:

```bash
export GEMINI_API_KEY="your_api_key_here"
```

## Safety and limitations

This project is **not clinically validated**. Model-generated health information can be incomplete or incorrect, and the local dataset is intentionally limited.

Do not use the application for emergency decisions or as a replacement for a qualified healthcare professional.

Important production considerations include authentication, privacy controls, source citations, model-response evaluation, restricted CORS, and careful handling of browser LocalStorage if sensitive information is entered.

## License

MIT License. See `LICENSE` for details.

## Author

**Mohith Krishnaa** — [@mohith-krishnaa](https://github.com/mohith-krishnaa)
