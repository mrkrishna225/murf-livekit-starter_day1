# Voice Agent (Murf + LiveKit)

A real-time voice AI agent built on top of the
[Murf LiveKit starter](https://github.com/murf-ai/murf-livekit-starter).

User speaks -> Deepgram transcribes -> LLM generates a response -> Murf Falcon synthesizes
speech -> LiveKit streams it back over WebRTC.

## Architecture

```
User speaks --> [Deepgram STT] --> [LLM (Gemini/OpenAI)] --> [Murf Falcon TTS] --> [LiveKit WebRTC] --> User hears
```

## What I changed from the starter

- Customized the system prompt for a specific use case
- Configured voice selection and LLM provider

## Setup

You'll need API keys for: LiveKit, Murf, Deepgram, and either Google (Gemini) or OpenAI.

```bash
# Backend
cd backend
uv sync
uv run python src/agent.py dev

# Frontend
cd frontend
pnpm install
pnpm dev
```

Or use the all-in-one script:
- Windows: `.\start_app.ps1`
- Mac/Linux: `./start_app.sh`

## Project structure

```
backend/
  src/agent.py       # Agent entry point — system prompt, STT/LLM/TTS config
  pyproject.toml     # Python deps (uv)
frontend/
  app/page.tsx       # Main page
  components/        # UI components
  app-config.ts      # Branding and button text
```

Full docs in the original [Murf starter repo](https://github.com/murf-ai/murf-livekit-starter).
