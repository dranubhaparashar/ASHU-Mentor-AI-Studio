# Quick Links

## Demo

- [YouTube Demo](https://youtu.be/2XXnTbtjREs)
- [Live Hugging Face App](https://huggingface.co/spaces/AnubhaParashar/ASHU)

## Local Run Command

```bash
conda activate chatbot

cd "/mnt/c/Users/AnubhaAnubha/OneDrive - Pearce Services, LLC/onedrive_ubuntu/project/chatbot3"

ASHU_VOICE_ENV=voice COQUI_TOS_AGREED=1 PYTHONNOUSERSITE=1 python -m streamlit run app.py --server.fileWatcherType none
```

## Important Folders

```text
chatbot3/
├── app.py
├── tools/voice_clone_xtts.py
├── voice_samples/
├── presenter_sources/
├── lipsync_renders/
└── reports/
```

## Renderer Paths

```text
SadTalker: /home/anubhaparashar/ashu_renderers/SadTalker
Wav2Lip:   /home/anubhaparashar/ashu_renderers/Wav2Lip
```

## Troubleshooting Commands

```bash
# Check voice env
conda activate voice
PYTHONNOUSERSITE=1 python -c "from TTS.api import TTS; print('TTS import OK')"

# Check latest generated video
cd "/mnt/c/Users/AnubhaAnubha/OneDrive - Pearce Services, LLC/onedrive_ubuntu/project/chatbot3"
latest=$(find lipsync_renders -name "*.mp4" -printf "%T@ %p\n" | sort -n | tail -1 | cut -d' ' -f2-)
echo "$latest"
explorer.exe "$(wslpath -w "$latest")"
```
