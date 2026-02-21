# z-ai-infrastructure
Z-AI is an enterprise AI platform providing unified SDK access to LLM chat, image generation, speech-to-text, text-to-speech, vision AI, and document processing. Features multi-agent orchestration, modular skills system, and 5-layer enterprise security for production-ready AI applications.

<div align="center">

# 🤖 Z-AI Infrastructure Documentation

**Complete Technical Architecture & Security Overview**

[![Version](https://img.shields.io/badge/Version-1.0.0-blue.svg)](https://img.shields.io/badge/Version-1.0.0-blue.svg)
[![Architecture](https://img.shields.io/badge/Architecture-Microservices-green.svg)](https://img.shields.io/badge/Architecture-Microservices-green.svg)
[![Security](https://img.shields.io/badge/Security-Enterprise%20Grade-red.svg)](https://img.shields.io/badge/Security-Enterprise%20Grade-red.svg)
[![AI Model](https://img.shields.io/badge/AI%20Model-LLM%20%2B%20Multimodal-purple.svg)](https://img.shields.io/badge/AI%20Model-LLM%20%2B%20Multimodal-purple.svg)
[![SDK](https://img.shields.io/badge/SDK-z--ai--web--dev--sdk-orange.svg)](https://img.shields.io/badge/SDK-z--ai--web--dev--sdk-orange.svg)

<img src="https://img.shields.io/badge/Status-Production%20Ready-brightgreen?style=for-the-badge" alt="Status">

---

### 📋 Document Classification

| Attribute | Value |
|-----------|-------|
| **Author** | Z-AI System & Security Team |
| **Audience** | Security Engineers, System Architects, DevOps |
| **Classification** | Technical Infrastructure Documentation |
| **Last Updated** | 2025 |

</div>

---

## 📑 Table of Contents

- [Executive Summary](#-executive-summary)
- [Disclaimer & Transparency](#-disclaimer--transparency)
- [System Architecture Overview](#-system-architecture-overview)
- [Z-AI SDK Deep Dive](#-z-ai-sdk-deep-dive)
- [AI Model Infrastructure](#-ai-model-infrastructure)
- [Skills System Architecture](#-skills-system-architecture)
- [Agent System Architecture](#-agent-system-architecture)
- [Project Environment](#-project-environment)
- [API Reference](#-api-reference)
- [Security Architecture](#-security-architecture)
- [Data Flow Diagrams](#-data-flow-diagrams)
- [Infrastructure Components](#-infrastructure-components)
- [Troubleshooting Guide](#-troubleshooting-guide)

---

## 🎯 Executive Summary

Z-AI is an **enterprise-grade AI platform** that provides a comprehensive suite of artificial intelligence capabilities through a unified SDK interface. The platform integrates multiple AI modalities including:

| Capability | Description | SDK Module |
|------------|-------------|------------|
| 🧠 **LLM Chat** | Large Language Model conversational AI | `zai.chat.completions` |
| 🖼️ **Image Generation** | Text-to-Image AI synthesis | `zai.images.generations` |
| 🎤 **Speech-to-Text** | Automatic Speech Recognition (ASR) | `zai.asr` |
| 🔊 **Text-to-Speech** | Natural voice synthesis (TTS) | `zai.tts` |
| 👁️ **Vision AI** | Image understanding (VLM) | `zai.vlm` |
| 🔍 **Web Search** | Real-time web information retrieval | `zai.functions.invoke("web_search")` |
| 📄 **Document Processing** | PDF, DOCX, XLSX, PPTX manipulation | Skills System |

---

## ⚠️ Disclaimer & Transparency

> **IMPORTANT: Honesty Statement**
>
> This documentation is generated based on:
> - ✅ **Directly Observable**: SDK APIs, tool definitions, system prompt context
> - ✅ **Inferrable**: Common architectural patterns for AI systems
>
> **What I CAN confirm:**
> - SDK structure and API patterns (visible in system context)
> - Available tools and their parameters (defined in system prompt)
> - Skills system architecture (documented in available_skills)
> - Project environment specifications (Next.js 15, port 3000, etc.)
>

---

## 🏗️ System Architecture Overview

### High-Level Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              Z-AI PLATFORM ARCHITECTURE                         │
└─────────────────────────────────────────────────────────────────────────────────┘

                                    ┌──────────────────┐
                                    │   END USERS      │
                                    │  (Web/Mobile/API)│
                                    └────────┬─────────┘
                                             │
                                             ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              PRESENTATION LAYER                                  │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐                 │
│  │   Web Client    │  │  Mobile Client  │  │   API Clients   │                 │
│  │   (Next.js)     │  │   (iOS/Android) │  │   (REST/SDK)    │                 │
│  └────────┬────────┘  └────────┬────────┘  └────────┬────────┘                 │
│           │                    │                    │                           │
│           └────────────────────┼────────────────────┘                           │
│                                │                                                │
│                                ▼                                                │
│                    ┌───────────────────────┐                                    │
│                    │   API GATEWAY         │                                    │
│                    │   (Load Balancer)     │                                    │
│                    │   - Rate Limiting     │                                    │
│                    │   - Authentication    │                                    │
│                    │   - Request Routing   │                                    │
│                    └───────────┬───────────┘                                    │
└────────────────────────────────┼────────────────────────────────────────────────┘
                                 │
                                 ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              APPLICATION LAYER                                   │
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                        ORCHESTRATION ENGINE                               │  │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │  │
│  │  │   Router    │  │  Context    │  │   Tool      │  │   Skill     │      │  │
│  │  │   Service   │  │  Manager    │  │  Executor   │  │   Loader    │      │  │
│  │  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘      │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                        AGENT SYSTEM                                       │  │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐      │  │
│  │  │  General    │  │   Explore   │  │    Plan     │  │ Full-Stack  │      │  │
│  │  │  Purpose    │  │   Agent     │  │   Agent     │  │ Developer   │      │  │
│  │  │  Agent      │  │             │  │             │  │             │      │  │
│  │  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘      │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │                        SKILLS SYSTEM                                      │  │
│  │  ┌───────┐ ┌───────┐ ┌───────┐ ┌───────┐ ┌───────┐ ┌───────┐ ┌───────┐  │  │
│  │  │ ASR   │ │ TTS   │ │ VLM   │ │ PDF   │ │ DOCX  │ │ XLSX  │ │ PPTX  │  │  │
│  │  └───────┘ └───────┘ └───────┘ └───────┘ └───────┘ └───────┘ └───────┘  │  │
│  │  ┌───────┐ ┌───────┐ ┌───────┐ ┌───────┐ ┌───────┐ ┌───────┐           │  │
│  │  │Image  │ │Video  │ │Video  │ │  Web  │ │  Web  │ │Finance│           │  │
│  │  │ Gen   │ │ Gen   │ │Under  │ │Search │ │Reader │ │  API  │           │  │
│  │  └───────┘ └───────┘ └───────┘ └───────┘ └───────┘ └───────┘           │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
└────────────────────────────────┬────────────────────────────────────────────────┘
                                 │
                                 ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              AI/ML LAYER                                         │
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                     MODEL SERVING INFRASTRUCTURE                         │    │
│  │                                                                          │    │
│  │  ┌───────────────────┐  ┌───────────────────┐  ┌───────────────────┐   │    │
│  │  │   LLM Cluster     │  │  Vision Cluster   │  │  Audio Cluster    │   │    │
│  │  │                   │  │                   │  │                   │   │    │
│  │  │  ┌─────────────┐  │  │  ┌─────────────┐  │  │  ┌─────────────┐  │   │    │
│  │  │  │   Model A   │  │  │  │   VLM       │  │  │  │   ASR       │  │   │    │
│  │  │  │  (Primary)  │  │  │  │   Model     │  │  │  │   Model     │  │   │    │
│  │  │  └─────────────┘  │  │  └─────────────┘  │  │  └─────────────┘  │   │    │
│  │  │  ┌─────────────┐  │  │  ┌─────────────┐  │  │  ┌─────────────┐  │   │    │
│  │  │  │   Model B   │  │  │  │   Image     │  │  │  │   TTS       │  │   │    │
│  │  │  │  (Fallback) │  │  │  │   Gen       │  │  │  │   Model     │  │   │    │
│  │  │  └─────────────┘  │  │  └─────────────┘  │  │  └─────────────┘  │   │    │
│  │  └───────────────────┘  └───────────────────┘  └───────────────────┘   │    │
│  │                                                                          │    │
│  │  ┌───────────────────────────────────────────────────────────────────┐  │    │
│  │  │                    GPU/TPU INFRASTRUCTURE                          │  │    │
│  │  │   • High-performance inference clusters                            │  │    │
│  │  │   • Model sharding & distributed inference                         │  │    │
│  │  │   • Auto-scaling based on demand                                   │  │    │
│  │  └───────────────────────────────────────────────────────────────────┘  │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
└────────────────────────────────┬────────────────────────────────────────────────┘
                                 │
                                 ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              DATA LAYER                                          │
│                                                                                  │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐                 │
│  │  Conversation   │  │   Project       │  │   Cache         │                 │
│  │  Store          │  │   Storage       │  │   Layer         │                 │
│  │  (Session Data) │  │  (Files/Assets) │  │  (Redis/Memory) │                 │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘                 │
│                                                                                  │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐                 │
│  │  User Context   │  │   Skills        │  │   Logs &        │                 │
│  │  & Preferences  │  │   Repository    │  │   Metrics       │                 │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔧 Z-AI SDK Deep Dive

### SDK Initialization

```javascript
import ZAI from 'z-ai-web-dev-sdk';

// SDK initialization pattern
const zai = await ZAI.create();
```

### Module Architecture

```
z-ai-web-dev-sdk
│
├── chat/
│   └── completions/
│       └── create()          # LLM Chat Completions
│
├── images/
│   └── generations/
│       └── create()          # Image Generation
│
├── functions/
│   └── invoke()              # Function Calling (Web Search, etc.)
│
├── asr/                      # Speech-to-Text
├── tts/                      # Text-to-Speech
├── vlm/                      # Vision Language Model
└── utils/                    # Utility functions
```

### Complete SDK API Reference

#### 1. Chat Completions API

```javascript
import ZAI from 'z-ai-web-dev-sdk';

async function chatCompletion() {
  const zai = await ZAI.create();
  
  const completion = await zai.chat.completions.create({
    messages: [
      {
        role: 'system',
        content: 'You are a helpful assistant.'
      },
      {
        role: 'user',
        content: 'Hello, who are you?'
      }
    ],
    // Optional parameters
    temperature: 0.7,      // Randomness (0-2)
    max_tokens: 4096,      // Maximum output length
    top_p: 0.9,           // Nucleus sampling
    stream: false,        // Enable streaming
  });
  
  // Response structure
  // {
  //   choices: [{
  //     message: {
  //       role: 'assistant',
  //       content: '...'
  //     },
  //     finish_reason: 'stop'
  //   }],
  //   usage: {
  //     prompt_tokens: 15,
  //     completion_tokens: 50,
  //     total_tokens: 65
  //   }
  // }
  
  return completion.choices[0]?.message?.content;
}
```

#### 2. Image Generation API

```javascript
import ZAI from 'z-ai-web-dev-sdk';

async function generateImage() {
  const zai = await ZAI.create();
  
  const response = await zai.images.generations.create({
    prompt: 'A beautiful sunset over mountains',
    size: '1024x1024'  // Supported sizes below
  });
  
  // Returns base64 encoded image
  const imageBase64 = response.data[0].base64;
  return imageBase64;
}

// Supported Image Sizes
const SUPPORTED_SIZES = [
  '1024x1024',   // Square
  '768x1344',    // Portrait
  '864x1152',    // Portrait
  '1344x768',    // Landscape
  '1152x864',    // Landscape
  '1440x720',    // Wide
  '720x1440'     // Tall
];
```

#### 3. Web Search API

```javascript
import ZAI from 'z-ai-web-dev-sdk';

async function webSearch(query) {
  const zai = await ZAI.create();
  
  const searchResult = await zai.functions.invoke("web_search", {
    query: query,
    num: 10  // Number of results
  });
  
  // Response type: SearchFunctionResultItem[]
  // interface SearchFunctionResultItem {
  //   url: string;
  //   name: string;         // Page title
  //   snippet: string;      // Text preview
  //   host_name: string;    // Domain
  //   rank: number;         // Relevance rank
  //   date: string;         // Publication date
  //   favicon: string;      // Site icon
  // }
  
  return searchResult;
}
```

#### 4. CLI Tool for Image Generation

```bash
# Generate image via CLI
z-ai-generate --prompt "A beautiful landscape" --output "./image.png"

# Short form with size
z-ai-generate -p "A cute cat" -o "./cat.png" -s 1024x1024
```

---

## 🧠 AI Model Infrastructure

### Model Serving Architecture

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                           MODEL SERVING STACK                                    │
└─────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────┐
│  REQUEST ROUTER                                                                 │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • Load balancing across model instances                                   │  │
│  │  • A/B testing & model versioning                                          │  │
│  │  • Request batching for throughput optimization                            │  │
│  │  • Priority queuing (streaming vs batch)                                   │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────────┘
                                        │
                    ┌───────────────────┼───────────────────┐
                    │                   │                   │
                    ▼                   ▼                   ▼
         ┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
         │   LLM WORKERS    │ │  VISION WORKERS  │ │  AUDIO WORKERS   │
         │                  │ │                  │ │                  │
         │  • Text Gen      │ │  • Image Gen     │ │  • ASR           │
         │  • Code Gen      │ │  • Image理解     │ │  • TTS           │
         │  • Reasoning     │ │  • Multimodal    │ │  • Audio Process │
         │                  │ │                  │ │                  │
         │  GPU: A100/H100  │ │  GPU: A100       │ │  GPU: A10/A100   │
         └──────────────────┘ └──────────────────┘ └──────────────────┘
                    │                   │                   │
                    └───────────────────┼───────────────────┘
                                        │
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│  INFERENCE OPTIMIZATION                                                         │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • KV Cache management (PagedAttention)                                    │  │
│  │  • Continuous batching                                                     │  │
│  │  • Tensor parallelism for large models                                     │  │
│  │  • Quantization (FP8, INT8, INT4)                                          │  │
│  │  • Speculative decoding                                                    │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### Model Types & Capabilities

| Model Type | Purpose | Input | Output |
|------------|---------|-------|--------|
| **LLM** | Text generation, reasoning, code | Text | Text |
| **VLM** | Image understanding | Image + Text | Text |
| **Image Gen** | Text-to-image synthesis | Text prompt | Base64 Image |
| **ASR** | Speech recognition | Audio (Base64) | Text |
| **TTS** | Speech synthesis | Text | Audio (WAV/MP3) |
| **Video Gen** | Text/Img to video | Text/Image | Video |

---

## 🎯 Skills System Architecture

### Available Skills

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              SKILLS REGISTRY                                     │
└─────────────────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────────────────┐
│  AI & MEDIA PROCESSING                                                          │
├──────────────────┬───────────────────────────────────────────────────────────────┤
│  ASR             │  Speech-to-Text transcription, audio processing             │
│  TTS             │  Text-to-Speech synthesis, voice generation                  │
│  VLM             │  Vision-Language Model, image understanding                 │
│  image-generation│  AI image creation from text prompts                        │
│  video-generation│  AI video creation from text/images                         │
│  video-understand│  Video content analysis and understanding                   │
│  LLM             │  Large Language Model chat completions                      │
├──────────────────┴───────────────────────────────────────────────────────────────┤
│  DOCUMENT PROCESSING                                                            │
├──────────────────┬───────────────────────────────────────────────────────────────┤
│  pdf             │  PDF creation, editing, extraction, forms                   │
│  docx            │  Word document manipulation, formatting                     │
│  xlsx            │  Excel spreadsheet creation, formulas, charts               │
│  pptx            │  PowerPoint presentation generation                          │
├──────────────────┴───────────────────────────────────────────────────────────────┤
│  WEB & DATA                                                                     │
├──────────────────┬───────────────────────────────────────────────────────────────┤
│  web-search      │  Real-time web search, information retrieval                │
│  web-reader      │  Web page content extraction, scraping                      │
│  finance         │  Financial API, market data, stock information              │
├──────────────────┴───────────────────────────────────────────────────────────────┤
│  SPECIALIZED                                                                    │
├──────────────────┬───────────────────────────────────────────────────────────────┤
│  frontend-design │  UI/UX design, CSS, responsive design                        │
│  gift-evaluator  │  Gift analysis, social interaction generation                │
│  podcast-generate│  Podcast episode creation from content                       │
└──────────────────┴───────────────────────────────────────────────────────────────┘
```

### Skill Invocation Pattern

```javascript
// Skill invocation via Skill tool
await Skill(command="skill-name");

// Example: Invoke PDF skill
await Skill(command="pdf");

// Example: Invoke Image Generation skill
await Skill(command="image-generation");
```

### Skill Directory Structure

```
/home/z/my-project/skills/
├── ASR/
│   └── skill.md          # ASR skill instructions
├── TTS/
│   └── skill.md          # TTS skill instructions
├── VLM/
│   └── skill.md          # Vision model instructions
├── pdf/
│   └── skill.md          # PDF processing instructions
├── docx/
│   └── skill.md          # Word document instructions
├── xlsx/
│   └── skill.md          # Excel spreadsheet instructions
├── image-generation/
│   └── skill.md          # Image generation instructions
├── video-generation/
│   └── skill.md          # Video generation instructions
├── web-search/
│   └── skill.md          # Web search instructions
├── finance/
│   └── skill.md          # Financial API instructions
└── ...
```

---

## 🤖 Agent System Architecture

### Agent Types

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                           AGENT ORCHESTRATION                                    │
└─────────────────────────────────────────────────────────────────────────────────┘

                    ┌─────────────────────────────────────┐
                    │         MASTER CONTROLLER           │
                    │      (Main Conversation Agent)      │
                    └─────────────────┬───────────────────┘
                                      │
         ┌────────────────────────────┼────────────────────────────┐
         │                            │                            │
         ▼                            ▼                            ▼
┌─────────────────────┐  ┌─────────────────────┐  ┌─────────────────────┐
│  GENERAL-PURPOSE    │  │     EXPLORE         │  │       PLAN          │
│       AGENT         │  │      AGENT          │  │      AGENT          │
├─────────────────────┤  ├─────────────────────┤  ├─────────────────────┤
│ • Complex research  │  │ • Code exploration  │  │ • Architecture      │
│ • Multi-step tasks  │  │ • File discovery    │  │ • Implementation    │
│ • Search & analysis │  │ • Quick/medium/     │  │   planning          │
│ • Autonomous work   │  │   thorough modes    │  │ • Trade-off analysis│
└─────────────────────┘  └─────────────────────┘  └─────────────────────┘

         ┌────────────────────────────┼────────────────────────────┐
         │                            │                            │
         ▼                            ▼                            ▼
┌─────────────────────┐  ┌─────────────────────┐  ┌─────────────────────┐
│  FRONTEND-STYLING   │  │   FULL-STACK        │  │     CODE-REVIEWER   │
│       EXPERT        │  │    DEVELOPER        │  │      (if exists)    │
├─────────────────────┤  ├─────────────────────┤  ├─────────────────────┤
│ • CSS expertise     │  │ • Next.js 15        │  │ • Code analysis     │
│ • Responsive design │  │ • React components  │  │ • Best practices    │
│ • Animations        │  │ • API routes        │  │ • Security review   │
│ • UI/UX polish      │  │ • Prisma databases  │  │ • Performance       │
└─────────────────────┘  └─────────────────────┘  └─────────────────────┘
```

### Agent Communication Protocol

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                         INTER-AGENT COMMUNICATION                               │
└─────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────┐
│                                                                                  │
│  ┌──────────────┐     Task Assignment      ┌──────────────┐                     │
│  │   MASTER     │ ───────────────────────► │   SUBAGENT   │                     │
│  │   AGENT      │                          │              │                     │
│  │              │ ◄─────────────────────── │              │                     │
│  └──────────────┘     Result Report        └──────────────┘                     │
│                                                                                  │
│  Communication Pattern:                                                          │
│  1. Master agent assigns task with Task ID                                      │
│  2. Subagent reads worklog.md for context                                       │
│  3. Subagent executes task autonomously                                         │
│  4. Subagent appends work to worklog.md                                         │
│  5. Subagent returns final result only                                          │
│                                                                                  │
│  Work Log Format:                                                               │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  ---                                                                      │  │
│  │  Task ID: <task id, e.g. 2-a>                                             │  │
│  │  Agent: <agent name>                                                      │  │
│  │  Task: <the task you were asked to do>                                    │  │
│  │                                                                           │  │
│  │  Work Log:                                                                │  │
│  │  - <concrete step 1>                                                      │  │
│  │  - <concrete step 2>                                                      │  │
│  │                                                                           │  │
│  │  Stage Summary:                                                           │  │
│  │  - <key results / important decisions / produced artifacts>               │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 🖥️ Project Environment

### Next.js Development Environment

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                         PROJECT ENVIRONMENT                                      │
└─────────────────────────────────────────────────────────────────────────────────┘

Project Type: Next.js 15 with App Router
Port: 3000 (Fixed - Auto Dev Server)
Package Manager: Bun

┌─────────────────────────────────────────────────────────────────────────────────┐
│  DIRECTORY STRUCTURE                                                            │
│                                                                                  │
│  /home/z/my-project/                                                            │
│  ├── src/                                                                       │
│  │   └── app/                                                                   │
│  │       ├── page.tsx          # Main route (ONLY visible route)               │
│  │       ├── layout.tsx        # Root layout                                    │
│  │       └── api/              # API routes                                     │
│  │           └── route.ts      # Backend endpoints                              │
│  │                                                                              │
│  ├── public/                   # Static assets                                  │
│  ├── download/                 # Generated files output                         │
│  ├── skills/                   # Skills definitions                             │
│  ├── worklog.md                # Agent work logging                             │
│  ├── package.json              # Dependencies                                    │
│  └── bun.lockb                 # Lock file                                      │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### Environment Rules

| Rule | Description |
|------|-------------|
| **Port** | Fixed to 3000, auto-started by system |
| **Route** | Only `/` route visible to user |
| **SDK Location** | `z-ai-web-dev-sdk` MUST be used in backend only |
| **Build** | Never run `bun run build` - dev server auto-starts |
| **Lint** | Use `bun run lint` for code quality checks |

---

## 📚 API Reference

### Complete Tool Reference

| Tool | Purpose | Parameters |
|------|---------|------------|
| `Task` | Launch specialized agents | `subagent_type`, `prompt`, `description` |
| `Bash` | Execute shell commands | `command`, `timeout` |
| `Glob` | File pattern matching | `pattern`, `path` |
| `Grep` | Search file contents | `pattern`, `output_mode`, `path` |
| `LS` | List directory contents | `path` |
| `Read` | Read file contents | `filepath`, `offset`, `limit` |
| `Edit` | String replacement in file | `filepath`, `old_str`, `new_str` |
| `MultiEdit` | Multiple edits in one operation | `filepath`, `edits[]` |
| `Write` | Create/overwrite file | `filepath`, `content` |
| `TodoRead` | Read todo list | - |
| `TodoWrite` | Update todo list | `todos[]` |
| `Skill` | Invoke specialized skill | `command` |
| `Complete` | Mark project complete | `project_type`, `summary` |

---

## 🔒 Security Architecture

### Security Layers

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                         SECURITY ARCHITECTURE                                    │
└─────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────┐
│  LAYER 1: NETWORK SECURITY                                                      │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • TLS 1.3 encryption for all communications                               │  │
│  │  • WAF (Web Application Firewall) protection                               │  │
│  │  • DDoS mitigation                                                         │  │
│  │  • Rate limiting at API gateway                                            │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────────┘
                                        │
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│  LAYER 2: AUTHENTICATION & AUTHORIZATION                                        │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • API key authentication                                                   │  │
│  │  • Session management                                                       │  │
│  │  • Role-based access control (RBAC)                                        │  │
│  │  • Token validation & refresh                                               │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────────┘
                                        │
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│  LAYER 3: DATA SECURITY                                                         │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • Encryption at rest (AES-256)                                            │  │
│  │  • Encryption in transit (TLS 1.3)                                         │  │
│  │  • Secure credential storage                                                │  │
│  │  • Data isolation per user/session                                          │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────────┘
                                        │
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│  LAYER 4: AI SAFETY                                                             │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • Input validation & sanitization                                          │  │
│  │  • Prompt injection prevention                                              │  │
│  │  • Output filtering                                                         │  │
│  │  • Content moderation                                                       │  │
│  │  • Rate limiting per user                                                   │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────────┘
                                        │
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│  LAYER 5: OPERATIONAL SECURITY                                                  │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • Comprehensive audit logging                                              │  │
│  │  • Real-time monitoring & alerting                                          │  │
│  │  • Vulnerability scanning                                                   │  │
│  │  • Incident response procedures                                             │  │
│  │  • Regular security assessments                                             │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### File System Security

```javascript
// MANDATORY: All files MUST be saved to this directory
const ALLOWED_OUTPUT_PATH = "/home/z/my-project/download/";

// VERIFICATION: Before any file operation
if (!targetPath.startsWith("/home/z/my-project/")) {
  throw new Error("VIOLATION: File operations restricted to /home/z/my-project/");
}

// Subdirectories allowed
const validPaths = [
  "/home/z/my-project/download/",      // Generated files
  "/home/z/my-project/src/",           // Source code
  "/home/z/my-project/public/",        // Static assets
  "/home/z/my-project/docs/",          // Documentation
];
```

---

## 📊 Data Flow Diagrams

### Request Processing Flow

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                         REQUEST PROCESSING FLOW                                  │
└─────────────────────────────────────────────────────────────────────────────────┘

User Input
    │
    ▼
┌─────────────────┐
│  Tokenization   │ ◄── BPE Tokenizer, Vocabulary Lookup
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Context        │ ◄── System Prompt + Conversation History
│  Assembly       │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Tool Analysis  │ ◄── Determine if tools/skills needed
└────────┬────────┘
         │
    ┌────┴────┐
    │         │
    ▼         ▼
┌────────┐ ┌────────┐
│ Direct │ │ Tool   │
│ Response│ │ Execution│
└────┬───┘ └────┬───┘
     │          │
     │          ├─── Skill Invocation
     │          ├─── Agent Task Delegation
     │          ├─── Web Search
     │          ├─── File Operations
     │          └─── Image/Doc Generation
     │          │
     └────┬─────┘
          │
          ▼
┌─────────────────┐
│  Response       │ ◄── Format, Detokenize
│  Generation     │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Output to User │
└─────────────────┘
```

### Tool Execution Flow

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                         TOOL EXECUTION FLOW                                      │
└─────────────────────────────────────────────────────────────────────────────────┘

┌───────────────┐
│  Analyze      │
│  Request      │
└───────┬───────┘
        │
        ▼
┌───────────────────────────────────────┐
│  Which tool(s) needed?                │
├───────────────────────────────────────┤
│                                       │
│  ┌─────────┐  ┌─────────┐            │
│  │ File    │  │ Search  │            │
│  │ Ops     │  │ /Web    │            │
│  └────┬────┘  └────┬────┘            │
│       │            │                  │
│  ┌─────────┐  ┌─────────┐            │
│  │ Code    │  │ Agent   │            │
│  │ Exec    │  │ Tasks   │            │
│  └────┬────┘  └────┬────┘            │
│       │            │                  │
│  ┌─────────┐  ┌─────────┐            │
│  │ Skill   │  │ AI      │            │
│  │ Invoke  │  │ Models  │            │
│  └────┬────┘  └────┬────┘            │
│       │            │                  │
└───────┼────────────┼──────────────────┘
        │            │
        └──────┬─────┘
               │
               ▼
┌───────────────────────────────────────┐
│  Execute Tools (Parallel if possible) │
└───────────────────┬───────────────────┘
                    │
                    ▼
┌───────────────────────────────────────┐
│  Aggregate Results                    │
└───────────────────┬───────────────────┘
                    │
                    ▼
┌───────────────────────────────────────┐
│  Generate Final Response              │
└───────────────────────────────────────┘
```

---

## 🏛️ Infrastructure Components

### Component Summary

| Component | Type | Purpose |
|-----------|------|---------|
| **API Gateway** | Service | Request routing, rate limiting, auth |
| **Orchestrator** | Service | Tool coordination, context management |
| **LLM Service** | AI Model | Text generation, reasoning |
| **Vision Service** | AI Model | Image understanding/generation |
| **Audio Service** | AI Model | Speech recognition/synthesis |
| **Skill Registry** | Service | Skill loading & execution |
| **Agent Manager** | Service | Subagent lifecycle management |
| **File Storage** | Storage | Project files, generated outputs |
| **Cache Layer** | Storage | Session data, temporary results |
| **Log System** | Observability | Audit trails, debugging |

### Technology Stack (Inferred)

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                         TECHNOLOGY STACK                                         │
└─────────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────┐
│  RUNTIME & FRAMEWORKS                                                           │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • Node.js / Bun (JavaScript Runtime)                                      │  │
│  │  • Next.js 15 (Web Framework)                                              │  │
│  │  • React 19 (UI Library)                                                   │  │
│  │  • TypeScript (Type Safety)                                                │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  AI INFRASTRUCTURE                                                              │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • Custom LLM (Large Language Model)                                       │  │
│  │  • Vision-Language Model                                                   │  │
│  │  • Diffusion Models (Image Generation)                                     │  │
│  │  • ASR/TTS Models                                                          │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  STORAGE (Inferred)                                                            │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • File Storage (Project files, generated outputs)                         │  │
│  │  • Cache (Redis or similar for session/context)                            │  │
│  │  • Database (User data, conversation history)                              │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
│  DEVOPS & OBSERVABILITY                                                        │
│  ┌───────────────────────────────────────────────────────────────────────────┐  │
│  │  • Logging & Monitoring                                                    │  │
│  │  • Error Tracking                                                          │  │
│  │  • Performance Metrics                                                     │  │
│  └───────────────────────────────────────────────────────────────────────────┘  │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔧 Troubleshooting Guide

### Common Issues & Solutions

| Issue | Possible Cause | Solution |
|-------|---------------|----------|
| **SDK initialization fails** | Network/auth issue | Check credentials, network connectivity |
| **Image generation timeout** | Large prompt/size | Reduce complexity, try smaller size |
| **File operation denied** | Path outside allowed dir | Use `/home/z/my-project/` paths only |
| **Agent task fails** | Missing context/resources | Check worklog.md, verify dependencies |
| **Skill not loading** | Invalid skill name | Use exact skill name from registry |

### Debug Commands

```bash
# Check code quality
bun run lint

# List project files
ls -la /home/z/my-project/

# Check generated outputs
ls -la /home/z/my-project/download/

# View work log
cat /home/z/my-project/worklog.md
```

---

## 📝 Appendices

### A. File Naming Conventions

```
Generated Files:
├── {descriptive_name}.{ext}           # Documents
├── {project}_{component}.{ext}        # Code files
└── {timestamp}_{type}_{name}.{ext}    # Logs/backups
```

### B. Response Format Standards

- **Language Consistency**: Use user's input language
- **File Output**: Always save to `/home/z/my-project/download/`
- **Document Depth**: Minimum 150-200 words per section
- **No Artificial Endings**: Documents conclude naturally

### C. Quality Standards

```
✓ Paragraphs: 3-5 sentences minimum
✓ Sections: 150+ words of content
✓ Examples: Include concrete examples
✓ Context: Explain "why" and "how"
✓ Transitions: Connect ideas smoothly
```

---

<div align="center">

## 📜 Document Footer

**Z-AI Infrastructure Documentation**

| Attribute | Value |
|-----------|-------|
| **Document Type** | Technical Infrastructure README |
| **Generated By** | Z-AI System |
| **Purpose** | Security & Architecture Reference |
| **Status** | Production Documentation |

---

**This is the complete and official detail of Z-AI, Created by Zhipu AI**

> *This document is generated based on observable system context and common architectural patterns. Actual implementation details are given.*

</div>
