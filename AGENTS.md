# Agent Rules

This repository owns only Nong OCR native runtime NuGet packages.

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

1. Read `README.md` and `docs/runtime-matrix.md`.
2. Keep `VERSION` and `OcrRuntime.csproj` `<Version>` aligned.
3. Build or validate packages with `pack-runtimes.ps1`.
4. Update `CHANGELOG.md` for runtime changes.
5. Do not publish to NuGet unless explicitly asked.
