# Voice Agent (Murf + LiveKit)

A real-time voice AI agent built on top of the [Murf LiveKit starter](https://github.com/murf-ai/murf-livekit-starter).

The pipeline: user speaks -> Deepgram transcribes -> LLM generates a response -> Murf Falcon
synthesizes speech -> LiveKit streams it back. All over WebRTC, so latency stays low.

## Architecture

```
User speaks -> [Deepgram STT] -> [LLM] -> [Murf Falcon TTS] -> [LiveKit] -> User hears
```

## Setup

You'll need API keys for LiveKit, Murf, Deepgram, and either Google (Gemini) or OpenAI.

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

Or use the all-in-one script: `./start_app.ps1` (Windows) / `./start_app.sh` (Mac/Linux)

See the original [Murf starter README](https://github.com/murf-ai/murf-livekit-starter) for
full setup docs, deployment guides, and voice configuration.
