# HealthAI Pro+

HealthAI Pro+ is an educational full-stack health-information assistant with a lightweight Java HTTP backend and browser frontend. It combines a local knowledge fallback with Google Gemini API integration and an in-memory cache.

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

## Requirements

- Java 17 or newer
- `org.json` dependency required by the Java source
- A Gemini API key for AI-backed responses

## Setup

Clone the repository:

```bash
git clone https://github.com/mohith-krishnaa/healthai-java-chatbot.git
cd healthai-java-chatbot
```

Download a compatible `org.json` JAR and keep the JAR outside source control.

### Configure Gemini

Set the API key as an environment variable. **Do not put a real key in `HealthAIProPlus.java`.**

Windows PowerShell:

```powershell
$env:GEMINI_API_KEY="your_api_key_here"
```

Linux/macOS:

```bash
export GEMINI_API_KEY="your_api_key_here"
```

A `.env.example` file is provided as a reference, but this plain Java application does not automatically load `.env` files. The variable must exist in the process environment unless you add a dotenv library yourself.

### Compile

Windows:

```powershell
javac -cp ".;json-20230227.jar" HealthAIProPlus.java
```

Linux/macOS:

```bash
javac -cp ".:json-20230227.jar" HealthAIProPlus.java
```

### Run

Windows:

```powershell
java -cp ".;json-20230227.jar" HealthAIProPlus
```

Linux/macOS:

```bash
java -cp ".:json-20230227.jar" HealthAIProPlus
```

Open `http://localhost:8080` after the server starts.

## API

### `POST /ask`

Request:

```json
{
  "message": "What is malaria?"
}
```

The response includes the generated reply and a `source` value indicating whether the response came from local knowledge, cache, or Gemini.

## Safety and limitations

This project is **not clinically validated**. Model-generated health information can be incomplete or incorrect, and the local dataset is intentionally limited.

Do not use the application for emergency decisions or as a replacement for a qualified healthcare professional.

Important production gaps include:

- No clinical validation of the knowledge base
- No persistent user database
- No authentication boundary for sensitive medical data
- Browser LocalStorage is not suitable for confidential medical records
- Gemini output requires independent validation
- Cache entries can become stale
- CORS is currently permissive and should be restricted before production deployment

## Roadmap

- Add automated Java tests
- Add structured logging
- Add persistent storage with explicit privacy controls
- Add authentication and authorization
- Add model-response evaluation tests
- Add source citations to generated health information
- Restrict CORS for production deployments

## License

MIT License. See `LICENSE` for details.

## Author

**Mohith Krishnaa** — [@mohith-krishnaa](https://github.com/mohith-krishnaa)
