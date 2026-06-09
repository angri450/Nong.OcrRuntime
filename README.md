# Angri450.Nong.OcrRuntime

Dedicated repository for Nong local OCR native runtime NuGet packages.

These packages contain platform-specific PaddleInference and OpenCvSharp native files for `nong ocr install-model pp-ocrv5-mobile`. They do not contain Python, pip packages, external OCR executables, or user-trained models.

## Package Matrix

| Package | RID | Current version |
|---------|-----|-----------------|
| `Angri450.Nong.OcrRuntime.WinX64` | `win-x64` | `4.0.0` |
| `Angri450.Nong.OcrRuntime.LinuxX64` | `linux-x64` | `4.0.0` |
| `Angri450.Nong.OcrRuntime.LinuxArm64` | `linux-arm64` | `4.0.0` |
| `Angri450.Nong.OcrRuntime.OsxX64` | `osx-x64` | `4.0.0` |
| `Angri450.Nong.OcrRuntime.OsxArm64` | `osx-arm64` | `4.0.0` |

All five package definitions are maintained here. A release may publish only a validated subset, but the packaging contract must keep every RID definition valid.

## Version Contract

- `VERSION` is the repository runtime version.
- `OcrRuntime.csproj` `<Version>` must match `VERSION`.
- The Nong.NET CLI repository pins the consumed runtime version in `Cli/Common/OcrRuntimeVersion.cs`.
- CLI, Word, PDF, Excel, and PPT patch releases do not republish these large native runtime packages.
- Bump this repository only when native Paddle/OpenCV contents or the runtime install contract changes.

## Pack

Pack and validate all runtime packages:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\pack-runtimes.ps1
```

Pack one RID:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\pack-runtimes.ps1 -RuntimeIdentifier win-x64
```

Validate existing packages without packing:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\pack-runtimes.ps1 -ValidateOnly
```

The script restores required upstream native packages into the NuGet cache when missing, packs each selected first-party runtime bundle, and validates that every nupkg contains exactly one RID native directory with no Python files, model files, executable OCR wrappers, or debug symbols.

## Consumer Install

Users should not reference these packages directly. They install through Nong CLI:

```powershell
nong ocr install-model pp-ocrv5-mobile --source https://mirrors.huaweicloud.com/repository/nuget/v3/index.json --json
```

Upstream Sdcb/OpenCvSharp fallback in Nong CLI remains explicit and must use `--allow-upstream-fallback`.
