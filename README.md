# LLMChat with WebGPU & Transformers.js

基于 WebGPU 和 Transformers.js 的浏览器端大语言模型聊天实现，通过 GPU 加速实现高效的 AI 对话体验。

![webgpu llm chat](https://github.com/xinzhanguo/webgpullmchat/blob/main/webgpullmchat.png?raw=true)

## ✨ 特性

- **WebGPU 加速** - 利用浏览器 GPU 资源加速推理
- **零服务端依赖** - 完全在浏览器端运行
- **即开即用** - 无需复杂环境配置
- **实时交互** - 低延迟的流式响应
- **模型兼容** - 支持 Hugging Face 格式的 LLM 模型

## 📦 快速开始

### 前置要求
- 支持 WebGPU 的浏览器（Chrome 113+ / Edge 113+）
- 现代 JavaScript 运行环境

### 打开体验
- 浏览器中打开即可体验

### 开发说明

* @huggingface/transformers@3.0.0
* webgpu

```
import { pipeline } from 'https://cdn.jsdelivr.net/npm/@huggingface/transformers@3.0.0';

// Create a text generation pipeline
const generator = await pipeline(
  "text-generation",
  "onnx-community/Qwen2.5-0.5B-Instruct",
  { dtype: "q4", device: "webgpu" },
);

// Define the list of messages
const messages = [
  { role: "system", content: "You are a helpful assistant." },
  { role: "user", content: "Tell me a funny joke." },
];

// Generate a response
const output = await generator(messages, { max_new_tokens: 128 });
console.log(output[0].generated_text.at(-1).content);

```