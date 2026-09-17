# AEO Playbook

A living playbook for building judgment about AI search, from a designer & product builder who got tired of guessing why some pages get cited and others don't.

## what this is

Principles, checklists, and deep dives on Answer Engine Optimization (you'll also see it called GEO or AI SEO, same thing). It's a working reference for someone who makes content and product decisions and wants to know what AI systems actually reward.

I started this while building Open Visibility, an AEO product. The playbook is what I read before I direct strategy. The checklists are what I judge the output against.

I'm still learning this. It grows as I do.

**heads up on freshness:** research sources were last reviewed 2026-05-02. The principles are meant to outlast the data, but the specific stats, tools, and platform behaviors in the deep dives will drift. If something reads stale, it probably is.

## what's inside

**start here:**
- **[AEO Learnings & Playbook.md](<AEO Learnings & Playbook.md>)**: the hub. Principles, checklists, the learning path, and a running log of what I got wrong.

**deep dives:**
- **[How AI Search Actually Works.md](<How AI Search Actually Works.md>)**: query fan-out, grounding, RAG, how LLMs decide when to retrieve vs answer from memory
- **[The GEO Evidence Base.md](<The GEO Evidence Base.md>)**: Princeton study findings, proven optimization methods, what the data actually shows
- **[Platform Citation Mechanics.md](<Platform Citation Mechanics.md>)**: how ChatGPT, Google AI, and Perplexity each discover and cite content differently
- **[Content Structure for AI Extraction.md](<Content Structure for AI Extraction.md>)**: grounding chunks, semantic compression, density over length, citable formatting
- **[Authority and Off-Site Presence.md](<Authority and Off-Site Presence.md>)**: brand mentions, YouTube, Reddit, review platforms, earned vs owned strategy
- **[AEO Measurement and Tracking.md](<AEO Measurement and Tracking.md>)**: share of voice, selection rate, tracking pitfalls, tool landscape
- **[Entity Optimization for AI.md](<Entity Optimization for AI.md>)**: entity mapping, schema patterns (`sameAs`, `mainEntityOfPage`), knowledge graph connection, cross-platform consistency
- **[Technical AI Accessibility.md](<Technical AI Accessibility.md>)**: llms.txt, AI crawler taxonomy (training vs search bots), the JS rendering gap, timeout behavior, WAF pitfalls

## how it's built

These are my actual Obsidian notes, synced to GitHub. Cross-links are plain markdown, so they're clickable here and still work if you clone the repo into an Obsidian vault. Flat structure, no subfolders. The playbook is the root note that links out to everything else.

There's a sister repo for the engineering side: [engineering-playbook](https://github.com/aprianil/engineering-playbook).

Built with the help of Claude Code.
