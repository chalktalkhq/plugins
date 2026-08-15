---
name: chalktalk-authoring
description: "Author or edit a ChalkTalk tutorial video. Loads ChalkTalk's own authoring guidance over MCP before writing any project YAML. Use when: creating, restructuring, or reviewing a ChalkTalk video project. Skip when: the task does not involve a ChalkTalk project."
metadata:
  source: chalktalk
---
# ChalkTalk authoring

ChalkTalk's authoring guidance is served by the ChalkTalk MCP server, not
bundled into this plugin, so it is always current. Load it before writing YAML.

## Do this first

1. Call `listSkills` to get the catalogue with a `whenToUse` line for each entry.
2. Call `loadSkill` for the ones that apply — at most three per turn, and never
   reload one you already loaded in this conversation.
3. Only then author or edit the project.

Skipping this produces videos that parse but read badly: wrong step types, code
steps that overflow the frame, narration that fights the visuals.

The catalogue is deliberately not listed here — `listSkills` returns the live set
with a `whenToUse` line for each, so this file never goes stale against it.

## Authoring loop

`createProject` or `updateProject` replace the whole YAML document — there are
no partial-edit tools on this surface, so read before you write:

1. `getProjectMetadata` for the step outline, or `fetchGvid` with
   `includeYaml: true` for the full document.
2. `validateYaml` on your draft before sending it.
3. `createProject` / `updateProject`.
4. `getDiagnostics` for pacing and writing warnings.
5. `previewStepStills` to actually look at the frames.

Rendering is deliberately not exposed here. On success, give the user the
`title` and `editorUrlAbsolute` from the response so they can review and export
in ChalkTalk.
