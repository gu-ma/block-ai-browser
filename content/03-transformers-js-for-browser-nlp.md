---
title: "04 - Transformers.js for Browser NLP"
draft: false
---

# 04 - Transformers.js for Browser NLP

## What Transformers.js Is

Transformers.js is a JavaScript library that makes it easier to run Hugging Face transformer models in the browser and other JavaScript environments. In practice, it gives learners a friendlier API than raw tensor code, especially for standard NLP tasks.

It is a good fit when you want to demonstrate browser inference quickly without building every preprocessing and post-processing step from scratch.

## Why It Is Good for Teaching

- the API is compact
- common NLP tasks are easy to prototype
- it connects well to the Hugging Face ecosystem
- it helps students focus on inputs, outputs, and async flow before diving into lower-level runtime details

## Typical Tasks

- sentiment analysis
- named-entity recognition (NER)
- text classification
- question answering
- feature extraction / embeddings

## Model Compatibility

Not every Hugging Face model will run directly in the browser as-is. In many cases, you need:

- a model already converted for Transformers.js / ONNX use
- or an export workflow that produces a compatible ONNX version

Teaching point: “available on Hugging Face” does **not** automatically mean “browser-ready.”

## Core API Pattern

The most approachable API is the pipeline pattern:

```js
import { pipeline } from 'https://cdn.jsdelivr.net/npm/@xenova/transformers@2.17.2'

const classifier = await pipeline('sentiment-analysis')
const result = await classifier('Running AI in the browser is surprisingly practical.')
console.log(result)
```

## What to Highlight in Class

- **async/await:** model loading and inference are both asynchronous
- **data types:** inputs are strings, outputs are structured objects
- **confidence scores:** predictions are usually probabilities or scores, not absolute truths
- **task abstraction:** `pipeline('task')` hides a lot of lower-level complexity

## Demo Idea: Sentiment Analysis

Minimal UI:

- a text input or textarea
- a button to trigger inference
- an output area for label and score

Example output:

```text
sentiment: POSITIVE
confidence: 0.92
```

## ES Module Template

```js
import { pipeline } from 'https://cdn.jsdelivr.net/npm/@xenova/transformers@2.17.2'

const statusEl = document.querySelector('#status')
const outputEl = document.querySelector('#output')

statusEl.textContent = 'Loading model...'
const classifier = await pipeline('sentiment-analysis')
statusEl.textContent = 'Model ready.'

document.querySelector('#run').addEventListener('click', async () => {
  const text = document.querySelector('#text').value
  const result = await classifier(text)
  outputEl.textContent = JSON.stringify(result, null, 2)
})
```

## CDN-Style Teaching Note

For very small demos, CDN imports are convenient because students can focus on one HTML file. For larger projects, npm + bundlers become easier to maintain.

## Hands-on Task (5–10 min)

Extend a sentiment demo so it:

1. disables the run button while inference is running
2. shows a loading message
3. displays both label and confidence score clearly

## Continue

- [05 – WebLLM Browser Chat](./04-webllm-browser-chat.md)
- [07 – Comparison, Practice, and Limitations](./06-comparison-practice-and-limitations.md)