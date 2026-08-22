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

## Global styling

A whole-project look request ("warmer tone", "make it monochrome") is a
`settings` change, sent alongside `yamlText` on `updateProject`. Settings
replace rather than merge on this surface, so read the current ones with
`getProjectMetadata` first and resend every field you want to keep.

Values are exact, and they are wire values rather than the labels shown in the
app: write `material-darker`, never "Material Darker", and `forest`, never
"Forest". An unrecognized field is rejected rather than ignored.

    settings:
      theme: material-darker
      terminalTheme: Gruvbox
      mermaidTheme: monochrome
      backgroundColor: "#17130F"
      foregroundColor: "#F2EADF"

`theme` (lowercase-hyphen): dark-plus, dracula-soft, dracula, github-dark, github-dark-dimmed, github-light, light-plus, material-darker, material-default, material-lighter, material-ocean, material-palenight, min-dark, min-light, monokai, nord, one-dark-pro, poimandres, slack-dark, slack-ochin, solarized-dark, solarized-light.

`terminalTheme` (PascalCase): Ayu, Catppuccin, Dracula, Gruvbox, Monokai, Nord, OceanicNext, Solarized, SolarizedLight, Tomorrow.

`mermaidTheme` (lowercase): default, ocean, forest, monochrome, vibrant, pastel.

Other fields: agent, backgroundColor, backgroundImage, foregroundColor, intro, subtitle, useWatermark, watermarkText. There is no `palette`, `accent`, or semantic
colour field; do not invent one.
