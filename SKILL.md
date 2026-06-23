---
name: apollo-lead-scoring
description: Apollo B2B company research, AnySearch evidence capture, Agent-led customer fit scoring, and Excel writeback workflows. Use when working on Apollo customer pools, lead scoring spreadsheets, scanner/digital signage/POS product directions, company website research, product-fit judgement, Chinese Apollo Excel files, or migrating this workflow between machines.
---

# Apollo Lead Scoring

## Core Rule

Use this skill for Apollo customer-pool workflows where companies are researched from Excel, evidence is gathered from websites/search/social pages, and an Agent writes customer type, score, fit reason, cut-in angle, and development advice back to the workbook.

Never let Python keyword matching decide the final customer score. Python only reads/writes Excel, captures evidence, caches AnySearch output, backs up files, and validates results. The Agent decides customer type, score, level, reason, cut-in angle, unsuitable reason, and final advice from website evidence, product boundaries, and salesperson feedback.

## Workflow

1. Read the project `agent.md` first when it exists.
2. Read the target workbook structure and headers.
3. Choose the product rule:
   - Digital signage: read `references/digital-signage-rules.md`.
   - Scanner: read `references/scanner-rules.md`.
   - POS: read `references/pos-rules.md`.
   - New product without a calibrated rule: read `references/product-index.md` and create/update a product rule from a suitable template.
4. Export evidence with `scripts/export_evidence.py`.
5. Have the Agent generate a judgement JSON. Use `references/excel-fields.md` for required JSON keys and Excel columns.
6. Write results with `scripts/write_judgements.py`.
7. Validate with `scripts/validate_workbook.py`.
8. Update the project `agent.md` with the run summary, distribution, caches, and lessons.

## Required Evidence Policy

Prefer evidence in this order:

1. Company website homepage, About, Products, Services, Solutions, CMS, Digital Signage, Auto-ID, POS, or product pages.
2. Search results only when they clearly belong to the target company.
3. Social pages only as low-weight support because LinkedIn/Facebook/X often fail extraction.
4. Apollo `Industry`, `Keywords`, and old script summaries are clues only, not high-score proof.

Do not score a company high because a search query, Apollo keyword, or unrelated result contains the product term.

## Excel Safety

- Always back up before writing.
- Set `freeze_panes = None` unless the user explicitly asks otherwise.
- Do not freeze row 10 or any other row by default.
- Preserve base company fields: Company ID, Company Name, Apollo Link, Website URL, All Social Links, Batch No., Batch Name, Industry, Keywords, Source File.
- Low and unsuitable rows must include `不适合原因`.
- Scores must be integers `0-100`; levels must match thresholds: 高 `80-100`, 中 `60-79`, 低 `40-59`, 不适合 `<40`.
- `社媒辅助评分调整` must be one of `0`, `3`, or `5`.

## Scripts

Use bundled scripts when useful:

```powershell
python scripts/export_evidence.py --target-xlsx <xlsx> --sheet <sheet> --out-dir <cache-dir> --prefix <run-name>
python scripts/write_judgements.py --target-xlsx <xlsx> --sheet <sheet> --judgements-json <json>
python scripts/validate_workbook.py --target-xlsx <xlsx> --sheet <sheet>
```

The scripts are intentionally generic. If a local project has more specialized scripts, prefer the project scripts after reading them, but keep this skill's role boundary: scripts move evidence and data; Agent judges.

## Encoding And Paths

For Chinese paths and Chinese worksheet names, read `references/encoding-and-path-notes.md` before writing scripts or running PowerShell commands. Use UTF-8 script files and `apply_patch`; avoid PowerShell here-strings for Chinese content.

## Git And Migration

This skill folder can be committed to Git. Read `references/git-and-migration.md` before preparing it for another computer or another model. Do not commit API keys, `.env`, live customer workbooks, or private caches unless the user explicitly asks and has reviewed the contents.
