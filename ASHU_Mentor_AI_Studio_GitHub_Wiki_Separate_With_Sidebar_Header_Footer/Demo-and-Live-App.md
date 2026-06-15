# Demo & Live App

## Video Walkthrough

[Watch ASHU Mentor AI Studio demo on YouTube](https://youtu.be/2XXnTbtjREs)

## Live App

[Try ASHU Mentor AI Studio on Hugging Face Spaces](https://huggingface.co/spaces/AnubhaParashar/ASHU)

## Local App Runtime

ASHU Mentor AI Studio also runs as a local Streamlit application.

```bash
conda activate chatbot

cd "/mnt/c/Users/AnubhaAnubha/OneDrive - Pearce Services, LLC/onedrive_ubuntu/project/chatbot3"

ASHU_VOICE_ENV=voice COQUI_TOS_AGREED=1 PYTHONNOUSERSITE=1 python -m streamlit run app.py --server.fileWatcherType none
```

## Demo Flow

1. Load candidate resume or training topic.
2. Select interview/training mode.
3. Generate question or learning segment.
4. Use live browser preview for quick teaching.
5. Use authorized XTTS voice for final lecture audio.
6. Render digital presenter video through SadTalker/Wav2Lip.
7. Prefetch cached output for fast repeated demos.
8. Play the generated lecture in the YouTube-style assistant player.
9. Download final MP4 and evidence/report bundle.

## What the Demo Shows

- Local LLM readiness
- Lip-sync renderer readiness
- Authorized voice sample selection
- XTTS generated audio
- Background voice/video rendering
- Teaching assistant video playback
- Cached media prefetch
- Final lecture video download
