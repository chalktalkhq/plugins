# ChalkTalk plugin

<!-- GENERATED — run `pnpm plugin:build` in the ChalkTalk repo. Do not edit by hand. -->

Connects ChalkTalk to Claude and ChatGPT through one remote MCP server at
`https://frameflow1.vercel.app/api/mcp`. Sign-in happens on first use via OAuth; there is no API key to paste.

## Claude Code

```
/plugin marketplace add chalktalkhq/plugins
/plugin install chalktalk@chalktalk-plugins
```

Then run `/mcp` inside Claude Code to sign in.

This works straight off the git repo — **nothing has to be published**. Anyone
with read access to `chalktalkhq/plugins` (including a private repo, via their own git
credentials) can run those two lines. Submitting to a directory only affects
whether strangers can *discover* it, not whether it can be installed.

Other ways to share privately:

- **Skip the plugin entirely** — `claude mcp add --transport http chalktalk https://frameflow1.vercel.app/api/mcp`.
  One line, no repo access needed. Loses the bundled skills.
- **A whole team, zero steps** — commit `extraKnownMarketplaces` and
  `enabledPlugins` to `.claude/settings.json` in the team's own repo; the
  plugin loads for everyone who opens it.
- **Local checkout** — `/plugin marketplace add /path/to/this/repo` for testing
  before anything is pushed.

## Claude Desktop, claude.ai, mobile

Plugins do not reach these surfaces. Add the server directly instead:
Settings → Connectors → Add custom connector → `https://frameflow1.vercel.app/api/mcp`.

## ChatGPT

Settings → Security and login → enable Developer mode, then
Plugins → "+" → Public endpoint → `https://frameflow1.vercel.app/api/mcp`.

## What's inside

- `.mcp.json` — points Claude Code at the hosted ChalkTalk MCP server
- `skills/chalktalk-authoring/` — a bootstrap skill that tells the agent to load
  ChalkTalk's authoring guidance over MCP before writing YAML

## Where the real skills live

ChalkTalk's eight authoring skills are **not** bundled here. They are served by
the MCP server through the `listSkills` and `loadSkill` tools, behind the
`chalktalk:read` OAuth scope.

That is deliberate, and better than shipping copies:

- **Always current.** You get the guidance as it is deployed, not whatever was
  frozen into the plugin when you installed it.
- **One source of truth.** The same markdown drives the ChalkTalk web app and
  every MCP client, so they cannot drift apart.
- **Nothing to re-install.** Improvements land for existing users immediately.

The bootstrap skill exists because a file-based plugin is what makes ChalkTalk
discoverable in Claude Code's `/` menu at all; it carries no guidance of its own.
