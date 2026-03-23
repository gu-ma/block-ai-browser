---
title: "01 - Browser AI Overview and Landscape"
draft: false
---

# 01 - Browser AI Overview and Landscape

## Intro

For many years, most AI applications ran on servers: the browser sent data to an API, the server ran inference, and the result came back. Today, more models can run directly in the browser thanks to better JavaScript tooling, standardized model formats, and faster browser runtimes.

This changes the design space. Browser AI can improve privacy, reduce round trips to a server, support offline interactions, and make teaching demos easier to share. At the same time, it introduces hard constraints around model size, memory, loading time, and device capability.

## Possible Schedule

| Time    | Activity |
| ------- | -------- |
| 10 mins | From server-side ML to browser-side ML |
| 15 mins | Benefits: privacy, latency, offline use |
| 20 mins | Constraints: hardware, memory, downloads, UX |
| 15 mins | Tool landscape: ONNX Runtime Web, Transformers.js, WebLLM |
| 10 mins | Discussion: when browser AI is the right choice |

## Why Run AI in the Browser?

- **Privacy:** input data can stay on the user’s device
- **Lower latency after load:** once the model is available locally, inference can feel responsive
- **Offline use:** some demos continue to work without a network connection after initial asset download
- **Simple product demos:** no backend inference service required for small prototypes
- **Teaching value:** students can inspect both UI code and inference code together

## Practical Constraints

- **Model size matters:** a browser is not a datacenter
- **First load can be slow:** users may wait while weights download and cache
- **Device variability is real:** laptops differ wildly in GPU, CPU, RAM, and browser support
- **Backends are not equal:** WebGPU is often fastest, while WebAssembly is the fallback
- **UX matters as much as the model:** loading indicators, error states, and clear expectations are essential

## The Three Main Angles in This Block

### 1) ONNX Runtime Web

Good for general ONNX models and reusable inference pipelines.

### 2) Transformers.js

Good for browser-friendly NLP workflows with a high-level API.

### 3) WebLLM

Good for browser-only local LLM chat demos when the hardware is strong enough.

## Teaching Focus

This block is not just about “making a demo work.” It is about helping learners understand:

- why one tool is better than another in a given situation
- how assets load in the browser
- why async/await and state management matter
- how model constraints shape interaction design

## Hands-on Task (5–10 min)

Write down one use case that is **better in the browser** and one use case that is **better on a server**.

For each, justify your choice using:

1. privacy
2. latency
3. model size
4. reliability

## Continue

- [02 – ONNX Runtime Web Foundations](./02-onnx-runtime-web-foundations.md)
- [03 – Transformers.js for Browser NLP](./03-transformers-js-for-browser-nlp.md)
- [04 – WebLLM Browser Chat](./04-webllm-browser-chat.md)