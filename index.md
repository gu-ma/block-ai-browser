---
title: "Block: AI – Running AI in the Browser"
description: "Practical introduction to browser-side AI with ONNX Runtime Web, Transformers.js, and WebLLM."
theme: "AI"
block_name: "Running AI in the Browser"
block_type: lecture
draft: false
tags:
  - ai
  - browser-ai
  - lecture
  - onnx
  - transformers.js
  - webllm
---

# Block: AI – Running AI in the Browser

This block introduces how to run machine-learning models directly in the browser. Students move from the big-picture shift from server-side AI to client-side AI, into practical workflows with ONNX Runtime Web, Transformers.js, and WebLLM. The emphasis is on understanding the trade-offs, loading patterns, and user experience constraints that shape real browser AI demos.

The block is designed for learners who are already comfortable with HTML, CSS, and basic JavaScript, and want to understand how modern browser inference works in practice.

## Learning Objectives

By the end of this block, you will be able to:

- Explain why developers run AI in the browser and when this approach makes sense
- Describe the role of ONNX, model export, and browser inference backends such as WebGPU and WebAssembly
- Build a simple NLP demo with Transformers.js using a Hugging Face-compatible model
- Build a minimal browser chat demo with WebLLM and explain its practical limitations
- Compare browser AI libraries and choose a suitable stack for a classroom or prototype project

## Session Timeline Overview

- **Part 1 (Lecture + Discussion, ~35–45 min):**
  - From server-side ML to browser-side ML
  - Browser runtime constraints and opportunities
  - ONNX Runtime Web foundations
- **Part 2 (Hands-on Studio, ~60–75 min):**
  - Transformers.js text demo
  - ONNX Runtime Web reusable inference scaffold
  - WebLLM minimal chat demo
- **Debrief (10–15 min):**
  - Performance expectations, hardware limits, and tool-selection trade-offs

## Part 1: Concepts + Technical Foundations

**Format:** Lecture + guided discussion

- **Core notes:**
  - [01 – Browser AI Overview and Landscape](./content/01-browser-ai-overview-and-landscape.md)
  - [02 – ONNX Runtime Web Foundations](./content/02-onnx-runtime-web-foundations.md)
  - [03 – MediaPipe for Browser Vision](./content/03-mediapipe-for-browser-vision.md)
  - [04 – Transformers.js for Browser NLP](./content/04-transformers-js-for-browser-nlp.md)

## Part 2: Practice + Reusable Scaffolding

**Format:** Hands-on workshop

- **Practice notes:**
  - [05 – WebLLM Browser Chat](./content/05-webllm-browser-chat.md)
  - [06 – Model Loading Patterns and Shared Scaffolding](./content/06-model-loading-patterns-and-shared-scaffolding.md)
  - [07 – Comparison, Practice, and Limitations](./content/07-comparison-practice-and-limitations.md)

- **Sample demos:**
  - [01 – Transformers.js Sentiment Demo](./samples/01-transformersjs-sentiment-demo.html)
  - [02 – ONNX Runtime Web Image Classification Template](./samples/02-onnx-runtime-web-image-classification-template.html)
  - [03 – MediaPipe Hand Detection Demo](./samples/03-mediapipe-hand-landmarker-demo.html)
  - [04 – WebLLM Chat Template](./samples/04-webllm-chat-template.html)
  - [Samples README](./samples/README.md)

## Preparation

- Read the notes in order from 01 → 06
- Make sure you can run a local static web server such as `python -m http.server 8000`
- Use a recent version of Chrome or Edge for WebGPU-based demos
- Be ready to discuss where browser AI is preferable to API-based inference

## Going Further

- [Transformers.js Documentation](https://huggingface.co/docs/transformers.js/)
- [ONNX Runtime Web Documentation](https://onnxruntime.ai/docs/tutorials/web/)
- [WebLLM Documentation](https://webllm.mlc.ai/)
- [Hugging Face Model Hub](https://huggingface.co/models)
- [ONNX Overview](https://onnx.ai/)

## Tools

- [Transformers.js](https://huggingface.co/docs/transformers.js/)
- [ONNX Runtime Web](https://onnxruntime.ai/)
- [WebLLM](https://webllm.mlc.ai/)
- [Hugging Face](https://huggingface.co/)
- [Chrome](https://www.google.com/chrome/) / [Microsoft Edge](https://www.microsoft.com/edge)

## Running the Samples

The sample demos are designed to run **locally first** using a static server. This is more reliable than opening files directly with `file://` and makes model loading easier to debug. 

Clone or download the code locally:

```bash
git clone https://github.com/gu-ma/block-ai-browser
```

Navigate to the `samples` directory and start a server (you can also use live-server):

```bash
python -m http.server 8000
```

Then open the sample in your browser via `http://localhost:8000/...`

GitHub Pages could be used later for sharing a stable demo, but the primary teaching workflow in this block is local execution and iteration.
