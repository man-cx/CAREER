# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working in this folder.

## About This Workspace

Man Li's **career wiki** — work history, engagements, and reference material. It is **not a code project** — there are no build, test, or lint commands.

## Folder Map

| Item | Purpose |
|------|---------|
| `Projects/` | Man's work history — one folder per engagement, each with its own `README.md` |
| `_archive/` | Retired career workspace — frozen, read-only. See `_archive/README.md` |

## The Notion CRM

This folder reads Man's Notion CRM — Company-DB, Contact-DB, Activity-DB — through **mcp-crm**, the governed service at `https://mcp-crm.zeabur.app`. Career is one **client** of it; the service is external and is not built or changed from here.

- **Read-only.** The key's identity is `verify`, scope `read` — look-ups work, writes are refused. A write-scoped key is Man's decision, not an oversight
- **Registered for this folder only**, local scope, key held in `~/.claude.json`. It must never enter this repo — `--scope project` writes a `.mcp.json` carrying the key into git
- Servers load at session start, so a newly registered server appears from the **next** session

## Working Rules

- **`_archive/` is frozen.** Do not edit, move, rename or delete its contents — it is historical record. `Projects/` is **not** frozen (unfrozen 2026-09-21): its contents may be edited, but treat it as history — change it deliberately, not casually
- **Keep the top level simple.** New career content goes at the root; add a folder only when there is real content to fill it
- Before changing approved docs, ask for explicit confirmation
- If unsure where a piece of content belongs, ask — don't guess
