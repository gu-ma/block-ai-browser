---
title: "07 - Comparison, Practice, and Limitations"
draft: false
---

# 07 - Comparison, Practice, and Limitations

## Quick Comparison Table

| Tool | Best For | Strengths | Limits | Good Classroom Use |
| ---- | -------- | --------- | ------ | ------------------ |
| **MediaPipe** | Ready-made browser vision tasks | Fast visible results, good webcam demos, beginner-friendly | Less general than raw model runtimes | Face detection, hands, pose, landmarks |
| **ONNX Runtime Web** | General ONNX models | Flexible, low-level control, reusable runtime | More setup, more tensor handling | Teaching model assets and generic inference |
| **Transformers.js** | NLP / Hugging Face tasks | Friendly API, fast prototyping, good for text demos | Less general than raw ONNX workflows | Sentiment, classification, NER, QA |
| **TF.js** | TensorFlow.js ecosystem | Mature browser ML ecosystem, browser-native history | Different ecosystem assumptions | Optional comparison point |
| **WebLLM** | Local LLM chat | Strong conceptual impact, browser-only chat demos | Heavy model/runtime constraints | Demoing local LLMs and device trade-offs |

## Choosing the Right Tool

Use **MediaPipe** when:

- you want the fastest path to a working browser vision demo
- you want webcam-based interaction with minimal AI setup overhead
- you want beginners to see landmarks, boxes, and real-time perception quickly

Use **ONNX Runtime Web** when:

- you want to run a custom-exported model
- you need more control over tensors and outputs
- you want a general-purpose reusable browser runtime

Use **Transformers.js** when:

- you want the shortest path to a browser NLP demo
- your task already matches a standard transformer pipeline
- you want students to focus on inputs/outputs before lower-level details

Use **WebLLM** when:

- your goal is a local browser chat experience
- you want to demonstrate that some LLMs no longer require a server API
- you are willing to teach hardware and latency constraints as part of the lesson

## Security and Expectations Notes

- browser AI improves privacy in many cases, but model files still need to be distributed
- no API dependency does not eliminate performance cost
- student devices will not behave identically
- first impressions depend heavily on loading feedback and expectations management

## Suggested Hands-on Tasks

### Task A — Transformers.js (5–10 min)

Build a sentiment demo with:

- text input
- run button
- label + confidence display

### Task B — ONNX Runtime Web (5–10 min)

Wrap a model session into:

- `loadModel(url)`
- `runModel(data)`

Then explain which parts would change for a vision model versus an NLP model.

### Task C — MediaPipe (5–10 min)

Create a webcam demo with:

- live video
- one visible overlay such as a bounding box or landmarks
- one short note explaining what the model is detecting

Then explain why MediaPipe feels easier to start with than ONNX Runtime Web.

### Task D — WebLLM (5–10 min)

Create a tiny chat page with:

- input box
- send button
- output area
- loading / model-ready message

## Final Teaching Takeaway

The main lesson of browser AI is not “everything should move client-side.” The main lesson is that developers now have meaningful choices. Understanding those choices means balancing privacy, responsiveness, model size, browser support, and user experience.

## Reference Links

- [MediaPipe Documentation](https://developers.google.com/mediapipe)
- [Transformers.js Documentation](https://huggingface.co/docs/transformers.js/)
- [ONNX Runtime Web Documentation](https://onnxruntime.ai/docs/tutorials/web/)
- [WebLLM Documentation](https://webllm.mlc.ai/)