# Security Policy

HealthAI Pro+ is an educational project and is not clinically validated. It accepts user prompts, can call an external model provider, and stores conversation state in the browser. Do not submit real patient records, credentials, or other sensitive personal information.

## Supported versions

Only the latest state of the `main` branch is considered for security fixes. This project does not currently promise a long-term supported release line.

## Reporting a vulnerability

Please open a private security report through GitHub’s **Report a vulnerability** flow if it is enabled for this repository. If that option is unavailable, open a minimal issue without including secrets, personal data, exploit payloads, or private conversations, and request a private follow-up channel from the maintainer.

Include the affected file or route, a short impact description, reproduction steps that use non-sensitive data, and any suggested mitigation. Please allow reasonable time for triage before public disclosure.

## Scope reminders

Do not treat the demo as a medical service. Report exposed credentials, unsafe CORS behavior, prompt or data leakage, authentication bypasses, and vulnerabilities that could affect users or the hosted demo. General model-quality complaints are useful project feedback but are not necessarily security vulnerabilities.
