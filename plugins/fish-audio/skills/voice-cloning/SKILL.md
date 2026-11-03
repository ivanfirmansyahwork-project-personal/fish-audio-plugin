---
name: voice-cloning
description: This skill should be used when the user asks to "clone a voice", "create a custom voice", "make a voice from this recording", "verify a voice clone", or wants a Fish Audio voice that sounds like a specific speaker.
---

# Voice Cloning with Fish Audio

Create a reusable voice from recordings of a single speaker.

## Consent first
Voice cloning requires the user to confirm they have the rights to the voice (it is their own voice, or they have the speaker's permission). Ask for this explicitly before calling `create_voice_clone`. If the user cannot confirm, or the voice belongs to a public figure or someone who has not agreed, decline to proceed and explain why.

## Workflow

1. **Collect the sample**: ask for clean recordings of one speaker only. Guidance to share: quiet room, no music or background voices, natural speaking, consistent mic, roughly 10-60 seconds or more of clear speech.
2. **Upload**: for local files, call `get_upload_url`. Where the client can upload, upload the file; otherwise (e.g. claude.ai) give the user the upload link to open in their browser. Warn that anyone with the link can upload until it expires, so it should not be shared.
3. **Create the clone**: after consent is confirmed, call `create_voice_clone` with the sample(s) and a descriptive name. Cloning is free.
4. **Verify if required**: if the result says speaker verification is needed, share the passage Fish Audio provides, have the speaker record themselves reading it, upload it, and call `verify_voice_clone`.
5. **Test**: generate a short sample with `text_to_speech` using the new voice and share the link. Offer to adjust by adding cleaner or additional recordings.

## Guidelines
- Never clone from a recording that mixes multiple speakers.
- Do not retry failed verification repeatedly; explain what to improve (clarity, passage fully read).
