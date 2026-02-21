# Agent Flow Builder

![alt text](https://github.com/Fefe-88/Agent-Flow-Builder/blob/main/example_1.png?raw=true)


**Agent Flow Builder** is a Visual Studio Code extension that lets you visually design complex AI agent workflows using a drag-and-drop editor — and **automatically generates production-ready Node.js / JavaScript code** from your flow. No boilerplate, no manual wiring: just connect blocks, configure your agents, and the extension writes the code for you.

It supports **OpenAI**, **Google Gemini**, and **Anthropic Claude** out of the box, with built-in capabilities for text generation, structured JSON output, image generation, vision, text-to-speech, speech-to-text, web search, and advanced reasoning/thinking models.

> **Design visually. Generate code automatically. Run anywhere Node.js runs.**

---

## Table of Contents
1. [Getting Started](#getting-started)
2. [Supported Providers & Models](#supported-providers--models)
3. [Core Features](#core-features)
   - [Visual Flow Editor](#visual-flow-editor)
   - [Variable Management](#variable-management)
   - [Flow Control](#flow-control)
4. [Component Types](#component-types)
5. [Multimedia Capabilities](#multimedia-capabilities)
6. [Code Generation & Execution](#code-generation--execution)
7. [Requirements & Installation](#requirements--installation)

## Getting Started

First, install the extension from the [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=fefe-88.agent-flow-builder).

1. Open the **Agent Flow Builder** view in VS Code.
2. Create a new flow or open an existing `.agent` file.
3. Drag and drop components from the palette onto the canvas.
4. Connect components to define the execution flow.
5. Configure each component using the settings panel.

## Supported Providers & Models

 The extension supports these AI providers:

* **OpenAI**.
* **Google Gemini**
* **Anthropic**

## Core Features

### Visual Flow Editor
* **Drag & Drop Interface**: Easily place nodes on an infinite canvas.
* **Clean Flow Visualization**: Auto-layout and connection lines help visualize complex logic.
* **Zoom & Pan**: Navigate large workflows with ease.
* **Clipboard Support**: Copy/Paste blocks (or groups of blocks) to duplicate logic.
* **Undo/Redo**: Full history support for safe editing.

### Variable Management
* **Start Variables**: Define global variables in the **START** block with types (String, Number, Boolean, Array, Object) and default values.
* **State Management**: Variables are automatically prefixed with `state.` in the generated code.
* **Dynamic Context**: Agents can read and write to the shared state, allowing data to pass between steps.

### Flow Control
* **Sequential Execution**: Default linear flow.
* **Branching (If/Else)**: Create logic paths based on variable values or agent outputs.
* **Loops**: Create cyclic flows to retry tasks or process lists (automatically detected).
* **Parallel Execution**: Run multiple agents simultaneously (configurable in supported patterns).
* **Error Handling**: Route errors directly in the flow using dedicated error connections.

### Customizable Labels & Internal Code
* **Rename Blocks**: Click a block and edit its name in the settings panel.
* **Custom Code**: Use the **Code / Function Caller** block to execute arbitrary JavaScript within the flow (e.g., for data formatting, math, or external API calls).

## Component Types

| Icon | Component | Description |
|------|-----------|-------------|
| ▶️ | **START** | The entry point of the flow. Defines input variables. |
| 🤖 | **AGENT** | An AI worker. Configurable with specific prompts, models, and capabilities. |
| 🔀 | **IF/ELSE** | specialized branching logic based on conditions. |
| 💻 | **CODE** | Executes custom JavaScript functions. |
| 🏁 | **END** | Marks the completion of a flow path. |

## Multimedia Capabilities

The builder goes beyond text-only agents:

* **Image Generation**: create images from text descriptions.
* **Vision (Image Analysis)**: Analyze images.
* **Text-to-Speech (TTS)**: Convert agent text responses into audio files.
* **Speech-to-Text (STT)**: Transcribe audio files into text for processing.

## Code Generation & Execution

The extension generates a pure **Node.js** module.
* **Automatic Exports**: The main function is exported `module.exports = { runMyFlow };`.
* **State Preservation**: The execution context is maintained via a `state` object passed through the chain.
* **Error Handling**: Wraps agent calls in try/catch blocks for robustness.

To run the generated code, simply import the function in your Node.js application:

```javascript
const { runMyFlow } = require('./my_agent_flow.js');

async function main() {
  const result = await runMyFlow({ state: {}, conversationHistory: [] });
  console.log(result);
}
main();
```

## Requirements & Installation

To fully utilize all generated agents, your project requires the following SDKs. The extension includes an **Environment Validator** that checks for these dependencies.

### Required Environment Variables
Create a `.env` file in your project root with your API keys:
```env
OPENAI_API_KEY=sk-...
GEMINI_API_KEY=...
ANTHROPIC_API_KEY=sk-...
```

### SDK Dependencies
Install the necessary packages via npm:

```bash
# Core utils
npm install dotenv zod zod-to-json-schema wav

# AI SDKs (install based on providers used)
npm install openai
npm install @google/generative-ai @google/genai
npm install @anthropic-ai/sdk
```

* **Note**: `wav` is required specfically for Gemini TTS feature to handle audio formatting.

---

## Tags

`ai agent builder` `visual workflow editor` `code generation` `openai` `gpt` `gemini` `anthropic` `claude` `llm` `node.js` `javascript` `drag and drop` `no-code` `low-code` `automation` `vscode extension` `ai workflow` `text-to-speech` `speech-to-text` `image generation` `vision` `web search` `structured output` `json schema` `multi-agent` `ai orchestration` `prompt engineering`
