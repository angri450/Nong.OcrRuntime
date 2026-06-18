# Nong.OcrRuntime — ARCHIVED (2026-06-18)

**This repository has been retired.** The Nong OCR runtime no longer needs PaddleInference native DLLs.

## Why retired

PP-OCRv6 inference has moved from PaddleInference to ONNX Runtime. The ONNX-formatted models are published by PaddlePaddle on ModelScope:

| Model | Size |
|-------|------|
| `PaddlePaddle/PP-OCRv6_medium_det_onnx` | 59 MB |
| `PaddlePaddle/PP-OCRv6_medium_rec_onnx` | 73 MB |
| `PaddlePaddle/PP-OCRv6_small_det_onnx` | 9.5 MB |
| `PaddlePaddle/PP-OCRv6_small_rec_onnx` | 21 MB |
| `PaddlePaddle/PP-OCRv6_tiny_det_onnx` | 1.7 MB |
| `PaddlePaddle/PP-OCRv6_tiny_rec_onnx` | 4.3 MB |

## What replaces this

- **Inference engine:** `Microsoft.ML.OnnxRuntime` (same as embedding — `nong search` uses it)
- **Image loading:** SkiaSharp (already used by chart/pdf/diagram)
- **Model download:** `nong ocr install-model pp-ocrv6-medium` → git clone from ModelScope
- **Runtime install:** No longer needed — ONNX Runtime is part of the main CLI

## What happened to the NuGet packages

The `Angri450.Nong.OcrRuntime.*` packages will be deprecated on nuget.org. Users who installed them for previous nong-ocr versions can keep them, but `nong ocr install-model` no longer deploys them.

## New code location

- `Nong.Cli.Net/MultiModal/OcrOnnx/OcrOnnxEngine.cs`
- `Nong.Cli.Net/MultiModal/OcrOnnx/OcrOnnxPreprocess.cs`
- `Nong.Cli.Net/MultiModal/OcrOnnx/OcrOnnxPostprocess.cs`

## History preserved

The pack-runtimes.ps1 script, OcrRuntime.csproj, and all package definitions remain in git history.
