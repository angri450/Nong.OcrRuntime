# CLAUDE.md - Nong.OcrRuntime

Nong.OcrRuntime owns native OCR runtime NuGet packages for Nong local OCR.

## 信息源

`../.claude/PROJECT_STATE.md` 是全家桶唯一真相源。`../.claude/references/agent-rules.md` 有本项目 agent 行为约束。

本项目的 `PROJECT_STATE.md`、`AGENTS.md` 等开发文件已全部迁到 `../.claude/`。

## 先读那里

Read `../.claude/PROJECT_STATE.md` before this file. It is the cross-repo truth source.

Do not bulk-read history archives to decide current work. All archives are in `../.claude/`. Only the plan linked from `PROJECT_STATE.md` is active for a builder window.

## 当前开发状态（每次施工后更新）

- 版本: PP-OCRv6 native runtime（独立版本线，不跟 CLI 走）
- NuGet: `Angri450.Nong.OcrRuntime.*` 已发布
- 最近施工: 稳定运行，无活跃 plan
- 待办: 无

## Scope

- Maintain `Angri450.Nong.OcrRuntime.*` native runtime bundles.
- Keep all five RID package definitions valid.
- Do not add CLI, model, Word, PDF, Excel, PPT, or OCR client logic here.
- Do not publish NuGet packages unless explicitly asked.

## Required Workflow

1. Read `../.claude/PROJECT_STATE.md`.
2. Read `README.md` and `docs/runtime-matrix.md`.
3. Preserve unrelated dirty worktree changes.
4. Keep `VERSION` and `OcrRuntime.csproj` `<Version>` aligned for release work.
5. Validate with `pack-runtimes.ps1` when package contents change.
6. Record process changes under `../.claude/`; runtime release notes can also update `CHANGELOG.md`.

## Verification

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\pack-runtimes.ps1 -ValidateOnly
```
