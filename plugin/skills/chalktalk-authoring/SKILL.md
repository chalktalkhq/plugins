---
name: chalktalk-authoring
description: "Author or edit a ChalkTalk tutorial video: load ChalkTalk's authoring guidance, then write and check the project. Use when: creating, restructuring, or reviewing a ChalkTalk video project. Skip when: the task does not involve a ChalkTalk project."
metadata:
  source: chalktalk
---
# ChalkTalk authoring

## Load the guidance first

1. Call `listSkills` for the catalogue - each entry carries a `whenToUse` line.
2. Call `loadSkill` for the ones that apply. At most three per turn, and never
   reload one already loaded in this conversation.
3. Only then author or edit the project.

Skipping this produces videos that parse but read badly: wrong step types, code
that overflows the frame, narration that fights the visuals.

## Authoring loop

`createProject` or `updateProject` replace the whole YAML document - there are
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
