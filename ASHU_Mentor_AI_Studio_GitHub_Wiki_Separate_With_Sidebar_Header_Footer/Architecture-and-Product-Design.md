# Architecture & Product Design

ASHU Mentor AI Studio is organized as a local-first, multi-stage AI system. The core application runs in the `chatbot` environment, while the consent-based voice generation pipeline runs in a separate `voice` environment to avoid dependency conflicts with video rendering.

## High-Level Architecture

```mermaid
flowchart LR
    U[User / Trainer / Candidate] --> UI[Streamlit UI]
    UI --> LLM[Local LLM Engine]
    UI --> INT[Interview & Training Orchestrator]
    UI --> CAP[Candidate Capture Layer]

    INT --> QG[Resume/JD-Aware Question Generator]
    INT --> EV[Answer Evaluation Engine]
    INT --> TR[Adaptive Training Planner]

    TR --> VOICE[XTTS Voice Generation\nvoice env]
    VOICE --> AUDIO[Generated tts_audio.wav]
    AUDIO --> RENDER[Local Lip-Sync Renderer\nSadTalker / Wav2Lip]
    RENDER --> MP4[Lecture MP4]
    MP4 --> SAFE[Browser-Safe MP4 Conversion]
    SAFE --> PLAYER[YouTube-Style Assistant Player]

    CAP --> EVID[Evidence Store]
    EV --> REPORT[Candidate Report]
    EVID --> REPORT
```

## Runtime Layers

| Layer | Responsibility |
|---|---|
| Streamlit UI | Tabs, controls, teaching assistant panel, progress bars, downloads |
| Local LLM | Question generation, evaluation feedback, adaptive training content |
| Interview Engine | Resume/JD-aware rounds, coding prompts, face-to-face questions |
| Voice Engine | Consent-based XTTS generation using selected authorized sample |
| Video Engine | SadTalker/Wav2Lip rendering, browser-safe MP4 conversion |
| Cache Layer | Reuse previous `tts_audio.wav` and generated MP4 for faster demos |
| Evidence Layer | Recording metadata, screenshots, logs, transcripts, downloadable bundles |

## Environment Separation

```mermaid
flowchart TB
    A[chatbot env] --> B[Streamlit app]
    A --> C[SadTalker/Wav2Lip integration]
    A --> D[Browser-safe MP4 conversion]
    B -->|conda run -n voice| E[voice env]
    E --> F[Coqui XTTS / TTS]
    F --> G[tts_audio.wav]
    G --> C
```

This separation prevents XTTS/TTS dependencies from breaking the video rendering stack.
