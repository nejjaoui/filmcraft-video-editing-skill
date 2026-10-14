# FilmCraft CLI and MCP operations

FilmCraft offers a CLI for headless editing and an MCP server that can drive either a headless project or a running desktop app. The CLI is the straightforward choice for file-based work. Use an already available MCP connection when the user is working in the live app or asks for it. Never assume that this machine's executable path, installed release, or command schema matches a sample.

## Discover, then act

Check the executable and version, then inspect its local help. Typical CLI entry points are:

```sh
filmcraft-cli --version
filmcraft-cli --help
filmcraft-cli commands import
filmcraft-cli describe mediaBrowser.import
filmcraft-cli --project edit.fcproj inspect
filmcraft-cli probe input.mp4
```

Use `commands <filter>` to find commands and `describe <id>` to get parameters. Inspect project and sequence state before relying on numeric IDs; IDs are project-specific. The CLI supports `probe` for container, duration, streams, frame size/rate, and audio properties. Sample frames through supported FilmCraft render/export-frame commands or a local video inspection tool so style choices are grounded in what the footage shows.

## Save safely and batch edits

Keep the source media unchanged. For a new edit, save into a new project path. For an existing project, copy it first unless overwriting was explicitly requested. The CLI supports `--project`, `--save`, and `--save-as`; prefer an explicit destination path for the edited project.

Use `exec` for one command and `run <script.jsonl>` for a planned batch. Each JSONL line is one command object:

```json
{"id":"command.id","params":{"key":"value"}}
```

Build a batch only after discovering the current command IDs and parameter types. Use `--keep-going` only when later commands remain safe after an earlier failure. Read every result; `run` reports failures per line. Re-inspect the sequence after timeline changes to confirm clip order, source ranges, tracks, transitions, and total duration.

Time is represented internally in integer ticks (the CLI help documents the ticks-per-second value); commands may accept seconds, frames, or timecode. Prefer frame-based placement for frame-accurate edits and use the sequence frame rate. Do not round source cuts in a way that moves them across a spoken word or action.

## Preview, export, and verify

Render several representative Program frames with the installed `render` command or export-frame command. Check the start and end of every type of edit, not just the title frame. When a transition is central to the request, preview the frames spanning that transition.

Use FilmCraft's export command for the final render whenever it can satisfy the requested format and quality. Select the sequence and a suitable preset/format explicitly when needed. Wait for a blocking export to finish; for an asynchronous job, poll the documented job status rather than assuming that a started export succeeded. Do not export over source media.

Verify the output's duration, dimensions, frame rate, video/audio streams, and successful full decode with FilmCraft `probe` plus a local media inspector when available. Listen to representative cuts for clipped words, abrupt ambience, clicks, or audio drift. If an external renderer is necessary because the installed FilmCraft build cannot complete the requested render, preserve the FilmCraft edit project, disclose the alternate renderer in the handoff, and verify the result independently.

## MCP

If a FilmCraft MCP server is already available, inspect its tool list and project/sequence resources first. Current official documentation describes tools such as `command_list`, `command_run`, `command_batch`, `doc_inspect`, and `render_preview`; exact availability depends on the installed server. A headless server edits an in-process project; bridge mode controls the running desktop app. Use the mode appropriate to the task and never launch a listener or change MCP configuration without authorization. MCP has access to files available to the process, so keep operations within the paths the user provided or the task workspace.

Official references: [FilmCraft agent guide](https://github.com/storytold/filmcraft/blob/main/docs/agents.md), [FilmCraft README](https://github.com/storytold/filmcraft/blob/main/README.md), [latest releases](https://github.com/storytold/filmcraft/releases/latest).
