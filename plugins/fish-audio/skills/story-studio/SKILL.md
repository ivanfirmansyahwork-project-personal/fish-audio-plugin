---
name: story-studio
description: This skill should be used when the user asks to "make an audiobook", "create a multi-speaker audio drama", "turn this script/article into audio", "build a Story Studio project", "export a chapter as MP3", or wants long-form audio with different voices per character.
---

# Story Studio with Fish Audio

Story Studio projects contain chapters, chapters contain blocks (paragraphs or headings), and each block has its own voice. These tools edit the same projects as the Story Studio web editor, so changes appear live if the user has it open.

## Workflow

1. **Orient**: call `studio_help` when unsure about a feature. Use `studio_list_projects` to see existing projects and `studio_project` to inspect one (chapters, blocks needing audio, voices in use, import/export status).
2. **Create or import**:
   - Existing text (novel, script, article): `studio_import_document`. It splits into chapters, casts voices, and adds audio tags. The project is read-only until import finishes, so check `studio_project` for status.
   - Original content: write chapters and blocks, then `studio_create_project`.
3. **Cast voices**: use `search_voices` / `get_voice` to choose voices per character or narrator. Set defaults with `studio_update_project`; switch a whole speaker with `studio_recast_speaker`.
4. **Edit**: `studio_read_blocks` and `studio_find` to review, `studio_write_blocks` to edit, insert, move or delete blocks, `studio_create_chapter` / `studio_update_chapter` for chapters. Use `studio_enhance_text` to prep a block for speech (numbers, dates, symbols, audio tags).
5. **Quote cost before audio**: importing and editing are free; audio costs credits. Before `studio_generate` or `studio_export`, check `get_credit_balance`, state which blocks need audio and the expected cost, and proceed only after the user confirms.
6. **Generate**: `studio_generate` for blocks, a chapter, or the whole project. Only blocks that need audio are processed unless a redo is requested. Review with `studio_list_takes`; revert for free with `studio_adopt_take` when an earlier take still matches the text.
7. **Export**: `studio_export` as MP3 or WAV, optionally with subtitles, after the user confirms credits for any blocks still needing audio. Share the resulting link.

## Guidelines
- No Story Studio tool deletes projects or chapters; tell the user to delete those in the web editor.
- Start with a small chapter test before generating a whole book, to confirm voices and tone.
- Keep a short summary of changes made to the project after each editing session.
