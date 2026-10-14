---
name: filmcraft-video-editing
description: Use FilmCraft CLI or MCP to inspect, plan, edit, and export video, choosing a visual and pacing style that fits the supplied footage.
---

# FilmCraft video editing

Use this skill when the user wants FilmCraft to edit or export video, including when they want the agent to choose an appropriate edit style from their footage. Work through FilmCraft's installed CLI or already available MCP tools. Do not treat this as a guide to developing FilmCraft itself.

## Working method

1. **Discover the actual installation.** Locate the user's FilmCraft executable or available FilmCraft MCP server. Read its version and current help/command catalog before editing. For the CLI, start with `filmcraft-cli --version`, `filmcraft-cli --help`, `filmcraft-cli commands <filter>`, and `filmcraft-cli describe <command-id>`. For MCP, inspect its tools and command catalog first. The CLI and command set change quickly; do not copy a command or parameter from an older project or online guide without checking the installed version. Do not update, install, or start a desktop bridge unless the user requests it or the task already establishes that workflow.

2. **Inspect before choosing a treatment.** Probe each source for duration, frame size, frame rate, codecs, and audio streams. Inspect the project timeline if one exists. View representative frames across the footage (and listen to representative audio when available); metadata alone cannot reveal subject, motion, scene changes, screen content, or intentional quiet. Read [the editing playbook](references/editing-playbook.md) to choose pacing, transitions, and visual treatment from the material and the user's purpose. Make a good default choice and proceed when the request is clear; ask only when an unknown would materially change the edit.

3. **Keep source and edit reversible.** Leave source media untouched. Save the edit as a new `.fcproj` in the task's output folder, with output media beside it. If the user gave an existing project to continue, work on a copy unless they clearly asked to overwrite it. Use FilmCraft commands and supported project operations; do not hand-edit the binary/project internals. Before batching timeline changes, check command schemas and exact clip IDs with `describe`, `inspect`, and a small reversible preview where useful.

4. **Build the requested edit.** Preserve the source's intended orientation, aspect ratio, and sync unless the user asks for a change. Keep dialogue and meaningful action intact. Treat silence detection, transcript suggestions, and scene-change detection as candidates for review, not proof that content is disposable. If asked to remove silence, cut long dead air while retaining word boundaries and a little natural room tone; do not remove quiet emotional beats or music. Apply transitions only where they serve the cut: by default use clean cuts, and use dissolves for a clear shift in time, place, mood, or the user's explicit request. Keep audio transitions aligned with picture.

5. **Preview and deliver.** Inspect the edited sequence, render frames at the opening, a representative middle, the ending, and edit joins, then view them. Export with a format suited to the destination, preserving quality and aspect ratio. Wait for export completion. Probe the exported file and decode it end to end; review the joins and audio when tools permit. If verification is limited, say exactly what was checked. Deliver the video and editable FilmCraft project, and state the treatment, duration, and material limitations.

## FilmCraft operating references

- Read [CLI and MCP operations](references/cli-and-mcp.md) for command discovery, safe project workflows, batch commands, previews, and export.
- Read [the editing playbook](references/editing-playbook.md) for footage-led style selection, silence removal, transitions, and rhythm.
- For details beyond those references, prefer the installed CLI's `--help`, `commands`, and `describe` output, then FilmCraft's [agent guide](https://github.com/storytold/filmcraft/blob/main/docs/agents.md), [README](https://github.com/storytold/filmcraft/blob/main/README.md), and [release notes](https://github.com/storytold/filmcraft/releases/latest).
