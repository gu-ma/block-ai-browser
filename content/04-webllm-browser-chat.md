---
title: "05 - WebLLM Browser Chat"
draft: false
---

# 05 - WebLLM Browser Chat

## Beginner Positioning

WebLLM is exciting for beginners because it makes one idea very concrete: a chat model can sometimes run directly on your laptop in the browser.

At the same time, it is the **least predictable** demo in this block because performance depends heavily on the machine, browser, and model size.

## What WebLLM Is

WebLLM is a browser-focused runtime for running language models locally in web applications, with a strong emphasis on WebGPU acceleration. It is one of the most direct ways to build a “chat with a local LLM in the browser” experience.

For teaching, it is compelling because it makes a powerful point very quickly: some LLM experiences no longer need a remote API call.

## Why It Is Different from a Cloud Chat API

With a cloud API:

- prompts leave the browser
- inference happens on remote infrastructure
- you pay in latency, privacy trade-offs, and service dependency

With WebLLM:

- model execution happens on the client device
- no remote generation API is required for the chat itself
- hardware limits become a core product constraint

## Setup Flow

At a high level, the flow is:

1. import the library
2. initialize a model
3. accept user input
4. send prompt history or prompt text
5. render the response, either at once or incrementally

## Which Models Should Beginners Try?

For a classroom setting, the best approach is to recommend **small instruction-tuned models first**.

Good starting points to test as a teacher before class:

- `Phi-3.5-mini-instruct-q4f16_1-MLC`
- `gemma-2-2b-it-q4f32_1-MLC-1k`

Why these are better for beginners than larger models:

- smaller downloads
- faster first results
- lower risk of memory problems on student laptops

Teaching advice:

- provide **one default model name** for the class
- provide **one fallback model** if the first choice is too slow
- avoid starting with 7B–8B style models unless you already tested the classroom machines carefully

## Minimal Mental Model

```js
const engine = await init(modelName)
const reply = await chat(engine, prompt)
```

Actual APIs vary over time, but for teaching, this is the right abstraction: initialize first, then run the chat loop.

## What Model Sizes Work Best?

In the browser, smaller and medium models are much more realistic than large frontier models.

Students should expect trade-offs:

- smaller models load faster
- smaller models usually respond faster
- bigger models may exceed memory or run too slowly on everyday laptops

## Streaming vs Whole Response

Two useful UX patterns:

- **whole response:** simplest to implement and explain
- **streaming response:** better user experience, but slightly more UI logic

Teaching point: even when the ML part is interesting, interface design still matters.

## Recommended First Classroom Flow

1. load one recommended small model
2. ask one short factual prompt
3. render one complete reply
4. only later discuss streaming, chat history, and model switching

This keeps the first success path short and reduces classroom debugging time.

## Security and Expectation Notes

- no remote generation API does **not** mean zero cost; the user still pays in compute time and battery
- device GPU/CPU quality heavily affects the experience
- first-load download time can be substantial
- “runs in browser” does not mean “runs well on every browser or every machine”

## Beginner Expectations Box

Before class, students should hear this clearly:

- **best browser:** recent Chrome or Edge
- **best first prompt:** short and simple
- **first run may take time:** model download + initialization can be slow
- **not every laptop will behave the same:** some students may need a fallback demo
- **this is still a success even if it is slower than ChatGPT:** the point is understanding local browser inference

## Hands-on Task (5–10 min)

Ask students to improve a minimal chat UI by adding:

1. a model loading status message
2. a disabled send button until the model is ready
3. a warning note about browser/device requirements

## Continue

- [06 – Model Loading Patterns and Shared Scaffolding](./05-model-loading-patterns-and-shared-scaffolding.md)
- [07 – Comparison, Practice, and Limitations](./06-comparison-practice-and-limitations.md)