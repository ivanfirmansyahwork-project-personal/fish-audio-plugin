# Fish Audio plugin

Connects Claude to the [Fish Audio MCP server](https://docs.fish.audio/overview/mcp) (`https://api.fish.audio/mcp`, streamable HTTP) and adds skills for the most common audio workflows.

## Setup
1. Install the plugin.
2. When prompted, sign in to Fish Audio in the browser window (OAuth) and choose the team to use. A connection is tied to one team; to switch teams, reconnect and pick another.
3. Usage is billed through the Fish Audio web app. Video generation requires a Plus plan or higher.

## Skills
- **text-to-speech** - find a voice and generate narration or voiceover.
- **voice-cloning** - create a custom voice from a recording of one speaker (rights confirmation required).
- **transcription** - transcribe audio or video files to text.
- **story-studio** - build, edit, and export long-form multi-speaker audio projects.

## Notes
- The server exposes 47 tools (voices, speech, uploads, image/video, Story Studio, asset library, account). Tool arguments are provided by the server on connect.
- Credit-spending actions (speech, Story Studio audio, media generation) should be quoted before running.
