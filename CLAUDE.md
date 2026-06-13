# CLAUDE.md - Nong.OcrRuntime

Nong.OcrRuntime owns native OCR runtime NuGet packages for Nong local OCR.

## Start Here

Read `PROJECT_STATE.md` before this file. It is the current truth source for active plans, runtime contract, dirty state, and known risks.

Do not bulk-read `log/` to decide current work. `log/` is historical archive. Only the plan linked from `PROJECT_STATE.md` is active for a builder window.

## Scope

- Maintain `Angri450.Nong.OcrRuntime.*` native runtime bundles.
- Keep all five RID package definitions valid.
- Do not add CLI, model, Word, PDF, Excel, PPT, or OCR client logic here.
- Do not publish NuGet packages unless explicitly asked.

## Required Workflow

1. Read `PROJECT_STATE.md`.
2. Read `README.md` and `docs/runtime-matrix.md`.
3. Preserve unrelated dirty worktree changes.
4. Keep `VERSION` and `OcrRuntime.csproj` `<Version>` aligned for release work.
5. Validate with `pack-runtimes.ps1` when package contents change.
6. Record process changes under `log/`; runtime release notes can also update `CHANGELOG.md`.

## Verification

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\pack-runtimes.ps1 -ValidateOnly
```
