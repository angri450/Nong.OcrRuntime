# Changelog

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
