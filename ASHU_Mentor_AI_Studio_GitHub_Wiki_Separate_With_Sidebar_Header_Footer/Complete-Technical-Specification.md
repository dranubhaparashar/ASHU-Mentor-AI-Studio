# Complete Technical Specification

## Project Name

**ASHU Mentor AI Studio**  
**Full form:** Adaptive Smart Human-like Unit Mentor AI Studio

## Purpose

ASHU Mentor AI Studio is a local AI-powered system for interview simulation, candidate evaluation, adaptive training, and digital-human lecture generation. It supports both fast browser-based previews and production-style generated lecture videos using authorized voice and presenter media.

## Core Capabilities

1. Resume-aware interview question generation
2. Job-description-aware interview simulation
3. Candidate answer scoring and feedback
4. Coding-round and technical-round support
5. Adaptive training recommendations
6. Digital-human teaching assistant
7. Consent-based XTTS voice generation
8. SadTalker/Wav2Lip lip-sync video generation
9. Background voice/video rendering
10. Cached lecture prefetching
11. YouTube-style embedded video playback
12. Downloadable lecture videos and evidence bundles

## Local Runtime Command

```bash
conda activate chatbot

cd "/mnt/c/Users/AnubhaAnubha/OneDrive - Pearce Services, LLC/onedrive_ubuntu/project/chatbot3"

ASHU_VOICE_ENV=voice COQUI_TOS_AGREED=1 PYTHONNOUSERSITE=1 python -m streamlit run app.py --server.fileWatcherType none
```

## Conda Environments

| Environment | Purpose |
|---|---|
| `chatbot` | Main Streamlit app, UI, candidate workflows, rendering orchestration |
| `voice` | XTTS/Coqui voice generation only |

## Important Local Paths

| Component | Path |
|---|---|
| Main app | `/mnt/c/Users/AnubhaAnubha/OneDrive - Pearce Services, LLC/onedrive_ubuntu/project/chatbot3` |
| SadTalker renderer | `/home/anubhaparashar/ashu_renderers/SadTalker` |
| Wav2Lip renderer | `/home/anubhaparashar/ashu_renderers/Wav2Lip` |
| Generated media cache | `lipsync_renders/` |
| Authorized voice samples | `voice_samples/` |
| Presenter source media | `presenter_sources/` |

## Voice Environment Compatibility

Validated voice stack:

```text
numpy 1.22.0
scipy 1.11.4
torch 2.2.2+cpu
transformers 4.41.2
tokenizers 0.19.1
huggingface-hub 0.23.5
TTS 0.22.0
```

## Generated Artifacts

| Artifact | Description |
|---|---|
| `tts_audio.wav` | Generated XTTS/automated lecture audio |
| `tts_audio.script.txt` | Lecture script passed to voice engine |
| `talking_presenter_output.mp4` | Raw rendered digital-human lecture video |
| `*_browser.mp4` | Browser-safe H.264/AAC MP4 for Streamlit player |
| `manifest.json` | Media paths, voice mode, renderer status, selected sample |
| `voice_generation_run.log` | XTTS generation log |
| `renderer_run.log` | SadTalker/Wav2Lip render log |

## System Design Principles

- Local-first processing where possible
- Explicit consent for voice and presenter use
- No silent fallback from authorized voice to automated voice
- User-approved fallback if voice cloning fails
- Background execution for long-running tasks
- Cache reuse to avoid repeated slow rendering
- Evidence separation between candidate capture and digital presenter generation
