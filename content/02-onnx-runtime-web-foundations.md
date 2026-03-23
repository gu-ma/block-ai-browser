---
title: "02 - ONNX Runtime Web Foundations"
draft: false
---

# 02 - ONNX Runtime Web Foundations

## Beginner Positioning

For beginners, ONNX Runtime Web is best understood as the **"bring your own model"** path.

Unlike Transformers.js, which gives you a ready-made task API, ONNX Runtime Web asks you to think about:

- which model file you are loading
- what shape the input tensor should have
- how to interpret the output values

That makes it slightly more technical, but also very useful for teaching how browser inference actually works.

## What ONNX Is

ONNX stands for **Open Neural Network Exchange**. It is a model format designed to help move models between frameworks and runtimes. A model trained in PyTorch or TensorFlow can often be exported to ONNX and then loaded in environments beyond Python, including the browser.

This is useful because the browser does not run Python machine-learning code directly. Instead, it needs a runtime that can load a model file, create tensors, execute inference, and return outputs.

## Why ONNX Runtime Web Matters

ONNX Runtime Web provides that browser-side execution layer.

It is a strong choice when you want:

- a general model runtime rather than a task-specific helper
- support for custom or exported ONNX models
- explicit control over inputs, outputs, and inference sessions
- a reusable abstraction for multiple demos

## Which Model Should Beginners Use?

For a first classroom demo, I recommend using a **small image-classification model** that the teacher provides locally.

Good beginner-friendly model families to look for:

- **SqueezeNet** ONNX variants
- **MobileNet** ONNX variants

Why these are good first choices:

- they are small compared with larger vision models
- they fit the familiar idea of “classify this image into one label”
- they make tensor inputs easier to explain than more complex detection models

For the class, the easiest workflow is:

1. provide one tested `.onnx` file to all students
2. provide the input size and label list with it
3. let students focus on loading, running, and displaying results

Teaching note: beginners should **not** have to hunt for a compatible model on their first try.

## Browser Backends

ONNX Runtime Web can use different execution backends:

- **WebGPU:** usually the most interesting option for performance in modern browsers
- **WebGL:** available in some scenarios, but less central today than WebGPU
- **WebAssembly (WASM):** the most portable fallback, often slower but broadly useful

Teaching point: backend choice is part of the application design, not just an implementation detail.

## Typical Workflow

1. Train or obtain a model
2. Export it to `.onnx`
3. Serve the model file from a web-accessible path
4. Create an `InferenceSession`
5. Build input tensors
6. Run `session.run()`
7. Read and interpret outputs

## First Success Path for Students

Before teaching a reusable abstraction, I would frame the first successful run like this:

1. load one teacher-provided image-classification ONNX model
2. create one input tensor with the expected shape, for example `[1, 3, 224, 224]`
3. run inference once
4. print the raw output
5. only then discuss helper functions such as `loadModel()` and `runModel()`

This keeps the mental model concrete before introducing abstraction.

## Minimal Reusable Pattern

```js
import * as ort from 'https://cdn.jsdelivr.net/npm/onnxruntime-web/dist/ort.min.js'

async function loadModel(url) {
  return await ort.InferenceSession.create(url, {
    executionProviders: ['webgpu', 'wasm'],
  })
}

async function runModel(session, inputName, data, dims) {
  const tensor = new ort.Tensor('float32', data, dims)
  const outputs = await session.run({ [inputName]: tensor })
  return outputs
}
```

## What Students Should Notice

- inference is asynchronous
- inputs need explicit tensor shape and type
- model files are assets that must be served correctly
- outputs usually need post-processing before they are meaningful to users

## What Students Need to Know About Tensor Shape

For image classification, many beginner models expect something like:

- `1` = one image in the batch
- `3` = RGB channels
- `224, 224` = image width and height expected by the model

Students do not need to master tensor algebra on day one. They only need to understand that the model expects data in a very specific shape.

## Model Assets Workflow

When using ONNX in the browser, the model file becomes part of your application assets.

Questions students should ask:

- Where is the `.onnx` file hosted?
- How large is it?
- Will it be cached?
- What happens on first load vs later loads?
- Which browser/backend is expected?

## Hands-on Task (5–10 min)

Take a teacher-provided ONNX image-classification model and answer:

1. what file is the model loading?
2. what input shape does it expect?
3. what kind of output does it return?

Then sketch a helper API for the class using these functions:

- `loadModel(url)`
- `runModel(data)`

Then explain what additional state a real UI would need, such as loading indicators, backend selection, or error messages.

## Continue

- [03 – Transformers.js for Browser NLP](./03-transformers-js-for-browser-nlp.md)
- [05 – Model Loading Patterns and Shared Scaffolding](./05-model-loading-patterns-and-shared-scaffolding.md)