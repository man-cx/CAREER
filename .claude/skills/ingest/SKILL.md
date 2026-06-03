---
name: ingest
description: Process files from 00-Incoming/ — extract information, route to the correct workspace targets, and move originals to ~/Documents/_ingested-career/.
allowed-tools: Read, Write, Edit, Bash
---

## Overview

Process files dropped in `00-Incoming/` by extracting information, routing each piece to its correct target in the workspace, then moving originals to the ingestion archive. Never delete originals.

## Steps

### 1. Scan for items to process

Scan for both individual files and subfolders in `00-Incoming/`:

```bash
# List all items, excluding framework files and known local-only folders
ls 00-Incoming/ | grep -v -E '^README.md$|^\.DS_Store$|^Man-experiences$|^ZAN$'
```

Skip: `README.md`, `.DS_Store`, `Man-experiences/`, `ZAN/`, and any folder listed in `.gitignore`.

If nothing found, report: "00-Incoming is empty — nothing to ingest."

**Item types:**
- **Single file** — process it directly (step 2)
- **Subfolder** — process each file inside individually through routing, but archive the folder as a unit (step 3)

### 2. Process each file

For each file found:

**a. Read and classify the content.** Determine what type of information the file contains:
- Company profile / team contacts / project details
- Issue, task, follow-up, or action item
- Decision or rationale
- Risk or concern
- Research, topic reference, or discussion material
- Meeting notes or minutes
- Resume, CV, job description, or career artifact
- Mixed — spans multiple categories

**b. Route to targets.** Use this routing table to write content to the correct place:

| Content type | Target | Action |
|-------------|--------|--------|
| New company (not in registry) | `companies/README.md` | Add row to the relevant table |
| New company profile | `companies/<shortcode>/README.md` | Create from `companies/company-template.md` |
| Existing company — contacts, structure, projects | `companies/<shortcode>/README.md` | Update the relevant section in-place |
| New issue, follow-up, action item | `issues/ISSUE-NNN-slug.md` | Create from `issues/issue-template.md`, assign next number |
| Key decision | `decisions/DECISION-NNN-slug.md` | Create from `decisions/decision-template.md`, assign next number |
| Risk or concern | `risks/RISK-NNN-slug.md` | Create from `risks/risk-template.md`, assign next number |
| Topic research, drafts | `topics/TOPIC-NNN-slug/` | Create folder with `README.md` + supporting files |
| Meeting notes | `meetings/minutes/<date>-<topic>.md` | Create from `meetings/meeting-template.md` |
| Career artifact (CV, cert, reference) | `knowledge/` or update relevant company profile | File under `knowledge/career/` or attach to company |
| Reference / learning material | `knowledge/` | Place in an appropriate subfolder |

**Routing rules:**
- One file may update multiple targets — process each piece independently
- Check the existing target file first before writing — do not duplicate what's already there
- If unsure which company a piece belongs to, ask — don't guess
- If content spans multiple companies, update each company profile separately
- If a file contains only chatter or no actionable content, move it directly to the archive without creating workspace entries

### 3. Move originals to archive

**For individual files:** Move to `~/Documents/_ingested-career/` flat.

- Preserve original filename
- If a name collision: prepend ingestion date (`2026-06-03-<filename>`)
- If the date-prefixed name also collides: append `-2` (or next number)

**For subfolders:** Move the entire folder to `~/Documents/_ingested-career/`, preserving its internal structure.

- Prepend ingestion date to the folder name: `project-docs/` → `2026-06-03-project-docs/`
- If the date-prefixed folder name collides: append `-2`
- Files inside the folder keep their original names (no date prefix needed — the folder name provides context)

**Rationale:** Individual files go flat because their origin context is in the filename itself. Subfolders are preserved as units because the folder structure carries meaning (e.g., a project dossier with attachments).

### 4. Summary report

For each item processed, list all targets updated:

```
report.pdf
  → companies/acme/README.md (updated contacts)
  → issues/ISSUE-003-shipping-delay.md (new)
  → Archive: ~/Documents/_ingested-career/2026-06-03-report.pdf

project-docs/  (3 files)
  → companies/acme/README.md (updated)
  → risks/RISK-001-budget-cut.md (new)
  → Archive: ~/Documents/_ingested-career/2026-06-03-project-docs/
```

End with: "N items processed → M workspace targets updated. Archive: ~/Documents/_ingested-career/"

## Notes

- Never delete original files — only move them to the archive
- Individual files go flat; subfolders are preserved as units with date-prefixed names
- One file → many targets is normal — the workspace handles categorization, the archive is just the audit trail
