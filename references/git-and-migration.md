# Git And Migration

## Can This Skill Be Uploaded To Git?

Yes. The skill is a normal folder and can be committed to a Git repository.

Commit:

- `SKILL.md`
- `agents/openai.yaml`
- `references/*.md`
- `scripts/*.py`

Do not commit:

- `.env`
- API keys
- live customer Excel files
- raw AnySearch caches containing private company research unless reviewed
- local backup workbooks
- logs with sensitive data

## Install On Another Computer

Clone or copy the folder into:

```text
<CODEX_HOME>/skills/apollo-lead-scoring
```

If `CODEX_HOME` is not set, use:

```text
~/.codex/skills/apollo-lead-scoring
```

Restart Codex or reload skills so the metadata is discovered.

## Cross-Model Use

Other models can understand the workflow by reading:

1. `SKILL.md`
2. `references/workflow.md`
3. The relevant product rule file
4. `references/excel-fields.md`
5. `references/encoding-and-path-notes.md`

The scripts are optional helpers; the most important portable asset is the judgement policy that Python moves data and the Agent makes business decisions.
