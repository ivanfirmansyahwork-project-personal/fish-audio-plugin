---
name: text-to-speech
description: This skill should be used when the user asks to "generate speech", "read this aloud", "make a voiceover", "narrate this text", "text to speech", "find a voice", or wants audio from text using Fish Audio.
---

# Text-to-Speech with Fish Audio

Turn text into spoken audio using the Fish Audio connector.

## Workflow

1. **Clarify only what is missing**: language, tone (calm, energetic, formal), and whether a specific voice is wanted. If the user gave none, pick sensible defaults and say so.
2. **Check limits**: call `get_credit_balance` to see remaining credits and the maximum text length per speech call for the plan. Mention low credit balance before spending.
3. **Choose a voice**:
   - Use `search_voices` to browse popular voices for the language, search the public library by keyword, or list the workspace's own voices (`self`).
   - Use `get_voice` to inspect a candidate (languages, tags, sample). Offer 2-3 options with the sample link when the user hasn't chosen.
   - If no voice is specified and the user is fine with it, use the default voice for the language.
4. **Prepare the text**: remove stray markup, expand unclear abbreviations, and split very long text into logical sections. Long text may return as several clips; present them in order.
5. **Generate**: call `text_to_speech` with the text and voice. Share the returned permanent audio link(s).
6. **Offer follow-ups**: try another voice, adjust wording, or save the result to the asset library with `save_asset`.

## Guidelines
- Keep the user's wording intact unless asked to edit; only normalize text for speech.
- For multi-speaker or book-length content, suggest the story-studio skill instead of many separate calls.
- Never claim audio was generated unless the tool returned a link.
