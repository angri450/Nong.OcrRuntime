# Nong.OcrRuntime Project State

Last updated: 2026-06-13

This file is the current truth source for agents. Read it before `AGENTS.md`, `CLAUDE.md`, `README.md`, `CHANGELOG.md`, or any file under `log/`.

## Current Work

Active plan/handoff:

- None.

There is no active construction plan. If work is needed, the planner window must create or update a plan under `log/plans/`, update `log/plans/index.md`, and then update this section before a builder window starts.

Do not infer current work from `CHANGELOG.md` or old logs.

## Current Role

Nong.OcrRuntime owns only native OCR runtime NuGet packages for Nong local OCR.

It maintains first-party native runtime bundles for the `Angri450.Nong.OcrRuntime.*` package family. It does not own CLI commands, model logic, Word/PDF/Excel/PPT behavior, or OCR client code.

## Current Runtime Contract

Current repository runtime version:

- `VERSION`: `4.0.0`
- package family: `Angri450.Nong.OcrRuntime.*`

All five package IDs are first-class targets:

- `Angri450.Nong.OcrRuntime.WinX64` -> `win-x64`
- `Angri450.Nong.OcrRuntime.LinuxX64` -> `linux-x64`
- `Angri450.Nong.OcrRuntime.LinuxArm64` -> `linux-arm64`
- `Angri450.Nong.OcrRuntime.OsxX64` -> `osx-x64`
- `Angri450.Nong.OcrRuntime.OsxArm64` -> `osx-arm64`

Current supported backend contract:

- Nong's PP-OCRv6 PaddleInference path.
- Existing runtime bundles are PaddleInference/OpenCvSharp native files.
- PaddleOCR Python-side ONNX Runtime backend is not part of this package contract unless a separate ONNX backend is intentionally added and validated.

## Current Dirty State To Preserve

At the time this context map was added, these files already had uncommitted edits:

- `CHANGELOG.md`
- `OcrRuntime.csproj`
- `README.md`
- `docs/runtime-matrix.md`

Do not revert or overwrite those changes. Read them before release or packaging work.

## Planning Workflow

Development plans live in `log/plans/`.

Only the plan linked above is active for a builder window. Older plans remain as history and must not be scanned to infer current work.

Two-window workflow:

- Planner window: reads history as needed, writes or updates `log/plans/YYYY-MM-DD-topic.md`, updates `log/plans/index.md`, then updates this file's active plan pointer.
- Builder window: reads this file and the active plan only, then implements and verifies.

Detailed policy:

- `docs/wiki/planning-workflow.md`
- `log/plans/README.md`

## Current Architecture

Main files:

```text
OcrRuntime.csproj
pack-runtimes.ps1
packages.lock.json
VERSION
README.md
docs/runtime-matrix.md
```

The pack script creates and validates runtime-specific NuGet packages. The sibling `Nong.Cli.Net` repository consumes published runtime versions through its own `OcrRuntimeVersion` constant.

## Current Risks

- Native packages are large and platform-specific; publishing policy and packaging support are separate decisions.
- Version drift between `VERSION` and `OcrRuntime.csproj` must be checked before packaging.
- Existing uncommitted edits likely contain current ONNX/PaddleInference boundary work; preserve them.
- Do not publish NuGet packages unless the user explicitly asks.

## Information Sources

Use this order:

1. `PROJECT_STATE.md` for current truth.
2. `AGENTS.md` and `CLAUDE.md` for agent behavior.
3. The active plan linked above, if any.
4. `README.md` and `docs/runtime-matrix.md` for package contract details.
5. `CHANGELOG.md` and `log/` as historical evidence.

Never bulk-read `log/` to decide current work.

## Verification Baseline

Validate existing packages without packing:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\pack-runtimes.ps1 -ValidateOnly
```

Pack all runtime packages:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\pack-runtimes.ps1
```

Do not publish unless explicitly asked.
