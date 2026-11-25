---
name: archive
description: >-
  Archive inactive Claude Code session transcripts out of `~/.claude/projects/` into
  `~/.claude/archived_sessions/` and restore them when needed. Use when session lists in
  `claude --resume` or Zed's Agent Panel grow cluttered, when archiving old transcripts, or
  when restoring archived sessions.
---

# Archive Claude Code Sessions

Move inactive Claude Code session transcripts out of `~/.claude/projects/` into `~/.claude/archived_sessions/` to keep `claude --resume` and Zed's Agent Panel uncluttered, and restore them back to their original project directories on demand.

## Modes and options

- **Archive (default)**: Move matching transcripts older than the age cutoff (default `3` days) from `~/.claude/projects/<project>/` to `~/.claude/archived_sessions/<project>/`.
- **`restore [<pattern>]`**: Move matching archived transcripts back from `~/.claude/archived_sessions/<project>/` to `~/.claude/projects/<project>/`. Without a pattern, list available archived sessions and ask which to restore unless the user asked to restore all.
- **`--dry-run` / preview**: List the matching files, their project directories, and their destinations without moving anything.
- **`--days <N>`**: Override the default 3-day age cutoff based on file modification time.
- **Project filter**: Restrict archiving or restoration to one or more `<project>` directories when the user names a project, path, or slug.

## Archive

Inspect top-level `*.jsonl` transcripts directly under `~/.claude/projects/<project>/`. Leave subdirectories, project memory, settings, and non-transcript files untouched.

Exclude transcripts that should stay active:

- `agent-*.jsonl` subagent files.
- The currently active session transcript and any transcript modified more recently than the age cutoff, or held open by a live process (`lsof` when available).

Create `~/.claude/archived_sessions/<project>/` as needed and move each selected transcript without overwriting an existing file at the destination. If a destination path already exists, skip the move, keep both files intact, and report the collision.

## Restore

Search `~/.claude/archived_sessions/<project>/*.jsonl` for files matching `<pattern>` against the session filename or project directory name, respecting any project filter. Move each selected file back into `~/.claude/projects/<project>/` without overwriting an existing file there, skipping and reporting any collision. Once restored, the sessions reappear in `claude --resume` and Zed's Agent Panel.

## Report

Summarize how many transcripts were moved (or would move on a dry run), grouped by project, along with any skipped collisions or excluded active sessions. If nothing matched, say so.
