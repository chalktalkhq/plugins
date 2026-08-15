# ChalkTalk

Turn a conversation into a narrated tutorial video — without leaving your editor.

ChalkTalk writes the video as a structured document: scenes for code, diagrams,
charts, CLI sessions, and maths, each with its own narration. Ask for a
walkthrough of the function you just wrote and it drafts the scenes, checks them,
and renders preview frames it can actually look at. You review and export in
ChalkTalk.

## Install

**Claude Code**

```
/plugin marketplace add chalktalkhq/plugins
/plugin install chalktalk@chalktalk-plugins
```

Then run `/mcp` to sign in.

**Claude Desktop, claude.ai, mobile** — Settings → Connectors → Add custom
connector, and paste:

```
https://frameflow1.vercel.app/api/mcp
```

**ChatGPT** — Settings → Security and login → turn on Developer mode, then
Plugins → **+** → Public endpoint, and paste the same URL.

**Cursor, VS Code, Codex, Windsurf, and anything else** — one-click installs and
copy-paste config for every client: [frameflow1.vercel.app/mcp](https://frameflow1.vercel.app/mcp)

No API key. You sign in once in the browser on the first tool call.

## Try it

- "Make a 90-second video explaining this pull request."
- "Turn this function into a code walkthrough with narration."
- "Start from the binary search template and show me the first scene."
- "Check my project for pacing problems and show me frame 3."

## What it can do

| | |
|---|---|
| **Author** | Create, update, duplicate, and delete video projects |
| **Explore** | Search and fetch your projects and the template catalogue |
| **Check** | Validate structure, report pacing and writing problems |
| **See** | Render preview frames the agent can inspect before you commit |
| **Narrate** | Generate voiceover from narration you have approved |

Rendering runs in ChalkTalk rather than over the connector, so you review the
video before spending render time on it.

## Links

- [ChalkTalk](https://frameflow1.vercel.app)
- [Connect your AI tools](https://frameflow1.vercel.app/mcp)
- [Issues](https://github.com/chalktalkhq/plugins/issues)

<sub>This repo is generated from the ChalkTalk app repo — open an issue rather
than a pull request against these files.</sub>
