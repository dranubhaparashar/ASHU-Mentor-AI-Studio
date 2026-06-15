# Acceptance Criteria Mapping

| Requirement | Acceptance Criteria | Status |
|---|---|---|
| Local-first app | App runs locally through Streamlit in `chatbot` env | Implemented |
| Separate voice environment | XTTS runs through `conda run -n voice` | Implemented |
| Authorized voice sample | App stores and reuses selected sample from `voice_samples/` | Implemented |
| Coqui/XTTS terms handling | User checkbox sets `COQUI_TOS_AGREED=1` | Implemented |
| No silent voice fallback | XTTS errors are shown and fallback requires user approval | Implemented |
| Background audio generation | Voice can run in background pipeline | Implemented |
| Background video rendering | SadTalker/Wav2Lip can run without freezing UI | Implemented |
| Cached lecture reuse | Latest generated audio/video can be prefetched | Implemented |
| Browser-safe video playback | Raw MP4 converted to H.264/AAC browser-safe copy | Implemented |
| Teaching assistant video player | Generated MP4 can play inside assistant panel | Implemented |
| YouTube-style controls | Play/pause/seek/speed/volume controls available | Implemented |
| Candidate capture notice | Integrity capture text moved to bottom/collapsed section | Implemented |
| Architecture documentation | Technical Architecture tab includes diagrams | Implemented |

## Validation Commands

### Voice Environment

```bash
conda activate voice
PYTHONNOUSERSITE=1 python -c "import numpy, scipy, torch; print('numpy', numpy.__version__); print('scipy', scipy.__version__); print('torch', torch.__version__)"
COQUI_TOS_AGREED=1 PYTHONNOUSERSITE=1 python -c "from TTS.api import TTS; TTS('tts_models/multilingual/multi-dataset/xtts_v2'); print('XTTS model load OK')"
```

### Latest Output Check

```bash
cd "/mnt/c/Users/AnubhaAnubha/OneDrive - Pearce Services, LLC/onedrive_ubuntu/project/chatbot3"
latest_dir=$(find lipsync_renders -mindepth 1 -maxdepth 1 -type d -printf "%T@ %p\n" | sort -n | tail -1 | cut -d' ' -f2-)
cat "$latest_dir/manifest.json" | python -m json.tool | grep -E "authorized_voice_sample|voice_generation_mode|tts_audio"
```
