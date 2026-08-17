<div align="center">

# 🧠 Meeting Architect

### Role-Aware Virtual Meeting Intelligence System

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.30+-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io)
[![Ollama](https://img.shields.io/badge/Ollama-Local_LLM-000000?style=for-the-badge&logo=ollama&logoColor=white)](https://ollama.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-00f0ff?style=for-the-badge)](LICENSE)

**Turn raw meeting transcripts and recordings into structured, role-aware intelligence — including summaries, key decisions, action items, and priorities.**

**Built with local AI inference to keep meeting data on your machine.**

</div>

---

## 📌 Overview

**Meeting Architect** is a local-first meeting intelligence system that transforms raw meeting transcripts and audio/video recordings into structured, actionable information.

Instead of producing the same generic meeting summary for everyone, Meeting Architect analyzes conversations from different stakeholder perspectives.

The system currently supports:

- 🔧 Engineering
- 📦 Product
- 📊 Management

Each perspective focuses on the information most relevant to that role, helping stakeholders quickly understand what happened, what was decided, what needs to be done, and what requires attention.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔒 **Local & Private** | Run AI inference locally with no external AI APIs required. Meeting data remains on your machine. |
| 🧠 **Role-Aware Analysis** | Analyze meetings from Engineering, Product, or Management perspectives with role-specific priorities. |
| 🎙️ **Audio & Video Transcription** | Upload meeting recordings and transcribe them locally using Whisper. |
| 📝 **Transcript Analysis** | Paste an existing transcript and generate structured meeting intelligence instantly. |
| ⚡ **Structured Output** | Generate validated results containing summaries, key decisions, and action items. |
| 🗄️ **Meeting Vault** | Automatically save previous analyses locally for later review. |
| 🏷️ **Automatic Categorization** | Categorize meetings by relevant departments using keyword-based classification. |
| 🎨 **Interactive UI** | Custom Streamlit interface with 3D visual elements and glassmorphism styling. |

---

## 🏗️ Architecture

Meeting Architect follows a local-first architecture where transcription, LLM inference, structured validation, and storage are handled locally.

The system consists of three main layers:

1. **Presentation Layer**
   - Streamlit interface
   - Transcript Analyzer
   - Media Analyzer
   - Meeting Vault

2. **Core Intelligence Layer**
   - Whisper for speech-to-text
   - Ollama/Gemma for meeting analysis
   - Role-specific prompts
   - Pydantic schemas for structured output

3. **Storage Layer**
   - Local JSON-based storage
   - Meeting history
   - Analysis results

```text
┌─────────────────────────────────────────────────────────┐
│                     Streamlit UI                        │
│                                                         │
│  ┌──────────────┐  ┌──────────────┐  ┌───────────────┐ │
│  │ Landing Page │  │  Transcript  │  │ Media Upload  │ │
│  │  (Three.js)  │  │   Analyzer   │  │   Analyzer    │ │
│  └──────────────┘  └──────┬───────┘  └───────┬───────┘ │
│                           │                  │         │
│  ┌────────────────────────┴──────────────────┘         │
│  │                 Meeting Vault                       │
│  └────────────────────────┬──────────────────────────┘ │
├───────────────────────────┼─────────────────────────────┤
│                    Core Intelligence                     │
│                                                         │
│  ┌───────────┐  ┌────────┴────────┐  ┌──────────────┐  │
│  │  Whisper  │  │ MeetingAnalyzer │  │   Storage /  │  │
│  │   (STT)   │  │ (Ollama/Gemma)  │  │    Vault     │  │
│  └───────────┘  └────────┬────────┘  └──────────────┘  │
│                          │                              │
│  ┌───────────┐  ┌────────┴────────┐  ┌──────────────┐  │
│  │   Audio   │  │  Role Prompts   │  │   Pydantic   │  │
│  │ Processor │  │   (per role)    │  │    Schema    │  │
│  └───────────┘  └─────────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
