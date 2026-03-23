# Browser AI Samples

These samples are designed to be run **locally first** from the block root.

## Start a local server

From `blocks/block-ai-browser/` run:

```bash
python -m http.server 8000
```

Then open one of the following in a recent browser such as Chrome or Edge:

- `http://localhost:8000/samples/01-transformersjs-sentiment-demo.html`
- `http://localhost:8000/samples/02-onnx-runtime-web-image-classification-template.html`
- `http://localhost:8000/samples/03-mediapipe-hand-landmarker-demo.html`
- `http://localhost:8000/samples/04-webllm-chat-template.html`

## Why local-first?

- avoids `file://` asset-loading issues
- works better for model downloads and browser inference tests
- keeps the classroom workflow simple

## Sample Notes

- The Transformers.js sample is the most straightforward starting point.
- The ONNX Runtime Web sample now explains what kind of small teacher-provided model to start with and what students are expected to change.
- The MediaPipe sample is the easiest vision demo for beginners because it gives fast visual feedback.
- The WebLLM sample includes recommended small model names, but should still be tested on classroom machines before use.