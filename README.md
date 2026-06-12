# Apollo Lead Scoring Skill

Codex Skill for Apollo customer-pool research, evidence capture, Agent-led lead scoring, and Excel writeback.

This skill is designed for workflows where Apollo company lists are exported to Excel, company evidence is gathered from websites/search results/social links, and an Agent writes customer type, product fit, score, reason, cut-in angle, unsuitable reason, and development advice back to the workbook.

## Core Principle

Python should only move data:

- read and write Excel
- capture website/search evidence
- organize AnySearch cache
- create backups
- validate row count, score range, levels, and required fields

The Agent should make the business judgement:

- customer type
- product direction
- score and level
- matching reason
- salesperson cut-in angle
- unsuitable reason
- development advice

Do not use simple keyword addition/subtraction as the final scoring logic.

## Install

Clone this repository into your Codex skills directory.

Windows:

```powershell
git clone https://github.com/ergouzizi/apollo-lead-scoring.git "$env:USERPROFILE\.codex\skills\apollo-lead-scoring"
```

macOS / Linux:

```bash
git clone https://github.com/ergouzizi/apollo-lead-scoring.git ~/.codex/skills/apollo-lead-scoring
```

Restart or refresh Codex so the skill metadata is discovered.

## Usage

Ask Codex to use the skill, for example:

```text
Use $apollo-lead-scoring to analyze this Apollo Excel workbook for digital signage customers.
```

Typical workflow:

1. Read the project `agent.md` if one exists.
2. Inspect the target Excel workbook and sheet.
3. Select the product rule from `references/`.
4. Export evidence with `scripts/export_evidence.py`.
5. Let the Agent generate judgement JSON.
6. Write results with `scripts/write_judgements.py`.
7. Validate with `scripts/validate_workbook.py`.
8. Update the project `agent.md` with run results and lessons.

## Product Rules

Current rule files:

- `references/digital-signage-rules.md`
- `references/scanner-rules.md`
- `references/pos-rules-template.md`
- `references/product-index.md`

New products should get their own rule file, such as:

```text
references/pos-rules.md
references/payment-terminal-rules.md
references/tablet-rules.md
```

Keep product boundaries separate. For example, scanner is plug-and-play hardware and should not inherit the digital signage rule that customers need their own CMS/software.

## Scripts

Evidence export:

```powershell
python scripts/export_evidence.py `
  --target-xlsx "path\to\Apollo.xlsx" `
  --sheet "SheetName" `
  --out-dir "path\to\cache" `
  --prefix "run_name" `
  --product-query "digital signage CMS screen management"
```

Write judgement JSON back to Excel:

```powershell
python scripts/write_judgements.py `
  --target-xlsx "path\to\Apollo.xlsx" `
  --sheet "SheetName" `
  --judgements-json "path\to\judgements.json" `
  --level-column "综合数字标牌匹配层级"
```

Validate workbook:

```powershell
python scripts/validate_workbook.py `
  --target-xlsx "path\to\Apollo.xlsx" `
  --sheet "SheetName" `
  --level-column "综合数字标牌匹配层级" `
  --expect-freeze-none
```

## Privacy

Do not commit:

- API keys or `.env` files
- live customer Excel workbooks
- raw AnySearch caches unless reviewed
- backup spreadsheets
- logs with private customer data

The included `.gitignore` blocks common local artifacts, but review `git status` before pushing.

## Notes

For Windows Chinese paths and Chinese worksheet names, read:

```text
references/encoding-and-path-notes.md
```

For migration and Git usage, read:

```text
references/git-and-migration.md
```
