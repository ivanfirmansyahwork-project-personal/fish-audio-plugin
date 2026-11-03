---
name: transcription
description: This skill should be used when the user asks to "transcribe this audio", "speech to text", "get a transcript", "convert this recording to text", or provides an audio/video file or link to transcribe with Fish Audio.
---

# Transcription with Fish Audio

Convert speech in audio or video into text.

## Workflow

1. **Get the file as an HTTPS link**:
   - If the user gives a direct HTTPS link, use it.
   - If it is a local file, call `get_upload_url`, then upload the file (or give the user the upload link to use in their browser where the client cannot upload). Use the resulting direct link.
2. **Pick the model**: `speech_to_text` uses `pro` by default and accepts a language hint, so ask for or infer the spoken language. Use `flash` when the user wants a cheaper, faster pass.
3. **Transcribe**: call `speech_to_text` with the link (and language hint if known).
4. **Deliver**: return a clean transcript. Offer extras: speaker-turn formatting, removal of filler words, a summary, key points and action items, or a saved file.

## Guidelines
- Preserve what was said; mark unclear passages as [inaudible] instead of guessing.
- Fix only obvious formatting (punctuation, paragraphs) unless the user asks for a cleaned version, and say which version is shown.
- Link expiry: temporary upload links expire, so transcribe promptly after upload.
