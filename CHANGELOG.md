# Changelog

## Unreleased

- Clarify that the supported target for the existing native runtime bundles is Nong's PP-OCRv6 PaddleInference path.
- Record the PaddleOCR 3.7.0 backend boundary: ONNX Runtime backend support is not part of the current `Angri450.Nong.OcrRuntime.*` package contract, even if upstream PaddleInference packages carry ONNX-related DLLs.
- Keep package version `4.0.0` unchanged because native PaddleInference/OpenCvSharp contents did not change.

## 4.0.0 - 2026-06-08

- Split OCR native runtime package maintenance into this dedicated repository.
- Maintain all five package targets:
  - `Angri450.Nong.OcrRuntime.WinX64`
  - `Angri450.Nong.OcrRuntime.LinuxX64`
  - `Angri450.Nong.OcrRuntime.LinuxArm64`
  - `Angri450.Nong.OcrRuntime.OsxX64`
  - `Angri450.Nong.OcrRuntime.OsxArm64`
- Keep runtime package version independent from Nong.NET CLI and document packages.
- Preserve the native bundle contract: PaddleInference/OpenCvSharp native files only, no Python, no model files, no executable OCR wrapper, no debug symbols.
