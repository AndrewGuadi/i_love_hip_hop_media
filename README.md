# I Love Hip Hop Media

**Can you love it and let it change?**

A song-first hip-hop channel born from Andrew's love of the music. His perspective shapes the work; being on camera is optional. Every post gives people a particular song and a reason to hear it differently.

![Post 001: Can you love it and let it change? Common — I Used to Love H.E.R.](posts/001-common-i-used-to-love-her/cover-master.png)

## Start here, Muse

Read [AGENTS.md](AGENTS.md), then [the Muse handoff](docs/MUSE_HANDOFF.md). The approved cover above is the original master. Preserve it and build variants separately.

| Material | Location |
| --- | --- |
| Post 001: master, caption, alt text, original prompt, credits | [Post package](posts/001-common-i-used-to-love-her/) |
| Channel purpose and creative standards | [Editorial brief](docs/EDITORIAL_BRIEF.md) |
| Verified tools, free limits, and recommended workflow | [Tools and free workflow](docs/TOOLS_AND_FREE_WORKFLOW.md) |
| Distribution, community work, and proposed launch cadence | [Outreach playbook](docs/OUTREACH_PLAYBOOK.md) |
| All 50 AI critiques and synthesis | [Markdown](docs/REVIEWS_50.md) · [PDF](docs/I_Love_Hip_Hop_Media_50_Reviews.pdf) · [Individual reports](docs/reviews/) |
| Historical starting point | [Hip-hop origins](docs/HIP_HOP_ORIGINS.md) |
| Provenance and current completion status | [Project state](docs/PROJECT_STATE.md) |

## Work locally

```bash
git clone https://github.com/AndrewGuadi/i_love_hip_hop_media.git
cd i_love_hip_hop_media
python3 scripts/validate_content.py
python3 scripts/package_post.py posts/001-common-i-used-to-love-her
```

The two commands use Python's standard library, make no network calls, and incur no API charges. The package command creates a ZIP in `build/`. It does not publish a social post. See [scripts](scripts/README.md) for optional PDF rebuilding.

## Current state

The cover is approved. The caption and accessibility text are prepared. Fifty separate AI reviews are preserved as an editorial reset, not cultural consensus. The first social post is not published; music and narration are not embedded. This repository is the shared handoff, not evidence that Muse has opened it or connected social accounts.

Research checked **October 21, 2026**. Read current account limits before using a service. Repository visibility does not confer rights to referenced commercial music or artist identities. No broad reuse license is granted here.
