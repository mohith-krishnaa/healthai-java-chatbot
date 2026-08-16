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
Structured response
```

## Features

### Backend

- Java 17+ HTTP server
- `POST /ask` endpoint
- Gemini API integration
- Local health-information fallback
- In-memory cache with documented TTL
- Request timeouts and error handling
- CORS handling

### Frontend

- Browser-based chat interface
- Guest/login-style UI flows
- LocalStorage chat persistence
- Voice input through Web Speech API
- Dark/light theme
- Copy and export chat actions

## Project structure

```text
.
├── HealthAIProPlus.java
├── index.html
├── README.md
└── LICENSE
```

## Requirements

- Java 17 or newer
- A Gemini API key for AI-backed responses
- `org.json` dependency used by the current Java implementation

## Setup

Clone the repository:

```bash
git clone https://github.com/mohith-krishnaa/healthai-java-chatbot.git
cd healthai-java-chatbot
```

Download the `org.json` JAR version required by the current source and keep it outside source control.

### API key

Do **not** commit a real API key into Java source code. Use an environment variable or another local secret mechanism when adapting the application for deployment.

If the current implementation still contains a source-level key placeholder, replace it with your local configuration before running.

### Compile

Windows classpath syntax:

```powershell
javac -cp ".;json-20230227.jar" HealthAIProPlus.java
```

Linux/macOS classpath syntax:

```bash
javac -cp ".:json-20230227.jar" HealthAIProPlus.java
```

### Run

```bash
java -cp ".;json-20230227.jar" HealthAIProPlus
```

The documented development server runs on `http://localhost:8080`.

## API

### `POST /ask`

Example request:

```json
{
  "message": "What is malaria?"
}
```

The response identifies the source used by the application, such as local knowledge, cache, or Gemini, according to the current implementation.

## Safety and limitations

This project should not be presented as a clinically validated medical system. A model-generated response can be incomplete or wrong, and the local dataset is limited.

Important production gaps include:

- No clinical validation of the knowledge base
- No persistent user database
- No demonstrated authentication boundary for sensitive data
- Browser LocalStorage is not suitable for confidential medical records
- Gemini output requires independent validation
- Caching can return stale information

## Roadmap

Potential engineering improvements:

- Move secrets to environment-based configuration
- Add automated Java tests
- Add structured logging
- Add persistent storage with explicit privacy controls
- Add authentication and authorization
- Add model-response evaluation tests
- Add source citations to generated health information

## License

MIT License. See `LICENSE` for details.

## Author

**Mohith Krishnaa** — [@mohith-krishnaa](https://github.com/mohith-krishnaa)
