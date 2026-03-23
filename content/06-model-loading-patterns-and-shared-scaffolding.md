---
title: "06 - Model Loading Patterns and Shared Scaffolding"
draft: false
---

# 06 - Model Loading Patterns and Shared Scaffolding

## Shared Ingredients Across Browser AI Demos

Even when the libraries differ, browser AI demos often share the same application structure:

1. load assets asynchronously
2. communicate progress to the user
3. handle missing browser support
4. run inference
5. render outputs clearly
6. recover from errors gracefully

This is the connective tissue that makes the demos coherent as one class rather than three isolated examples.

## Core JavaScript Concepts to Reinforce

- `async` / `await`
- state transitions such as “idle → loading → ready → running → error”
- event listeners for buttons and forms
- conditional UI updates
- structured outputs instead of raw console logs

## Asset Loading Pattern

Typical stages:

- download library code
- download model files
- initialize runtime / backend
- cache assets when possible
- report readiness to the UI

## Generic UI State Pattern

```js
const state = {
  status: 'idle',
  model: null,
  error: null,
}

function setStatus(next) {
  state.status = next
  render()
}
```

This pattern helps students see that an AI demo is still an interface system, not only a model wrapper.

## Error Handling Checklist

- unsupported browser feature
- failed model download
- invalid input shape or type
- device memory limits
- user impatience caused by missing feedback

## Reusable Class Framework

One simple shared abstraction for the block could be:

```js
async function loadModel(urlOrConfig) {
  // initialize library-specific runtime
}

async function runModel(input) {
  // return structured outputs
}
```

Students should notice that the details differ between libraries, but the teaching architecture stays stable.

## Local-First Execution Pattern

For this block, the best default is to run all demos through a local static server:

```bash
python -m http.server 8000
```

This avoids common issues with direct file access and makes asset loading behavior easier to explain.

## Hands-on Task (5–10 min)

Take one sample from this block and add:

1. a visible loading indicator
2. a user-friendly error box
3. a “model ready” state

Then explain which part is UI logic and which part is inference logic.

## Continue

- [07 – Comparison, Practice, and Limitations](./06-comparison-practice-and-limitations.md)