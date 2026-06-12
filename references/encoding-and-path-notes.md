# Encoding And Path Notes

## Known Windows Issues

- PowerShell output may default to GBK and display Chinese as mojibake.
- PowerShell redirected logs can crash on Vietnamese characters unless output is ASCII-safe or UTF-8 is forced.
- Do not write Chinese-heavy scripts through PowerShell here-strings.
- Use `apply_patch` to create or edit UTF-8 files.
- In Python scripts, use Unicode-safe file paths and `encoding="utf-8"`.
- For progress logs that may be redirected, use `json.dumps(..., ensure_ascii=True)`.

## Recommended PowerShell Setup

```powershell
$OutputEncoding = [System.Text.Encoding]::UTF8
[Console]::OutputEncoding = [System.Text.Encoding]::UTF8
```

## Script Practices

- Use `Path("D:/...") / "中文目录"` in Python, not shell-composed Chinese strings.
- Prefer command-line arguments for target paths.
- Do not print secrets.
- Do not print raw API keys.
- Do not save AnySearch quota or registration responses into customer caches.

## Excel Freeze Rule

Set `ws.freeze_panes = None` in writeback scripts unless the user explicitly requests freezing. The Apollo project has a history of accidental row-10 freeze panes blocking content visibility.
