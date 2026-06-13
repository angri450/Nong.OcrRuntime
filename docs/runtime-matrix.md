# Runtime Matrix

The repository maintains five first-party native runtime package targets.

The package set currently covers Nong's PP-OCRv6 PaddleInference backend. PaddleOCR 3.7.0's ONNX Runtime backend is a separate inference backend and is not part of the current package contract. Upstream PaddleInference packages may still carry ONNX-related native DLLs as transitive files.

| Package | RID | Paddle package | Paddle version | OpenCV package | OpenCV version |
|---------|-----|----------------|----------------|----------------|----------------|
| `Angri450.Nong.OcrRuntime.WinX64` | `win-x64` | `Sdcb.PaddleInference.runtime.win64.mkl` | `3.3.1.70` | `OpenCvSharp4.runtime.win` | `4.11.0.20250507` |
| `Angri450.Nong.OcrRuntime.LinuxX64` | `linux-x64` | `Sdcb.PaddleInference.runtime.linux-x64.openblas` | `3.3.1.70` | `OpenCvSharp4.runtime.ubuntu.18.04-x64` | `4.6.0.20220608` |
| `Angri450.Nong.OcrRuntime.LinuxArm64` | `linux-arm64` | `Sdcb.PaddleInference.runtime.linux-arm64` | `3.3.1.70` | `OpenCvSharp4.runtime.linux-arm64` | `4.13.0.20260602` |
| `Angri450.Nong.OcrRuntime.OsxX64` | `osx-x64` | `Sdcb.PaddleInference.runtime.osx-x64` | `3.3.1.70` | `OpenCvSharp4.runtime.osx.10.15-universal` | `4.7.0.20230224` |
| `Angri450.Nong.OcrRuntime.OsxArm64` | `osx-arm64` | `Sdcb.PaddleInference.runtime.osx-arm64` | `3.3.1.70` | `OpenCvSharp4.runtime.osx.10.15-universal` | `4.7.0.20230224` |

## Validation Rules

Each package must contain:

- exactly one `runtimes/<rid>/native/` directory;
- required Paddle native runtime files;
- required OpenCvSharp native runtime files.

Each package must not contain:

- Python directories or files;
- model directories;
- `.exe` OCR wrappers;
- `.pdb` debug symbols;
- `.whl` packages.

These packages must not claim ONNX Runtime backend support unless an ONNX backend is intentionally added and validated as a separate runtime contract.

## Publishing Boundary

Packaging support and publishing policy are separate decisions. This repository keeps all five package targets valid. Maintainers may publish a subset only when that subset has target-machine smoke coverage.
