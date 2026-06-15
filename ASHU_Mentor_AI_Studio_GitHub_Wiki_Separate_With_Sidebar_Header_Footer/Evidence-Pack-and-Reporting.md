# Evidence Pack & Reporting

ASHU Mentor AI Studio separates candidate evidence capture from the digital presenter generation pipeline.

## Evidence Categories

| Evidence Type | Purpose |
|---|---|
| Candidate transcript | Supports evaluation and feedback generation |
| Candidate recording | Optional performance review and integrity evidence |
| Screen/focus events | Supports audit trail and candidate-session monitoring |
| Screenshots | Optional visual evidence for reports |
| Voice/video generation logs | Debugging and reproducibility for digital presenter generation |
| Final report | Summarizes candidate strengths, gaps, and recommendations |

## Generated Media Evidence

Every lecture render can store:

```text
manifest.json
voice_generation_run.log
renderer_run.log
tts_audio.script.txt
tts_audio.wav
final MP4
browser-safe MP4
```

## Example Manifest Fields

```json
{
  "tts_audio": ".../tts_audio.wav",
  "authorized_voice_sample": ".../voice_samples/authorized_voice_recording.wav",
  "voice_generation_mode": "authorized_voice_sample_xtts_if_available",
  "renderer": "SadTalker",
  "browser_safe_video": ".../talking_presenter_output_browser.mp4"
}
```

## Report Outputs

The candidate report should include:

1. Candidate profile summary
2. Interview round summary
3. Question-wise assessment
4. Coding-round observations
5. Communication and clarity feedback
6. Technical strengths
7. Improvement areas
8. Adaptive training recommendations
9. Evidence/log references
10. Final readiness rating
