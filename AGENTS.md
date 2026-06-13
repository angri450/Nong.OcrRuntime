# Agent Rules

This repository owns only Nong OCR native runtime NuGet packages.

## Required Entry

- Read `PROJECT_STATE.md` first. It is the current truth source.
- Then read this file, `README.md`, and `docs/runtime-matrix.md`.
- Read only the active plan linked from `PROJECT_STATE.md`, unless the user asks for historical research.
- Treat `log/` as historical archive.

## Scope

- Maintain `Angri450.Nong.OcrRuntime.*` native runtime bundles.
- Do not add CLI, Word, PDF, Excel, PPT, or model logic here.
- The main Nong.NET CLI consumes these packages through `nong ocr install-model`.

## Runtime Matrix

All five runtime package IDs are first-class package targets:

- `Angri450.Nong.OcrRuntime.WinX64` -> `win-x64`
- `Angri450.Nong.OcrRuntime.LinuxX64` -> `linux-x64`
- `Angri450.Nong.OcrRuntime.LinuxArm64` -> `linux-arm64`
- `Angri450.Nong.OcrRuntime.OsxX64` -> `osx-x64`
- `Angri450.Nong.OcrRuntime.OsxArm64` -> `osx-arm64`

Publishing policy can choose a subset, but the packaging contract must keep all five definitions valid.

## Required Loop

1. Read `PROJECT_STATE.md`, `README.md`, and `docs/runtime-matrix.md`.
2. Keep `VERSION` and `OcrRuntime.csproj` `<Version>` aligned.
3. For substantial work, write or update a plan under `log/plans/` and update `PROJECT_STATE.md` if another window will execute it.
4. Build or validate packages with `pack-runtimes.ps1`.
5. Update `CHANGELOG.md` or `log/changelog/` for runtime/context changes as appropriate.
6. Do not publish to NuGet unless explicitly asked.
