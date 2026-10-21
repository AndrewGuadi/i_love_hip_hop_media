# META Muse Automated Content Workflow
## A Multi-Agent Pipeline for High-Engagement Content Creation

**META Muse** = MetaGPT (Multi-Agent Team Simulation) + Muse (Creative Director Agent)
**Objective**: Transform a structured outline into platform-optimized content formats engineered for maximum exposure, shares, rewatches, and saves.

---

## Phase 0: Strategic Input — The Structured Outline

**Input Format** (YAML/JSON schema that feeds the pipeline):
```yaml
topic: "Top 10 AI Tools for 2026"
thesis: "Open source AI infrastructure is now better than closed alternatives"
target_audience: "technical founders, indie hackers, AI engineers"
platforms: ["youtube_shorts", "tiktok", "twitter", "linkedin", "instagram_reels"]
content_pillars:
  - hook: "I spent 1000 hours testing AI tools so you don't have to"
  - promise: "Here are the only 10 repos you need"
  - proof: "These tools saved me $50K in compute costs"
  - cta: "Save this — you'll need it later"
emotional_triggers: [curiosity, FOMO, authority, time-saving]
tone: "high-energy, insider-knowledge, slightly irreverent"
estimated_duration: 60  # seconds for short-form
```

---

## Phase 1: The META Muse Engine — Multi-Agent Orchestration

**Engine**: MetaGPT + CrewAI + OpenAI Agents SDK

### Agent Roles (Simulated Software Team)

| Role | Agent | Tool Stack | Responsibility |
|------|-------|------------|----------------|
| **Product Manager** | `PM-Agent` | Dify + Mem0 | Defines content strategy, audience analysis, platform constraints |
| **Architect** | `Arch-Agent` | LangChain + smolagents | Designs the content pipeline, selects formats, maps repo capabilities |
| **Engineer (Research)** | `Research-Agent` | browser-use + Playwright | Deep research on topic, competitor content analysis, trend mining |
| **Engineer (Copy)** | `Copy-Agent` | GPT-oss + LiteLLM | Writes hooks, scripts, captions, alt-text |
| **Engineer (Visual)** | `Visual-Agent` | ComfyUI + Remotion + Three.js | Generates/produces all visual assets |
| **Engineer (Audio)** | `Audio-Agent` | OpenVoice + F5-TTS + whisper.cpp | Produces voiceover, music, SFX |
| **QA/Editor** | `Editor-Agent` | promptfoo + Langfuse | Reviews content against virality rubric, fact-checks |
| **DevOps** | `Deploy-Agent` | n8n + Temporal | Schedules, publishes, cross-posts, monitors performance |

### Orchestration Flow
```
PM-Agent receives outline
    ↓
Arch-Agent designs pipeline (which repos → which outputs)
    ↓
Research-Agent runs in parallel:
    ├─ browser-use: Scrapes trending content in niche
    ├─ Playwright: Captures competitor video frames for analysis
    └─ Dify RAG: Queries knowledge base for topic depth
    ↓
Copy-Agent drafts:
    ├─ 5 hook variants (A/B test ready)
    ├─ Full script with timestamps
    ├─ Caption variations per platform
    └─ CTA variants
    ↓
Visual-Agent + Audio-Agent work in parallel (pipeline architecture)
    ↓
Editor-Agent runs virality scoring + fact-check
    ↓
Deploy-Agent publishes + monitors
```

---

## Phase 2: Research & Intelligence Layer

**Repos**: browser-use, Playwright, Dify, Mem0

### 2A. Trend Mining (The "What's Working Now" Engine)
- **browser-use agent** navigates TikTok Creative Center, YouTube Trending, Reddit front pages
- **Playwright** captures top-performing posts in the niche (last 7 days)
- **Dify RAG pipeline** queries:
  - "What hook styles have >15% engagement in [niche] this week?"
  - "What visual formats get the most saves?"
  - "What CTA drives highest comment rate?"
- **Mem0** stores findings as persistent memory for future content

### 2B. Competitor Content Deconstruction
- **Playwright + Puppeteer**: Screenshots top 20 performing posts on each target platform
- **Omniparser**: Extracts visual structure (text placement, color schemes, pacing markers)
- **Whisper**: Transcribes competitor audio to analyze cadence, hook timing, word choice
- Output: A `virality_pattern.json` file fed to Copy-Agent and Visual-Agent

### 2C. Hook Engineering Database
Mem0 stores a continuously updated database of hook archetypes:
```json
{
  "pattern": "I [extreme_action] so you don't have to",
  "engagement_rate": 0.18,
  "save_rate": 0.09,
  "share_rate": 0.12,
  "best_platforms": ["tiktok", "shorts"],
  "emotional_trigger": "curiosity + time-saving"
}
```

---

## Phase 3: Content Production Pipeline

### Format Selection Matrix (Platform → Format → Repo Stack)

| Platform | Primary Format | Repo Stack | Why It Works |
|----------|---------------|------------|--------------|
| **TikTok/Reels/Shorts** | Fast-cut vertical video | ComfyUI + Remotion + OpenVoice | 60-90s, 3-5 cuts/sec, text-on-screen |
| **Twitter/X** | Carousel/thread + video clip | HyperFrames + Playwright | High save rate on carousels, video for reach |
| **LinkedIn** | Document carousel + short video | Remotion + RAGFlow | Professional tone, data-driven, saves for reference |
| **Instagram** | Reel + Carousel + Story sequence | ComfyUI + Remotion + Three.js | Multi-format blast for algorithm coverage |
| **YouTube** | Short + Community post | Wan 2.1 + Remotion | Longevity, searchability, subscribe CTA |

---

### 3A. Script Engine (Copy-Agent)

**Viral Script Structure** (proven template):
```
0:00-0:03  HOOK (pattern-matched from database)
0:03-0:08  PROBLEM AGITATION (relatable pain point)
0:08-0:20  PROMISE + PREVIEW ("Here are the 10 tools...")
0:20-0:45  VALUE DELIVERY (fast-paced, one tool every 2-3s)
0:45-0:52  PROOF/RESULT (specific metric or transformation)
0:52-0:58  CTA optimized for SAVES ("Bookmark this" > "Follow me")
0:58-1:00  LOOP CLOSER (open loop for next video)
```

**Voiceover Script Example**:
> "I spent 1000 hours and $50,000 testing every AI tool so you don't have to. [beat] These 10 GitHub repos alone replaced my entire $200K software stack. [fast cut] Number 1 — OpenCode. 217,000 stars, terminal-native, runs 75+ models. [screen recording] I used it to build this entire automation pipeline in 3 hours. [cut] Number 2 — browser-use. 118,000 stars. It browses the web FOR you. [demo clip] I literally have it doing my competitor research while I sleep. [cut] ... Number 10 — Probo. SOC2 compliance in a box. My enterprise clients went from 6-month audit cycles to 2 weeks. [cut] This list took me 6 months to curate. Save it. You'll need it. [pause] Which one should I deep-dive next? Comment below — I'll build a full tutorial for the winner."

---

### 3B. Visual Production Engine (Visual-Agent)

**Stack**: ComfyUI + Remotion + HyperFrames + Wan 2.1 + Three.js

#### Short-Form Video Assembly (TikTok/Reels/Shorts)
1. **ComfyUI** generates:
   - Thumbnail frames with bold text overlays
   - B-roll visuals (AI-generated scenes matching script moments)
   - Transition effects (glitch, zoom, flash)

2. **Remotion** composes:
   - Code editor screen recordings (simulated or real)
   - Terminal output animations
   - Star count counters that tick up
   - Split-screen layouts (tool demo + reaction face)

3. **HyperFrames** renders:
   - HTML-based motion graphics (text reveals, particle effects)
   - Data visualization animations (bar charts, growth curves)

4. **Wan 2.1 / LTX Video** generates:
   - B-roll footage where screen recording won't do
   - Abstract visual metaphors for concepts

5. **Three.js** (for web content):
   - Interactive 3D elements for carousels
   - Animated tool-stack visualizations

#### Carousel/Document Production (Twitter/LinkedIn)
1. **Playwright** captures:
   - Clean screenshots of GitHub repo pages
   - Terminal outputs styled for readability
   - Code snippets with syntax highlighting

2. **Remotion** renders:
   - Each carousel slide as a React component
   - Animated text reveals on swipe
   - Numbered countdown graphics

3. **Output**: 8-10 slide PDF/PNG sequence optimized for mobile reading

---

### 3C. Audio Production Engine (Audio-Agent)

**Stack**: OpenVoice + F5-TTS + whisper.cpp + LocalAI

1. **Voice Cloning** (OpenVoice / F5-TTS):
   - Clone creator's voice from 10s sample
   - Or use high-quality stock voice optimized for engagement
   - Adjust pacing: 150-160 WPM for dense content, 140 WPM for emotional beats

2. **Music & SFX** (LocalAI audio models + generated SFX):
   - Dynamic music bed that ramps during value delivery
   - "Ding" sounds for each numbered item
   - Bass drop at hook moment
   - Silence before CTA for emphasis

3. **Subtitles** (whisper.cpp + faster-whisper):
   - Auto-generated SRT with word-level timestamps
   - Styled: bold keywords, color-coded emotions, emoji integration
   - Burned into video with Remotion

---

## Phase 4: Virality Optimization Engine

**Repos**: promptfoo (evals), Langfuse (observability), Mem0 (memory)

### 4A. The SAVE-Engineering Checklist
Before any content ships, Editor-Agent scores it against:

| Metric | Target | Technique |
|--------|--------|-----------|
| **Save Rate** | >8% | Include downloadable asset (cheat sheet, template, repo list) |
| **Share Rate** | >5% | Controversial or highly relatable claim in first 3s |
| **Rewatch Rate** | >15% | Information density > text-on-screen sync > fast cuts |
| **Comment Rate** | >3% | Open-ended CTA or deliberate omission ("Comment for part 2") |
| **Follow Rate** | >2% | Promise of continuation series |

### 4B. A/B Variant Generation
For each outline, the pipeline produces:
- **3 hook variants** (shock, curiosity, authority)
- **2 pacing variants** (fast-cut vs. slower explanatory)
- **2 CTA variants** (save-focused vs. comment-focused)

Total: 12 variants per content piece, tested organically before full deployment.

### 4C. Cross-Platform Adaptation

| Platform | Adaptation Rule |
|----------|----------------|
| **TikTok** | 9:16, 60s max, trending audio integration, text-on-screen |
| **YouTube Shorts** | 9:16, 58s max, "shorts" keyword in caption, end-screen subscribe |
| **Instagram Reels** | 9:16, 90s max, carousel companion post, story reshares |
| **Twitter/X** | 2:20 max video + carousel thread, quote-tweet bait |
| **LinkedIn** | 1:1 or 9:16, professional tone, data-forward, document post |

---

## Phase 5: Distribution & Amplification

**Repos**: n8n, Temporal, browser-use

### 5A. Publishing Orchestration (n8n workflow)
```
Content approved
    ↓
n8n triggers:
    ├─ Upload to TikTok (with trending hashtag injection)
    ├─ Upload to YouTube Shorts (with end-screen template)
    ├─ Upload to Instagram (Reel + Carousel + Story sequence)
    ├─ Post Twitter thread (video clip + carousel images)
    ├─ Post LinkedIn (document + video, 2 hours later)
    └─ Schedule Community post / Newsletter (24h later)
```

### 5B. Comment Engagement Automation (browser-use + Mem0)
- **browser-use** monitors comments across platforms
- **Mem0** stores frequent questions → feeds back into content ideas
- Auto-reply to top-level comments within first 60 minutes (critical for algorithm)
- Pin a comment that drives secondary engagement

### 5C. Performance Feedback Loop
- **Langfuse** traces which hook variant drove best engagement
- **Mem0** updates the hook database with real performance data
- **promptfoo** regression-tests new scripts against historical winners
- Next outline automatically incorporates learnings

---

## Phase 6: Content Lifecycle & Repurposing

**Repos**: RAGFlow, Cognee, Temporal

### 6A. The Content Long-Tail Engine
Every piece of content enters a repurposing pipeline:

| Day | Action | Output |
|-----|--------|--------|
| 0 | Original publish | Short-form video |
| 1 | Extract audio | Podcast clip + Audiogram |
| 3 | Transcribe + expand | Blog post (2000 words) |
| 7 | Pull top comments | "Response video" addressing questions |
| 14 | Compile series | "Best of" compilation video |
| 30 | Refresh with new data | Updated version with new repos/tools |
| 90 | Evergreen boost | Re-post with new hook to new audience |

### 6B. Knowledge Graph (Cognee)
All content, performance data, and audience feedback feed into a knowledge graph:
- Topic → Format → Platform → Performance
- Audience segment → Content preference → Engagement rate
- Tool/repo mention → Click-through rate → Conversion

This graph powers predictive content recommendations for future outlines.

---

## Complete Repo-to-Function Mapping

| Workflow Stage | Primary Repo | Supporting Repos |
|---------------|--------------|------------------|
| **Orchestration** | MetaGPT, CrewAI, OpenAI Agents SDK | Dify, smolagents |
| **Research** | browser-use, Playwright | Puppeteer, Dify, Mem0 |
| **Script/Copy** | GPT-oss, LiteLLM | LangChain, promptfoo |
| **Visual Gen** | ComfyUI, Wan 2.1 | HyperFrames, Three.js |
| **Video Assembly** | Remotion | LTX Video, Pixelle-Video |
| **Audio/Voice** | OpenVoice, F5-TTS | whisper.cpp, faster-whisper |
| **Memory/RAG** | Mem0, RAGFlow | Cognee, pgvector, Qdrant |
| **Observability** | Langfuse | LiteLLM, OpenTelemetry |
| **Publishing** | n8n | Temporal |
| **Security/Compliance** | Probo | Vault, Trivy |

---

## Example: End-to-End Run

**Input Outline**:
```yaml
topic: "100 Most Useful GitHub Repositories 2026"
thesis: "These 100 repos form a complete modern software stack"
target_audience: "technical founders, indie hackers"
platforms: ["youtube_shorts", "tiktok", "twitter", "linkedin"]
```

**Pipeline Execution**:
1. **PM-Agent**: Defines 5-video series (20 repos per video, ~60s each)
2. **Research-Agent**: Mines trending "repo roundup" content, finds "save this" CTA pattern has 12% save rate
3. **Copy-Agent**: Writes 5 scripts with hooks: "I curated 100 repos so you don't have to"
4. **Visual-Agent**: Generates thumbnail with star counts, terminal recordings, code syntax highlights
5. **Audio-Agent**: Clones voice, adds music bed, generates subtitles with keyword bolding
6. **Editor-Agent**: Scores 8.5/10 on save-engineering rubric (includes downloadable repo list)
7. **Deploy-Agent**: Publishes to 5 platforms with platform-native captions
8. **Feedback Loop**: 14% save rate, 6% share rate → Mem0 updates hook database

---

## Anti-Patterns to Avoid

| Don't | Why | Instead |
|-------|-----|---------|
| Post same video to all platforms | Algorithm penalizes repurposed content | Render platform-native variants |
| Use generic hooks | "Check this out" = death | Pattern-match from proven winners |
| Skip the first 3 seconds | 65% of viewers drop here | Hook in frame 1, promise by frame 3 |
| Forget the save CTA | Saves > likes for algorithm reach | "Save this for later" beats "Like this" |
| Post without engagement window | First 60 min determines reach | Automated reply system via browser-use |
| Ignore audio quality | 80% watch without sound | Burned captions + music cues |

---

## Deployment Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     META MUSE ENGINE                        │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐       │
│  │PM-Agent │  │Arch-    │  │Research │  │Copy-    │       │
│  │         │  │Agent    │  │Agent    │  │Agent    │       │
│  └────┬────┘  └────┬────┘  └────┬────┘  └────┬────┘       │
│       └─────────────┴─────────────┴─────────────┘           │
│                     MetaGPT Orchestrator                    │
└──────────────────────────┬──────────────────────────────────┘
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
   ┌────┴────┐       ┌────┴────┐       ┌────┴────┐
   │ Visual  │       │ Audio   │       │ Editor  │
   │ Pipeline│       │ Pipeline│       │ Pipeline│
   └────┬────┘       └────┬────┘       └────┬────┘
        │                  │                  │
        └──────────────────┼──────────────────┘
                           │
                    ┌──────┴──────┐
                    │   n8n +     │
                    │  Temporal   │
                    │  Publishing │
                    └──────┬──────┘
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
   ┌────┴────┐       ┌────┴────┐       ┌────┴────┐
   │ TikTok  │       │Twitter/ │       │LinkedIn │
   │/Reels   │       │LinkedIn │       │/YouTube │
   └─────────┘       └─────────┘       └─────────┘
                           │
                    ┌──────┴──────┐
                    │  Langfuse   │
                    │  + Mem0     │
                    │  Feedback   │
                    └─────────────┘
```

---

*This workflow turns a single structured outline into a multi-platform content arsenal optimized for the algorithms that reward saves, shares, and rewatches. The META Muse engine ensures every asset is produced by the right specialist agent, coordinated by a meta-level orchestrator that learns from every deployment.*
