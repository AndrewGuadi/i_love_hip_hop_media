# META Muse Automated Content Workflow
## For I Love Hip Hop Media

**META Muse** = MetaGPT (Multi-Agent Team Simulation) + Muse (Creative Director Agent)

This workflow adapts the META Muse engine specifically for the I Love Hip Hop Media channel — a song-first hip-hop channel where every post gives people a particular song and a reason to hear it differently.

---

## Phase 0: The Outline — Song-First Input Format

Every piece of content starts with a structured outline that respects the channel's core principle: **the song comes first**.

```yaml
content_type: "song_breakdown"  # or "album_retrospective", "artist_deep_dive", "culture_moment"
song:
  title: "I Used to Love H.E.R."
  artist: "Common"
  album: "Resurrection"
  year: 1994
  producer: "No I.D."
  sample_source: "The Rotations - I Love Her"
thesis: "Common personified hip-hop as a woman he fell in love with, then watched change — and the betrayal he felt mirrors every fan's tension with the genre's evolution"
 emotional_arc: [nostalgia, betrayal, acceptance, hope]
target_audience: "hip-hop heads 25-40, conscious rap fans, people who miss 'real hip-hop'"
platforms: ["youtube_shorts", "tiktok", "instagram_reels", "twitter", "linkedin"]
content_pillars:
  - hook: "They said this song killed conscious rap. They were wrong."
  - promise: "Why Common's love letter to hip-hop is more relevant in 2026 than ever"
  - proof: "The sample, the double meaning, the production — every layer explained"
  - cta: "Save this for your next deep dive"
tone: "conversational authority, reverent but not preachy, insider knowledge shared generously"
format_preference: "narrated_visual"  # voiceover + archival footage + lyrics on screen
estimated_duration: 90  # seconds for short-form
```

---

## Phase 1: The META Muse Engine — Multi-Agent Orchestration

### Agent Roles (Simulated Creative Team)

| Role | Agent | Tool Stack | Responsibility |
|------|-------|------------|----------------|
| **A&R / Curator** | `Curator-Agent` | Mem0 + RAGFlow | Selects the song, verifies rights, researches context |
| **Creative Director** | `Muse-Agent` | Dify + smolagents | Sets the emotional arc, approves creative direction |
| **Researcher** | `Research-Agent` | browser-use + Playwright | Deep research: samples, interviews, cultural context, charts |
| **Copywriter** | `Copy-Agent` | GPT-oss + LiteLLM | Writes hooks, scripts, captions, alt-text |
| **Visual Producer** | `Visual-Agent` | ComfyUI + Remotion + Three.js | Generates/produces all visual assets |
| **Audio Engineer** | `Audio-Agent` | OpenVoice + F5-TTS + whisper.cpp | Produces voiceover, music beds, SFX |
| **Editor / QA** | `Editor-Agent` | promptfoo + Langfuse | Reviews against channel standards, fact-checks |
| **Distribution** | `Deploy-Agent` | n8n + Temporal | Schedules, publishes, cross-posts, monitors |

### Orchestration Flow
```
Curator-Agent selects song + thesis
    ↓
Muse-Agent approves creative direction
    ↓
Research-Agent runs in parallel:
    ├─ browser-use: Scrapes Genius, Discogs, interviews, chart data
    ├─ Playwright: Captures album artwork, press photos, archival footage
    └─ Dify RAG: Queries hip-hop knowledge base for cultural context
    ↓
Copy-Agent drafts:
    ├─ 5 hook variants (A/B test ready)
    ├─ Full script with timestamps
    ├─ Caption variations per platform
    └─ CTA variants
    ↓
Visual-Agent + Audio-Agent work in parallel
    ↓
Editor-Agent runs quality scoring + fact-check
    ↓
Deploy-Agent publishes + monitors
```

---

## Phase 2: Research & Intelligence Layer

**Repos**: browser-use, Playwright, Dify, Mem0

### 2A. Cultural Archaeology (The "What Makes This Song Matter" Engine)
- **browser-use agent** navigates Genius, WhoSampled, Discogs, Billboard, streaming platforms
- **Playwright** captures:
  - Album artwork at high resolution
  - Chart performance data
  - Press coverage from release era
  - Artist interviews about the track
- **Dify RAG pipeline** queries:
  - "What samples does this song use and what's their significance?"
  - "How did critics receive this track on release?"
  - "What cultural moment was this song part of?"
  - "What later artists referenced or sampled this?"
- **Mem0** stores findings as persistent memory for future content about the artist, era, or style

### 2B. Competitor Content Deconstruction
- **Playwright + Puppeteer**: Screenshots top 20 performing hip-hop breakdown posts on each target platform
- **Omniparser**: Extracts visual structure (text placement, color schemes, pacing markers, when lyrics appear)
- **Whisper**: Transcribes competitor audio to analyze cadence, hook timing, word choice, music bed style
- Output: A `hip_hop_virality_pattern.json` file fed to Copy-Agent and Visual-Agent

### 2C. Hook Engineering Database
Mem0 stores a continuously updated database of hook archetypes specific to hip-hop content:
```json
{
  "pattern": "They said [controversial_claim]. They were wrong.",
  "engagement_rate": 0.16,
  "save_rate": 0.08,
  "share_rate": 0.11,
  "best_platforms": ["tiktok", "shorts", "twitter"],
  "emotional_trigger": "nostalgia + authority + mild controversy"
}
```

---

## Phase 3: Content Production Pipeline

### Format Selection Matrix (Platform → Format → Repo Stack)

| Platform | Primary Format | Repo Stack | Why It Works for Hip-Hop |
|----------|---------------|------------|-------------------------|
| **TikTok/Reels/Shorts** | Fast-cut vertical video | ComfyUI + Remotion + OpenVoice | 60-90s, lyrics on screen, archival footage, beat drops synced to cuts |
| **Twitter/X** | Carousel/thread + video clip | HyperFrames + Playwright | Lyric breakdowns as swipeable cards, video for reach |
| **LinkedIn** | Document carousel + short video | Remotion + RAGFlow | Cultural analysis with data, saves for reference |
| **Instagram** | Reel + Carousel + Story sequence | ComfyUI + Remotion + Three.js | Multi-format blast, Stories for behind-the-scenes |
| **YouTube** | Short + Community post | Wan 2.1 + Remotion | Longevity, searchability, subscribe CTA |

---

### 3A. Script Engine (Copy-Agent)

**Hip-Hop Script Structure** (proven 90s template):
```
0:00-0:03  HOOK (pattern-matched from database)
0:03-0:08  THE SONG (title + artist, establish credibility)
0:08-0:15  THE STAKES (why this song matters now)
0:15-0:35  THE BREAKDOWN (sample origin, double meanings, production details)
0:35-0:50  THE CULTURAL MOMENT (what was happening in hip-hop when this dropped)
0:50-0:82  THE PAYOFF (how this connects to today's hip-hop)
0:82-0:88  CTA optimized for SAVES ("Save this for your next deep dive")
0:88-0:90  LOOP CLOSER ("What's YOUR hip-hop song that deserves a breakdown?")
```

**Voiceover Script Example** (Common — I Used to Love H.E.R.):
> "They said this song killed conscious rap. They were wrong. [beat drop] In 1994, Common dropped 'I Used to Love H.E.R.' — but H.E.R. wasn't a woman. She was hip-hop itself. [cut to lyric card] 'I met her when I was 10, back in '82.' He's talking about how he fell in love with hip-hop's innocence. [cut] The sample? The Rotations, 'I Love Her,' 1966. No I.D. flipped it into something that sounds like memory feels. [cut] But here's the twist — Common's mourning how hip-hop 'went commercial.' Radio play, music videos, West Coast gangsta rap. [cut] The irony? This song MADE him commercial. It put Chicago hip-hop on the map. [cut] Fast forward to 2026. Every 'hip-hop is dead' debate is just a remix of what Common already said. The genre didn't die. It evolved. And loving it means loving ALL its phases. [cut] Save this for your next deep dive. [pause] What's YOUR hip-hop song that deserves a breakdown? Comment — I'll research it."

---

### 3B. Visual Production Engine (Visual-Agent)

**Stack**: ComfyUI + Remotion + HyperFrames + Wan 2.1 + Three.js

#### Short-Form Video Assembly (TikTok/Reels/Shorts)
1. **ComfyUI** generates:
   - Stylized lyric cards (typography matching the era's aesthetic)
   - Album artwork variations and animations
   - Transition effects (vinyl scratch, boombox static, VHS glitch)

2. **Remotion** composes:
   - Archival footage sequences (press photos, live performance clips)
   - Animated waveform visualizations synced to the track
   - "Sample family tree" animations showing what this song sampled and what sampled it
   - Split-screen layouts (lyrics on left, context on right)

3. **HyperFrames** renders:
   - HTML-based motion graphics (lyrics appearing word-by-word)
   - Data visualization animations (chart positions over time, streaming numbers)

4. **Wan 2.1 / LTX Video** generates:
   - Abstract visual metaphors for the song's themes
   - B-roll where archival footage isn't available

5. **Three.js** (for web content):
   - Interactive 3D turntable animations for carousels
   - Rotating vinyl record visualizations

#### Carousel/Document Production (Twitter/LinkedIn)
1. **Playwright** captures:
   - Clean screenshots of Genius lyrics pages
   - Discogs release pages
   - Streaming platform pages

2. **Remotion** renders:
   - Each carousel slide as a React component
   - Animated text reveals on swipe
   - "Did you know?" fact cards with subtle motion

3. **Output**: 8-10 slide PDF/PNG sequence optimized for mobile reading

---

### 3C. Audio Production Engine (Audio-Agent)

**Stack**: OpenVoice + F5-TTS + whisper.cpp + LocalAI

1. **Voice Cloning** (OpenVoice / F5-TTS):
   - Clone Andrew's voice from sample recordings
   - Or use a voice optimized for hip-hop commentary (warm, knowledgeable, unhurried)
   - Adjust pacing: 140-150 WPM for storytelling, 160 WPM for facts, pause before punchlines

2. **Music & SFX** (LocalAI audio models + generated SFX):
   - Low-volume instrumental bed from the discussed song (fair use / licensed)
   - Vinyl crackle and boom bass transitions between sections
   - Silence before the thesis statement for impact
   - Beat drop synced to the hook moment

3. **Subtitles** (whisper.cpp + faster-whisper):
   - Auto-generated SRT with word-level timestamps
   - Styled: bold on punchlines, italic on lyrics, color-coded for emotional shifts
   - Burned into video with Remotion

---

## Phase 4: Virality Optimization Engine

**Repos**: promptfoo (evals), Langfuse (observability), Mem0 (memory)

### 4A. The SAVE-Engineering Checklist for Hip-Hop
Before any content ships, Editor-Agent scores it against:

| Metric | Target | Technique |
|--------|--------|-----------|
| **Save Rate** | >8% | Include downloadable asset (playlist, sample map, lyric breakdown PDF) |
| **Share Rate** | >5% | Controversial but defensible take in first 3s ("They were wrong") |
| **Rewatch Rate** | >15% | Lyric double-meanings that require second viewing, sample origin reveals |
| **Comment Rate** | >3% | Open-ended CTA asking for THEIR song ("Comment yours — I'll research it") |
| **Follow Rate** | >2% | Promise of continuation series ("Part 2 drops Thursday") |

### 4B. A/B Variant Generation
For each outline, the pipeline produces:
- **3 hook variants**:
  - Shock: "They said this song killed conscious rap."
  - Curiosity: "The song that made Common famous was actually a breakup letter."
  - Authority: "Every 'hip-hop is dead' debate starts with this 1994 song."
- **2 pacing variants** (fast-cut vs. slower storytelling)
- **2 CTA variants** (save-focused vs. comment-focused)

Total: 12 variants per content piece, tested organically before full deployment.

### 4C. Cross-Platform Adaptation

| Platform | Adaptation Rule |
|----------|----------------|
| **TikTok** | 9:16, 60-90s, trending audio integration (when legally clear), lyrics on screen, fast cuts on beat drops |
| **YouTube Shorts** | 9:16, 58s max, "hip hop" + song title in caption, end-screen subscribe |
| **Instagram Reels** | 9:16, 90s max, carousel companion post with sample map, Story reshares with poll stickers |
| **Twitter/X** | 2:20 max video + carousel thread, quote-tweet bait with controversial but true take |
| **LinkedIn** | 1:1 or 9:16, cultural analysis angle, data-forward (chart positions, streaming numbers), document post |

---

## Phase 5: Distribution & Amplification

**Repos**: n8n, Temporal, browser-use

### 5A. Publishing Orchestration (n8n workflow)
```
Content approved by Muse-Agent
    ↓
n8n triggers sequential publishing:
    ├─ Upload to TikTok (with trending hip-hop hashtag injection)
    ├─ Upload to YouTube Shorts (with end-screen subscribe template)
    ├─ Upload to Instagram (Reel + Carousel + Story sequence)
    ├─ Post Twitter thread (video clip + carousel images with sample map)
    ├─ Post LinkedIn (document + video, 2 hours later for business audience)
    └─ Schedule Community post / Newsletter (24h later with extended essay)
```

### 5B. Comment Engagement Automation (browser-use + Mem0)
- **browser-use** monitors comments across platforms
- **Mem0** stores:
  - Song requests from comments (future content pipeline)
  - Corrections and additional context (community-sourced research)
  - Debates and reactions (sentiment tracking)
- Auto-reply to top-level comments within first 60 minutes (critical for algorithm)
- Pin a comment that drives secondary engagement ("Drop YOUR song below — I'll pick one for next week")

### 5C. Performance Feedback Loop
- **Langfuse** traces which hook variant drove best engagement per platform
- **Mem0** updates the hip-hop hook database with real performance data
- **promptfoo** regression-tests new scripts against historical winners
- Next outline automatically incorporates learnings

---

## Phase 6: Content Lifecycle & Repurposing

**Repos**: RAGFlow, Cognee, Temporal

### 6A. The Content Long-Tail Engine
Every piece of content enters a repurposing pipeline:

| Day | Action | Output |
|-----|--------|--------|
| 0 | Original publish | Short-form video breakdown |
| 1 | Extract audio | Podcast clip + Audiogram for Spotify/Apple |
| 3 | Transcribe + expand | Blog post / Newsletter essay (2000 words) |
| 7 | Pull top comments | "Response video" addressing community song requests |
| 14 | Compile series | "Best of [Era]" compilation video (90s hip-hop, Chicago hip-hop, etc.) |
| 30 | Refresh with new data | Updated version with new streaming numbers, new samples discovered |
| 90 | Evergreen boost | Re-post with new hook to new audience |

### 6B. Knowledge Graph (Cognee)
All content, performance data, and audience feedback feed into a knowledge graph:
- Artist → Songs covered → Performance per song
- Era → Cultural context → Audience engagement
- Sample → Sampled by → "Sample family tree" content opportunities
- Comment request → Song queued → Content pipeline

This graph powers predictive content recommendations:
- "If Common's 'I Used to Love H.E.R.' performed well, queue Black Star's 'Respiration' (same era, same conscious rap angle)"
- "Comment requests for 90s West Coast are spiking — shift next month's focus"

---

## Complete Repo-to-Function Mapping for I Love Hip Hop Media

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
| **Compliance** | Probo | Vault, Trivy |

---

## Example: End-to-End Run

**Input Outline**:
```yaml
content_type: "song_breakdown"
song:
  title: "I Used to Love H.E.R."
  artist: "Common"
  year: 1994
thesis: "Common personified hip-hop as a woman — the betrayal he felt mirrors every fan's tension with the genre's evolution"
```

**Pipeline Execution**:
1. **Curator-Agent** verifies sample clearance, confirms archival footage availability
2. **Research-Agent** finds: "I Used to Love H.E.R." peaked at #91 on Billboard Hot 100, sampled The Rotations, sparked East Coast/West Coast tension
3. **Copy-Agent** writes hook variants, discovers "They said this song killed conscious rap" pattern has 16% engagement in hip-hop niche
4. **Visual-Agent** generates: lyric cards in 90s graffiti font, sample family tree animation, Chicago 1994 archival footage composite
5. **Audio-Agent** clones Andrew's voice, layers instrumental bed at -18dB, adds vinyl transitions
6. **Editor-Agent** scores 8.7/10 on hip-hop save-engineering rubric (includes downloadable sample map)
7. **Deploy-Agent** publishes to 5 platforms with platform-native captions
8. **Feedback Loop**: 15% save rate, 7% comment rate (high song requests) → Mem0 queues 5 requested songs

---

## Anti-Patterns to Avoid for Hip-Hop Content

| Don't | Why | Instead |
|-------|-----|---------|
| Post same video to all platforms | Algorithm penalizes repurposed content | Render platform-native variants with different captions |
| Use generic hooks | "Check out this song" = death | Pattern-match from proven hip-hop content hooks |
| Skip the sample story | Samples are hip-hop's DNA | Always explain at least one sample origin |
| Forget the cultural context | Hip-hop is inseparable from its era | Anchor every song to what was happening in the world |
| Ignore the comment section | Hip-hop fans are passionate experts | Engage within 60 min, pin a discussion starter |
| Use corny visuals | Hip-hop audiences have high aesthetic standards | Match the era's visual language (grunge, bling, minimal) |
| Post without a downloadable | Saves drive the algorithm | Every post gets a playlist, sample map, or lyric PDF |

---

## Deployment Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                  I LOVE HIP HOP MEDIA                         │
│                    META MUSE ENGINE                          │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐    │
│  │Curator   │  │Muse      │  │Research  │  │Copy      │    │
│  │-Agent    │  │-Agent    │  │-Agent    │  │-Agent    │    │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘    │
│       └──────────────┴─────────────┴─────────────┘           │
│                    MetaGPT Orchestrator                      │
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

## Channel-Specific Standards

Every piece of content produced by META Muse must meet these **I Love Hip Hop Media** standards:

1. **Song first, always** — The song is the protagonist. The artist, era, and culture are supporting characters.
2. **Respect the craft** — No mockery of any era or style. Evolution is the story, not decline.
3. **Educate without lecturing** — Assume intelligence, add context generously. No hip-hop gatekeeping.
4. **Visual authenticity** — Match the era's aesthetic. 90s gets 90s treatment. Trap gets trap treatment.
5. **Community-driven** — Every post invites the audience to contribute THEIR song. The channel grows through shared curation.
6. **Accuracy above speed** — Sample credits, release dates, and chart positions are verified. Hip-hop fans will fact-check.

---

*This workflow is the engine. The heart is Andrew's love of the music. META Muse scales the craft without replacing the curator.*

**Last updated**: October 2026
**Next review**: After 10 published posts, when Mem0 has sufficient performance data to optimize
