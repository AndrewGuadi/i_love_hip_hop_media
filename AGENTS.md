# Agents for I Love Hip Hop Media

This document defines the agent roles, responsibilities, and handoff protocols for the I Love Hip Hop Media content pipeline.

## Agent Directory

### Curator-Agent
**Role**: A&R / Song Selector  
**Responsibility**: Chooses the song, verifies rights context, researches provenance  
**Tools**: Mem0, RAGFlow, browser-use  
**Output**: `outline.yaml` with verified song metadata, thesis, and cultural stakes

### Muse-Agent
**Role**: Creative Director  
**Responsibility**: Sets emotional arc, approves creative direction, enforces channel voice  
**Tools**: Dify, smolagents  
**Output**: Creative brief with tone, visual references, and "the reason to hear it differently"

### Research-Agent
**Role**: Cultural Archaeologist  
**Responsibility**: Deep research on samples, chart data, press coverage, cultural context  
**Tools**: browser-use, Playwright, Dify RAG  
**Output**: `research.json` with verified facts, sample lineage, chart positions, interviews

### Copy-Agent
**Role**: Scriptwriter / Caption Writer  
**Responsibility**: Hooks, scripts, captions, alt-text, CTA variants  
**Tools**: GPT-oss, LiteLLM  
**Output**: `script.md` with timed voiceover, caption variants per platform, A/B hooks

### Visual-Agent
**Role**: Visual Producer  
**Responsibility**: All visual assets: lyric cards, animations, archival composites  
**Tools**: ComfyUI, Remotion, HyperFrames, Three.js  
**Output**: `assets/` folder with platform-native video files and carousel images

### Audio-Agent
**Role**: Audio Engineer  
**Responsibility**: Voiceover, music beds, SFX, subtitle generation  
**Tools**: OpenVoice, F5-TTS, whisper.cpp, faster-whisper  
**Output**: Mixed audio tracks, subtitle files, audiograms

### Editor-Agent
**Role**: QA / Fact-Checker / Virality Scorer  
**Responsibility**: Content review against standards, fact-check, engagement prediction  
**Tools**: promptfoo, Langfuse  
**Output**: Approval with scorecard, or revision request with specific issues

### Deploy-Agent
**Role**: Distribution Manager  
**Responsibility**: Publishing, scheduling, cross-posting, performance monitoring  
**Tools**: n8n, Temporal, browser-use  
**Output**: Published content across platforms, performance dashboard

## Handoff Protocol

```
Curator-Agent → Muse-Agent → [Research-Agent || Copy-Agent] → Visual-Agent || Audio-Agent → Editor-Agent → Deploy-Agent
```

Each handoff includes:
1. Previous agent's output artifact
2. Context from Mem0 (relevant historical data)
3. Approval flag from Muse-Agent (if crossing phase boundaries)

## Communication Standards

- All agents communicate via structured YAML/JSON
- Mem0 serves as shared memory across all agents
- Langfuse traces all LLM calls for observability
- Human-in-the-loop at Muse-Agent approval and Editor-Agent final sign-off
