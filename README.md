# FilmCraft video-editing skill

A reusable agent skill for editing video with FilmCraft. It guides an agent to inspect footage before choosing a treatment, pick pacing and transitions to suit the material and purpose, make reversible edits, and verify the export.

## Contents

- `SKILL.md` — workflow and safety rules for an agent using FilmCraft.
- `references/cli-and-mcp.md` — command discovery, project handling, previews, exports, and verification.
- `references/editing-playbook.md` — footage-led style selection, pacing, silence removal, and transitions.

The skill expects FilmCraft CLI or an already available FilmCraft MCP connection. It tells the agent to inspect the installed version and command schemas instead of assuming commands from a different release.

## Install

Copy this repository into your agent's skills directory as `filmcraft-video-editing/`, preserving the `references/` folder. For Codex, that is typically `~/.codex/skills/filmcraft-video-editing/`. Restart or refresh the agent so it can discover the skill.

## References

- [FilmCraft agent guide](https://github.com/storytold/filmcraft/blob/main/docs/agents.md)
- [FilmCraft README](https://github.com/storytold/filmcraft/blob/main/README.md)
- [FilmCraft releases](https://github.com/storytold/filmcraft/releases)
