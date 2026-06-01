# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About this workspace

This is a project management workspace, not a code repository. It follows a company-first folder structure where each company gets its own project directory.

## Structure

- `CAREER.code-workspace` — VS Code workspace file
- Company-named folders (e.g., `acme-corp/`, `startup-x/`) — each holds that company's project files, notes, and artifacts

## Workflow

- Processed raw files move from `raw/new/` to `raw/ingested/`
- Chatter or wait-state items move to `raw/hold/`
- Never auto-delete raw files
- Preserve original filenames for raw files
- For ambiguous company/project identity, ask once

## Related config

Global preferences live in `~/.claude/CLAUDE.md` and `~/.claude/rules/man-working-style.md`. Main knowledge vault is at `~/KMS`.
