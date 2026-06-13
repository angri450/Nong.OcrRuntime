# Nong.OcrRuntime Architecture

Last updated: 2026-06-13

Nong.OcrRuntime packages native OCR runtime files for Nong local OCR.

## Package Direction

```text
Nong.OcrRuntime
  Angri450.Nong.OcrRuntime.* native NuGet packages
        |
        v
Nong.Cli.Net
  nong ocr install-model and runtime consumption
```

The runtime repo packages native files. The CLI repo decides how users install and invoke OCR.

## Package Targets

- `win-x64`
- `linux-x64`
- `linux-arm64`
- `osx-x64`
- `osx-arm64`

All five package definitions should remain valid even if a release publishes only a validated subset.

## Boundaries

- Include PaddleInference/OpenCvSharp native runtime payloads required by the current Nong OCR backend.
- Do not include Python packages, model files, OCR wrapper executables, debug symbols, or CLI logic.
- Do not claim ONNX Runtime backend support unless an ONNX backend is intentionally added and validated as a separate contract.
