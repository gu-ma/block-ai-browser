---
title: "03 - MediaPipe for Browser Vision"
draft: false
---

# 03 - MediaPipe for Browser Vision

## Why MediaPipe Belongs in This Block

MediaPipe is one of the best beginner entry points for browser AI because it gives fast, visible results with very little setup. Instead of starting from a raw model file, students can start from a working browser vision task such as:

- hand landmark detection
- face detection
- pose estimation

That makes MediaPipe a strong contrast with ONNX Runtime Web:

- **MediaPipe** = task-first and beginner-friendly
- **ONNX Runtime Web** = model-first and more flexible

## Best Beginner Use Cases

For a first class demo, I recommend one of these:

- **Hand Landmarker** for a visually clear webcam demo
- **Face Detector** for a very simple “box around the face” demo

For this block, hand landmarks are especially useful because students immediately see many points and understand that the browser is detecting structure, not just one label.

## Why It Feels Easier Than ONNX Runtime Web

With MediaPipe, beginners usually do not need to think first about:

- tensor shapes
- label files
- custom preprocessing pipelines

Instead, they can focus on:

- getting webcam input
- running a detection task
- drawing the result on a canvas

## Recommended First Classroom Flow

1. open webcam
2. run hand or face detection
3. draw one overlay on a canvas
4. discuss what the model is returning
5. only later compare that with more general runtimes such as ONNX Runtime Web

## Vanilla JS Browser Pattern

MediaPipe also fits the “simple browser demo” goal well. A typical beginner flow is:

1. load the browser package from a CDN
2. request webcam access
3. create the detector/landmarker
4. run detection on each frame
5. draw overlays

## Beginner Expectations

- use a recent Chrome or Edge browser
- allow webcam access
- start with one person in frame
- keep the demo visually simple before adding features

## Hands-on Task (5–10 min)

Build or modify a simple MediaPipe webcam page so that it:

1. shows the live camera feed
2. draws landmarks or a box on top
3. displays one line of text describing what is being detected

## Continue

- [04 – Transformers.js for Browser NLP](./03-transformers-js-for-browser-nlp.md)
- [07 – Comparison, Practice, and Limitations](./06-comparison-practice-and-limitations.md)