# ChalkTalk

Turn a conversation into a narrated tutorial video - without leaving your editor.

ChalkTalk writes the video as a structured document: scenes for code, diagrams,
charts, CLI sessions, and maths, each with its own narration. Ask for a
walkthrough of the function you just wrote and it drafts the scenes, checks them,
and renders preview frames it can actually look at. You review and export in
ChalkTalk.

## Install

| Client | How |
|---|---|
| Claude Code | Plugin - two commands below |
| Codex | Two CLI commands below |
| Cursor, VS Code | One click from [the install page](https://frameflow1.vercel.app/mcp) |
| Claude Desktop, claude.ai, mobile | Settings → Connectors → Add custom connector → server URL |
| ChatGPT | Settings → Security and login → Developer mode, then Plugins → **+** → Public endpoint → server URL |
| Windsurf, Antigravity | Config snippet below |
| Anything else | [The install page](https://frameflow1.vercel.app/mcp) has a prompt you can paste into your own agent |

**Claude Code**

```
/plugin marketplace add chalktalkhq/plugins
/plugin install chalktalk@chalktalk-plugins
```

Then run `/mcp` to sign in.

**Codex**

```
codex mcp add chalktalk --url https://frameflow1.vercel.app/api/mcp
codex mcp login chalktalk
```

**Windsurf, Antigravity** - merge into your MCP config. Windsurf keeps it at
`~/.codeium/windsurf/mcp_config.json`; Antigravity exposes it under
MCP Servers → Manage MCP Servers → View raw config.

```json
{
  "mcpServers": {
    "chalktalk": {
      "serverUrl": "https://frameflow1.vercel.app/api/mcp"
    }
  }
}
```

**Server URL**, for anything that just asks for one:

```
https://frameflow1.vercel.app/api/mcp
```

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

<sub>This repo is generated from the ChalkTalk app repo - open an issue rather
than a pull request against these files.</sub>
