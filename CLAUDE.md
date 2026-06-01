# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About This Workspace

This is Man Li's **career management workspace** — a project management workspace for tracking companies, roles, opportunities, decisions, and career-related research. It is **not a code project** — there are no build, test, or lint commands.

## Folder Map

| Folder | Purpose |
|--------|---------|
| `companies/` | SSOT: company profiles + project registry (team contacts, project details, cross-references) |
| `topics/` | Topic-based research, drafts, and converted files |
| `00-Incoming/` | Staging zone for dropped files before ingestion — process then move originals to archive |
| `88-outgoing/` | Drafts and sent items for external deliverables |
| `issues/` | Issue tracking with status, owner, and project tags |
| `decisions/` | Key project decisions with context and rationale |
| `risks/` | Project and operational risks with mitigation tracking |
| `knowledge/` | Reference knowledge base |
| `meetings/` | Meeting templates and minutes |

## Active Engagement

**Marketo B2B Marketing Global Rollout** — RFP response for CHINT (正泰) via GenOptima.

| Role | Entity | Detail |
|------|--------|--------|
| End client | [[CHINT]] (正泰) | $64.5B electrical group, 22 countries, Marketo + Dynamics CRM |
| Prospect | [[GenOptima]] (Leon Dai, CEO) | Singapore-based, AI/GEO marketing |
| My role | Solution Architect | Subcontracted through GenOptima, leading a fresh team member |
| Deadline | 2026-06-08 | RFP proposal presentation (dry-run Jun 5, proposal complete Jun 4) |
| Deliverable | `88-outgoing/proposal-chint-marketo-v1.md` | 14-slide keynote, motion-centric automation |
| Topic | `topics/TOPIC-001-chint-marketo-rfp/` | Status: in-progress, priority: high |

## Key Registries

- **`companies/README.md`** — SSOT for all companies and projects (profiles, team contacts, project registry)

## Ingestion Rules

`00-Incoming/` is a **temporary staging zone**. Files dropped there must be processed promptly and then moved to the shared archive.

- **Shared archive:** `~/Documents/_ingested-work/CAREER/` — the permanent, cross-project SSOT for all raw ingested files
- **Workflow:** File lands in `00-Incoming/` → AI extracts info and updates repo files → original moves to `_ingested-work/CAREER/`
- **Never delete originals.** The `_ingested-work/` copy is the audit trail
- **Never write processed output to `_ingested-work/`.** That folder is read-only archive — output goes to this repo's own folders

### Ingestion Routing — Which Content Goes Where

When extracting information from an ingested file, route each piece to its exact target. One ingestion file may update multiple targets — that's expected.

| Content type | Target file | Action |
|-------------|-------------|--------|
| New company (not in registry) | `companies/README.md` | Add row to relevant table (Internal / Clients / Partners) |
| New company profile | `companies/<shortcode>/README.md` | Create new file using the structure from an existing profile |
| Existing company — team contacts, structure, operations | `companies/<shortcode>/README.md` | Update the relevant section in-place |
| New issue, follow-up, action item | `issues/ISSUE-NNN-slug.md` | Create from `issues/issue-template.md`, assign next available number |
| Key decision made | `decisions/DECISION-NNN-slug.md` | Create from `decisions/decision-template.md`, assign next available number |
| Risk or concern identified | `risks/RISK-NNN-slug.md` | Create from `risks/risk-template.md`, assign next available number |
| Topic research, discussion prep, drafts | `topics/TOPIC-NNN-slug/` | Create topic folder from `topics/README.md` naming convention |

**Routing rules:**
- If unsure which company a piece of content belongs to, ask — don't guess
- If content spans multiple companies, update each company profile separately
- Always check the existing target file first before writing — don't duplicate what's already there

## Conventions

- Never delete original files. Processed files move from `00-Incoming/` to the ingestion archive
- Company profiles use `[[Company Name]]` cross-references
- Before changing approved docs, ask for explicit confirmation
- If unsure which target a piece of content belongs to, ask — don't guess
