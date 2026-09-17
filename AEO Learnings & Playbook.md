# AEO Learnings & Playbook

> A living document for building AEO judgment and strategy — from a designer and product builder learning to think about AI visibility like a practitioner, not a spectator.

---

> [!info]- Context for AI (Claude Code)
> This section is for you, the AI editing this file. Read this before making any changes.
>
> **What this file is:** A living playbook that shapes how I (Apri) think about Answer Engine Optimization before I direct strategy or create content. The flow is: I think (using this playbook) → I set context (research + frameworks) → I direct (content strategy) → I judge what's produced (using the checklists here). This playbook is my blueprint.
>
> **How to edit this file:**
>
> - Timeless over trendy. This is the #1 rule. Principles should last. Tools, platforms, and specific statistics are perishable — they belong in deep dive notes, not the playbook. The playbook holds the thinking, not the tools.
> - Follow the playbook's own principles. Simplicity first. Don't bloat it.
> - Don't add sections preemptively. Add them when there's a real learning to capture.
> - No rigid rules. Guidelines that flex beat hard rules that fight you.
> - Walk me through your thinking before making edits. I want to approve the reasoning first.
> - Check for internal conflicts before adding anything new. Don't let new advice contradict existing principles.
> - Tone: practical, direct, written for a designer/product builder. Not academic, not SEO-jargon-heavy.
> - No AI slop. Only include insights backed by original research, practitioners with real client data, or primary sources. If it reads like a repackaged listicle, it doesn't belong here.
> - **This playbook is the root, not the container.** When a topic needs a deep dive, create a new .md file in this vault (flat structure, no subfolders — all files live at the vault root) and link to it from here using `[[Note Name]]`. Keep the playbook as a clean hub that links out — don't let it grow into a textbook.

---

## Where I'm Starting From
- Background in design and product — I build products, ship features, work alongside engineers
- Building Open Visibility — applying AEO/GEO professionally
- I understand marketing and content strategy, but I'm building deeper judgment for how AI search actually works and how to optimize for it
- What I'm building now: the ability to evaluate content through an AI visibility lens, make strategic trade-offs, and know what "good" looks like in this new landscape

**The goal isn't to become an SEO technician. It's to develop the strategic eye — so I can build better products, create content that AI systems want to cite, and make informed decisions about AI visibility.**

**Deep dives (linked notes):**

| Note | What it covers |
|------|---------------|
| [[How AI Search Actually Works]] | Query fan-out, grounding, RAG, how LLMs decide when to retrieve vs answer from memory |
| [[The GEO Evidence Base]] | Princeton study findings, proven optimization methods, what the data actually shows |
| [[Platform Citation Mechanics]] | How ChatGPT, Google AI, Perplexity each discover and cite content differently |
| [[Content Structure for AI Extraction]] | Grounding chunks, semantic compression, density > length, citable formatting |
| [[Authority and Off-Site Presence]] | Brand mentions, YouTube, Reddit, review platforms, earned vs owned strategy |
| [[AEO Measurement and Tracking]] | Share of voice, selection rate, tracking pitfalls, tool landscape |
| [[Entity Optimization for AI]] | Entity mapping, schema patterns (`sameAs`, `mainEntityOfPage`), knowledge graph connection, cross-platform consistency |
| [[Technical AI Accessibility]] | llms.txt spec, AI crawler taxonomy (training vs search bots), JS rendering gap, timeout behavior, WAF pitfalls |

---

## Part 0: Before You Optimize
This is the foundation. Before touching any content, understand what you're actually optimizing for — because it's fundamentally different from traditional SEO.

### The Terminology
AEO (Answer Engine Optimization), GEO (Generative Engine Optimization), AI SEO — these are different labels for the same practice. The industry hasn't settled on one term. AEO is the most precise descriptor (Ethan Smith/Graphite coined it), GEO has academic credibility (Princeton paper), and "AI SEO" gets the most search volume. They all describe the same thing: optimizing your content and brand presence so AI systems cite you in their answers.

This playbook uses **AEO** as the default term.

### The Paradigm Shift
Traditional search returns a ranked list of links. You click through, visit websites, find your answer. SEO optimizes for position in that list.

AI search works differently. The user asks a question. The AI decomposes it into sub-queries (called "fan-out"), retrieves relevant sources from the web, synthesizes a single answer, and cites its sources inline. The user often gets their answer without ever clicking through to a website.

**The shift: from ranking in a link list → being cited inside AI answers.**

This changes what "visibility" means. You're not competing for a position on a page anymore. You're competing to be the source an AI system chooses to quote when constructing its answer.

### The Two Levers: On-Site and Off-Site
Ethan Smith (Graphite) breaks AEO down into two levers on [Lenny's Podcast](https://graphite.io/five-percent/the-ultimate-guide-to-aeo-on-lennys-podcast) — and everything you do falls into one of them:

**On-site** is what you control directly on your own product or brand:
- Content creation — articles, landing pages, documentation
- Content structure — front-loaded answers, self-contained chunks, schema markup
- Technical optimization — AI crawler access, page speed, server-side rendering
- Answering questions only you can answer — product-specific queries, original data

**Off-site** is what you do outside your own channels to build authority:
- Digital PR — getting mentioned in publications, news outlets, industry blogs
- YouTube — getting your brand mentioned in creator videos (titles, transcripts, descriptions)
- LinkedIn — publishing original articles and posts (LinkedIn is the #2 most-cited domain across AI platforms, and #1 for professional queries)
- Reddit and Quora — authentic participation in relevant discussions, disclosing affiliation
- Review platforms — encouraging customers to review you on G2, Trustpilot, Capterra
- Earned media — any third-party mention that AI systems can find and trust

The research backs this split. The Princeton GEO study shows on-site methods (statistics, citations, quotes) boost visibility by 27-41%. The Ahrefs/Profound data shows off-site signals (YouTube mentions, brand mentions, Reddit presence) correlate most strongly with AI citation across platforms.

**You need both.** On-site gets your content into the candidate pool. Off-site gets AI to trust you enough to select you. The Webflow case study (Graphite) showed that combining both levers — on-site content optimization *plus* Reddit engagement *plus* YouTube presence — drove a 2x increase in LLM signups. Neither lever alone would have achieved that.

See [[Authority and Off-Site Presence]] for the full deep dive on the off-site lever.

### Head Questions vs Tail Questions
Ethan Smith (Graphite) on [Lenny's Podcast](https://graphite.io/five-percent/the-ultimate-guide-to-aeo-on-lennys-podcast) distinguishes two types of questions you can target:

**Head questions** are broad, category-level queries with high volume:
- "What's the best CRM software?"
- "Top productivity tools for remote teams"
- "Best website builder for small business"

These are competitive. AI pulls from many sources — comparison articles, Reddit threads, YouTube reviews. Your strategy here is primarily **earned** (off-site): make sure your brand is mentioned across the sources AI already cites.

**Tail questions** are specific, often product-level queries:
- "Does Companio support voice upload?"
- "How does Webflow handle form validation?"
- "Can Notion automate recurring tasks?"

These are where your **owned** (on-site) content wins. Only you can answer product-specific questions authoritatively. These are also high-grounding queries — the AI can't answer from memory, so it *must* retrieve.

**Frontier questions** are a third category: questions triggered by new launches, competitor moves, or emerging trends where zero content exists on the web yet. Being first to answer a frontier question is a structural advantage — there's nothing to synthesize from, so the first credible source often becomes the default citation. Monitor product launches, regulatory changes, and competitor announcements in your space for these.

**The strategic implication:** You need all three. Head questions drive discovery (new audiences finding your brand). Tail questions drive conversion (people already evaluating you). Frontier questions drive authority (being the original source the AI learns from). Map your content strategy across all three.

### Prompt Discovery: Finding What People Actually Ask AI
ChatGPT doesn't share prompt data. AEO tools exist, but most track short prompts (~7 words) that represent the head of the distribution — while over 60% of real AI prompts are 10+ words. The average Google search is 3.5 words. AI prompts are a fundamentally different, much longer input. Most of the channel is long-tail, and almost no content competes for it.

This means **you can't rely on tools alone to find what people ask AI.** The best prompt discovery sources are places where people already ask long, specific questions:
- **Sales calls and call recordings** — prospects describe their problems in natural language, often mirroring how they'd prompt an AI
- **Support tickets** — existing customers ask specific questions that map directly to tail and frontier queries
- **Reddit threads and community forums** — real questions from real people, in prompt-like language
- **Quora and Stack Overflow** — same pattern, different communities

The insight: the long tail of AI prompts has almost no content competing for it. Teams that systematically mine their own customer conversations for prompt ideas have a structural advantage over teams relying solely on keyword tools built for traditional search.

### Co-Occurrence: Why Off-Site Mentions Actually Work
The mechanism behind off-site authority isn't just "brand awareness." It's **co-occurrence** — how often your brand name appears alongside a topic across the sources AI retrieves.

When an AI system searches for "best website builder," it retrieves multiple sources (articles, Reddit threads, YouTube transcripts). If your brand appears across many of those retrieved sources — mentioned by different people, in different contexts — the AI treats that as a strong signal that you belong in the answer.

This is why earned mentions matter more than any single piece of owned content for head questions. You're not trying to rank one page — you're trying to be mentioned across the *set of pages* the AI will retrieve.

Ethan Smith describes it as "citation as the new backlink" — in traditional SEO, links pointing to you boosted your rank. In AEO, mentions of you across citation sources boost your chance of being selected.

### Entity Clarity: AI Needs to Know What You Are
AI systems don't match keywords -- they map **entities** (brands, products, people, concepts) and the relationships between them. Google's Knowledge Graph, LLM knowledge bases, and RAG systems all work this way. When AI decides whether to cite you, it's asking "is this a well-defined, trusted entity I can confidently reference?" -- not "does this page have the right keywords?"

This matters at both gates. At the **retrieval gate**, AI uses entity graphs to decide which sources are relevant -- if your brand isn't a recognized entity linked to your category, you may not enter the candidate pool. At the **selection gate**, AI favors sources from entities it can verify across multiple trusted sources. A brand with consistent entity signals across its website, LinkedIn, Crunchbase, and G2 is safer to cite than one with fragmented information.

**What entity clarity looks like in practice:**
- Every important page maps to **one primary entity** -- the page title, H1, and schema markup all point to the same thing
- Schema uses `sameAs` to link your brand to authoritative external profiles (LinkedIn, Crunchbase, Wikidata), telling AI that these are all the same entity
- Brand name, description, and category are **consistent everywhere** -- your site, social profiles, review platforms, directories. Inconsistencies make AI choose silence over risking a wrong citation
- `mainEntityOfPage` in your schema declares what each page is about, not just what type of page it is

This connects directly to co-occurrence: when your brand entity appears consistently across multiple sources AI retrieves, that's entity co-occurrence with a clear identity attached. Without entity clarity, mentions are ambiguous. With it, every mention reinforces the same trusted identity.

See [[Entity Optimization for AI]] for the full deep dive on entity mapping, schema patterns, and cross-platform consistency.

### Don't Over-Index on the Top 10 Domains
The most-cited domain charts (Reddit, Wikipedia dominating a pie graph) are misleading. Reddit accounts for roughly 2.5% of all citations. Wikipedia is about 0.5%. The reason they look dominant is that charts only show the top 10 domains -- and 95% of cited domains are outside that top 10. The long tail of citation sources is enormous and varied.

**What this means:** Reddit matters and you should be there, but it's not "half of AEO." The domains cited for your specific prompts depend entirely on the topic. Check what's actually being cited for your target queries before assuming Reddit is the answer.

### Product Content: The Overlooked On-Site Lever
Help centers, integration pages, feature docs, and use-case pages are some of the highest-ROI content for AEO -- and most companies underinvest in them. The gap usually isn't quality, it's **coverage**.

Companies answer their top 10 FAQs but miss the "sometimes asked questions" -- the mid and long-tail queries that map directly to how people prompt AI. Examples:
- You have integration pages for your top 5 integrations but not your 35th
- You document your flagship features but not the niche use cases
- You answer the questions support gets daily but not the ones that come up monthly

This is where AI prompts actually live. Prompts are longer and more specific than search queries, so they disproportionately match tail content.

**The organizational bottleneck:** Help center content is usually owned by CS/support teams, not marketing. SEO and AEO strategy rarely reaches those pages. If you can bridge that gap -- getting product content teams to think about AI discoverability -- you unlock a content surface most competitors ignore.

### SEO Is Still the Foundation
AEO doesn't replace SEO -- it builds on it. The research is consistent on this: technical SEO, content quality, and domain authority are still the foundation that AI systems draw from. Google's AI Overviews pull heavily from top-ranking search results. ChatGPT's index source is debated -- the OpenAI-Microsoft partnership suggests Bing, but Metehan Yesilyurt's experiment found ChatGPT citation metadata matching Google's index, not Bing's. Verify both. Perplexity uses its own crawl but favors authoritative sources.

The prediction (Ethan Smith calls this the "Convergence Thesis"): LLMs and traditional search will converge into a single experience. Google is adding AI Overviews and AI Mode. ChatGPT is adding maps, shopping, clickable elements. They're meeting in the middle. Optimize for both — they reinforce each other.

### How AI Search Works (The Short Version)
1. User asks a question
2. AI breaks it into sub-queries ("fan-out") to explore different facets
3. AI retrieves relevant sources -- but only when it can't confidently answer from memory (exception: Gemini grounds everything, even stable knowledge)
4. Google adds an **intermediate summarization layer** -- before the LLM sees your content, Google's pipeline compresses it into a summary (`additional_info`). Your AI visibility depends not just on what you publish, but on what Google decides your brand represents
5. AI synthesizes a response from retrieved sources, extracting **text and basic HTML** -- it doesn't see your CSS, visual design, or raw schema markup
6. AI cites the sources it used

**The grounding trigger is critical:** On ChatGPT and Perplexity, AI only retrieves external sources when the query is time-sensitive, contested, or emerging. For well-established facts, the model answers from training data. **Gemini is the exception** -- DEJAN's research shows it grounds all factual claims, even common knowledge, making every query a citation opportunity on Google's AI surfaces.

**Target queries where the model is forced to go looking.** That's where your content has a chance to be cited. On Gemini, that's nearly every query.

See [[How AI Search Actually Works]] for the full deep dive.

### Filtering AEO Advice
Most AEO information online is wrong -- either from bad analysis or from incentives that distort the message. When evaluating a source, consider what persona is speaking:

- **SEO practitioners pivoting to AEO** -- most grounded. They have years of client data and say AEO is mostly an extension of SEO with some nuance. They're least likely to oversell disruption.
- **New AEO software companies** -- incentivized to maximize the disruption narrative. Fundraising requires a massive market and maximum disruption: "SEO is dead, everything is different, you need our tool." The story serves the pitch deck, not necessarily the truth.
- **New consultants without SEO backgrounds** -- incentivized to say experience doesn't matter. "It's all new, the baseline is zero, hire me" competes better against a 15-year SEO veteran than admitting the fundamentals haven't changed.

None of this means these groups are always wrong. But knowing the incentive structure helps you weigh their claims.

**Watch for the illusory truth effect:** hearing "search is declining" or "you need to convert everything to markdown" enough times makes it feel true -- even when the data says otherwise. The more uncertain you feel about this space, the more vulnerable you are to confident-sounding misinformation. When a claim feels obvious because you've heard it everywhere, that's exactly when you should check the source data.

---

## Part 1: The Mindset Shifts
These are the core principles. Each one is backed by specific research — not opinions, not hype.

**11 principles to internalize:**

1. **Optimize for citation, not clicks.** 93% of AI search sessions end without a click. Visibility now means being quoted inside the answer itself. The metric isn't rank position — it's whether you're in the response at all.

2. **Information gain beats keyword density.** Say something nobody else said. Keyword stuffing performs *worse* than doing nothing (-8% in the Princeton study). Meanwhile, original research gets 340% higher citation rates. The question isn't "did I include the right keywords?" — it's "did I add something new to the conversation?"

3. **Density beats length -- per page. Breadth wins across the cluster.** AI has a fixed grounding budget of roughly 2,000 words per query. An optimized 800-word page achieves better grounding than a padded 4,000-word page, and 44% of all citations come from the first 30% of your content. But ChatGPT uses RRF (k=60) to merge 8-16 sub-queries per prompt -- ranking consistently across many queries scores 46x higher than ranking #1 for one query. The winning strategy: a cluster of dense, focused pages covering the full sub-query space, not one bloated page trying to cover everything.

4. **Enrich with evidence, not claims.** The top 3 proven optimization methods from the Princeton GEO study are all about adding verifiable information: quotations (+41%), statistics (+31%), and source citations (+27%). Layer them together — the best combination (fluency + statistics) outperforms any single method by 5.5%.

5. **Human-quality content still wins.** Google cites 86% human-written content; ChatGPT and Perplexity cite 82% human-written (Graphite 11,994 URLs; independently confirmed by Semrush 42K posts/20K keywords, Nov 2025). Only 7% of top-ranking articles are AI-generated, and human content ranks statistically significantly higher (p < 1e-6). The human advantage is concentrated at positions 1–4 — the gap narrows at positions 5+, meaning pure-AI content can compete for mid-page rankings but rarely wins the top slot. AI articles surpassed human articles in raw volume in November 2024, but the growth plateaued because search engines aren't rewarding it. The sweet spot is AI-assisted, human-edited -- use AI to accelerate research and drafting, but the thinking and expertise must be human.

6. **Authority is earned off-site, not just on-page.** The Ahrefs 75K brand study is definitive: branded web mentions (0.664 correlation) are the #1 predictor of AI visibility -- 3x stronger than backlinks (0.218). YouTube mentions show the strongest single-platform correlation (~0.737). LinkedIn is the #2 most-cited domain overall and #1 for professional queries. Reddit and Quora mentions give roughly 4x higher citation likelihood. 61% of AI brand reputation signals come from editorial media (Hard Numbers). There's a brutal visibility cliff: brands in the bottom 50% of web mentions get essentially zero AI visibility, while the top quartile gets 10x more than the next quartile down. What AI trusts is what the web trusts -- and trust is measured in mentions, not links.

7. **Each platform plays by different rules.** Only 11% of domains get cited by both ChatGPT and Perplexity. ChatGPT leans on Wikipedia and authoritative knowledge bases. Perplexity heavily favors Reddit and community content. Google AI Overviews balance across social, professional, and editorial sources. These are separate ecosystems requiring separate strategies.

8. **Selection rate is the new CTR — but visibility has four levels, not three.** When AI retrieves multiple sources, it chooses which ones to cite, name, and recommend. Visibility splits into **retrieval** (page in the candidate set), **mention** (brand named), **citation** (page linked), and **recommendation** (positioned as the top pick). These don't move together. Engines split asymmetrically — Gemini mentions 83.7% of the time but cites only 21.4%; ChatGPT cites 87% but mentions 20.7% (Indig, Ghost Citation Problem). Reddit is retrieved heavily but cited only 1.93% on ChatGPT (Ahrefs, 1.4M prompts) — retrieval is not citation. Each level needs a different fix; diagnose first. Dan Petrovic (DEJAN) calls the citation-level optimization SRO.

9. **GEO levels the playing field.** The Princeton study found that lower-ranked sites benefit disproportionately from GEO optimization — a site ranked 5th in traditional search saw visibility increases of up to 115%, while top-ranked sites actually *lost* visibility when all sources optimized. Traditional SEO rewards domain authority and backlinks that favor incumbents. GEO evaluates content quality directly. If you're a smaller brand with genuinely better content, you can win.

10. **Freshness is a ranking signal comparable to content quality itself.** This isn't emergent behavior -- it's deliberate. ChatGPT's code has `use_freshness_scoring_profile: true` as an active configuration (Metehan Yesilyurt, 2025). Waseda University research across 7 AI models found up to 25% of relevance decisions flip based solely on dates, not content quality. Content updated within the last 30 days receives 3.2x more citations; a sharp 3-month recency cliff drops citations across all platforms (LLMrefs). Perplexity is the most freshness-sensitive (82% vs 37%). Treat content as a living product with regular refresh cycles, not a publish-and-forget artifact.

11. **Most AEO work is wasted.** 1 out of 20 pages drives roughly 85% of all traffic. The vast majority of content creation effort produces zero measurable impact. Test rigorously before scaling. Find the 5% that actually moves the needle — then invest heavily in making those pages exceptional.

**Essential resources:**
- [GEO: Generative Engine Optimization (Princeton, KDD 2024)](https://arxiv.org/abs/2311.09735) — the foundational academic paper. Read the results tables.
- [How GEO Rewrites the Rules of Search (a16z)](https://a16z.com/geo-over-seo/) — best strategic overview of the market shift.

> [!tip]- Further reading
> - [AEO Is The New SEO (Graphite)](https://graphite.io/five-percent/aeo-is-the-new-seo) — Ethan Smith's framework for the 5% Rule and owned vs earned strategy
> - [Selection Rate Optimization (DEJAN)](https://dejan.ai/sro/) — Dan Petrovic's deep dive on SRO as the new metric
> - [AI Platform Citation Patterns (Profound)](https://www.tryprofound.com/blog/ai-platform-citation-patterns) — 680M citations analyzed across platforms
> - [Succeeding in AI Search (Google)](https://developers.google.com/search/blog/2025/05/succeeding-in-ai-search) — Google's official guidance

---

## Part 2: Questions to Ask at Every Stage
These are the checklists that build judgment over time. Come back to these every time you create content or evaluate a strategy.

### Before Creating Content
```
- What question am I actually answering? For whom?
- Is this a head, tail, or frontier question? (Determines whether the strategy is earned, owned, or first-mover)
- Is this a high-grounding query? (Time-sensitive, contested, or emerging — or will the LLM answer from memory?)
- Where did this question come from? (AEO tool, sales call, support ticket, Reddit — the source affects how long-tail it really is)
- What's my information gain? Am I saying something nobody else said?
- What funnel stage? (TOFU/MOFU/BOFU — this determines structure, schema, and tone)
- Who's currently being cited for this topic? What are they missing?
- Is this worth investing in? (5% Rule — will this be one of the few pages that actually moves the needle?)
- Can I bring original data, expert insight, or a unique angle — or am I just rewriting what exists?
```

### While Creating
```
- Is my core answer in the first 40-60 words of each section?
- Am I enriching with stats, quotes, and citations — not just making claims?
- Is each section self-contained? (No "as mentioned above" — AI extracts chunks independently)
- Am I covering the fan-out queries — the subtopics AI will decompose this into?
- Would an AI system confidently quote this sentence? (The "quote-ready" test)
- Am I using specific entity names, not pronouns or vague references? (Semantic compression)
- Does this add information gain, or am I just restating what's already out there?
```

### Before Publishing
```
Technical
- Schema markup present and entity-aware? (Article, FAQ, Organization, Person — with sameAs, mainEntityOfPage — see [[Entity Optimization for AI]])
- AI search bots allowed in robots.txt? (OAI-SearchBot, ChatGPT-User, PerplexityBot, ClaudeBot drive citations. Training bots like GPTBot are a separate decision — see [[Technical AI Accessibility]])
- WAF/firewall rules checked? (Cloudflare/AWS bot protection can accidentally block AI crawlers)
- Both Bing AND Google indexation verified? (ChatGPT's index source is debated -- partnership suggests Bing, but experiments show citation metadata matching Google's index. Verify both. Google's AI Mode uses a separate content store that lags behind the search index)
- Page loads fast, renders server-side? (AI crawlers can't execute JS and timeout at 1-5 seconds — content must be in initial HTML)
- Content survival-ready? (Only 32% of page content survives Google's pre-filter. Filler, promos, boilerplate get stripped before the LLM sees anything — front-load answers and cut noise)
- llms.txt present at site root? (Emerging standard, low effort — see [[Technical AI Accessibility]])

Content
- Real author bio with credentials present?
- Publication date and "Last Updated" timestamp?
- Expert quotes with full attribution? (Name, credentials, organization)
- Statistics with sources and sample sizes?
- Each section extractable on its own without needing context from other sections?
```

### After Publishing
```
- Is this showing up in AI answers? (Check ChatGPT, Perplexity, Google AI Mode separately — they're different ecosystems)
- What's the share of voice? (Same question 10-20x across runs, calculate appearance rate)
- Am I reporting absolute numbers, not just percentages? (10 visits is 10 visits, even if it's "900% growth")
- Am I measuring the right prompts? (Most tools track short head prompts. Real AI usage skews 10+ words and long-tail — if your tracking only covers short queries, you're measuring the wrong slice of the channel)
- Am I accounting for mobile? (Most published AI data excludes mobile, which is the majority of AI usage — don't underestimate the channel based on desktop-only numbers)
- Am I testing logged in? (Almost all real users are logged in. Logged-out results are directionally accurate but citations and answers differ — tracking tools that use logged-out API calls aren't showing what users actually see)
- Do I have a control group to isolate my optimizations from natural platform growth?
- Did I collect 2-4 weeks of baseline data before intervening? (Without a baseline, you can't distinguish optimization impact from natural variance)
- Am I measuring in the right sequence? (Citations appearing in the source set → visibility/share of voice → position in the answer → referral traffic → conversions. Earlier signals move first; don't wait for traffic to validate)
- Am I asking "how did you hear about us?" post-conversion? (Self-reported attribution is biased but still signal — especially for a channel where click tracking is broken by design)
- What would I do differently? What did I learn that changes how I create next time?
```

---

## Part 3: What Good vs Bad Looks Like
Reference this when creating content or evaluating strategy. If something looks like the right column, stop and fix it.

### Content Structure & Extractability
| Good | Bad |
|------|-----|
| Core answer in first 40-60 words | Burying the answer after paragraphs of setup |
| Self-contained sections with explicit entity names | "As mentioned earlier..." / pronouns AI can't resolve when extracting |
| Stats with sources and sample sizes | "Studies show..." with no citation |
| Expert quotes with full attribution (name, credentials) | Generic assertions with no source |
| Direct topical headings | Keyword-stuffed or vague headings |
| Dense, focused pages (~800-1500 words) | 4,000-word "ultimate guides" padded with filler |

### Technical Implementation
| Good | Bad |
|------|-----|
| Entity-aware schema with `sameAs`, `mainEntityOfPage` | Generic schema types without entity connections |
| AI search bots allowed, training bots decision explicit | Blanket blocking or blanket allowing without understanding which bots do what |
| Fast page load, server-side rendered, key content in initial HTML | JS-heavy pages AI crawlers can't execute (they timeout at 1-5s) |
| Real author bios with credentials | Anonymous or fake author pages |
| Both Bing AND Google indexation verified | Only checking one search engine's index |
| llms.txt at site root with curated content map | No machine-readable content overview for AI systems |
| WAF/firewall rules audited for AI crawler access | Bot protection accidentally blocking AI crawlers |

### Measurement & Strategy
| Good | Bad |
|------|-----|
| Track across platforms separately (different ecosystems) | Checking one platform and assuming the rest |
| Statistical sampling (10-20x per query per platform) | Checking once and calling it your visibility |
| Control groups isolating optimization impact from platform growth | Crediting all AI traffic growth to your work |
| Absolute numbers + relative percentages + business impact | "900% increase!" (from 1 to 10 visits) |
| Monthly content refresh with fresh data and timestamps | Publish and forget |

---

## Part 4: The Trade-Off Muscle
This is the core skill. Not "always do X" — it's knowing when to switch gears.

| Situation | Lean Toward |
|-----------|-------------|
| New topic, no existing content | Depth. One exceptional page > five mediocre ones (5% Rule) |
| Existing content not getting cited | Refresh with fresh stats, quotes, citations. Don't rewrite from scratch |
| Limited team (1-2 people) | On-site content quality + one off-site channel (YouTube or Reddit) |
| Choosing between SEO and AEO work | Both. They reinforce each other. SEO is still the foundation |
| AI-generated vs human-written content | AI-assisted, human-edited. Pure AI content shows negative citation correlation |
| Tempted to game Reddit or Quora | Authentic participation. Disclose who you are. 5 thoughtful comments > 100 fake ones |
| Picking which platform to optimize for first | Where your audience actually searches. Then expand |
| Big content bet vs safe content | Test first. Most content drives no impact — validate before scaling |
| AEO traffic is tiny, is it worth it? | Yes — LLM traffic converts at 6x the rate of non-brand SEO (Webflow data: 24% vs 4%). Small volume, high quality. Invest now while competitors ignore it |
| Investing in AEO tools | Start cheap. Core features are commoditized. Premium pricing isn't justified yet |
| Choosing what prompts to target | Mine internal sources (sales calls, support tickets) for long-tail prompts. Tool-derived keyword lists skew short and competitive |
| New product launch or competitor move | Race to answer frontier questions — zero competing content means first credible source wins |
| AEO extraction advice conflicts with conversion-optimized page design | Don't gut a high-converting page for AI extractability. Front-load answers in new content. For existing pages that convert well, add a structured FAQ section or a companion page targeting the AI query. Optimize for both audiences, not one at the expense of the other |
| Technical AEO vs content/citation optimization | Technical fixes (crawlers, rendering, indexation) are binary prerequisites -- fix once, then move on. Ethan Smith (Graphite) says ongoing technical AEO work drives near-zero impact, mirroring the same trap from SEO. The real ongoing impact comes from content quality and citation optimization (selection gate). Exception: internal linking architecture, which compounds over time |
| Schema markup vs text quality | Schema helps at the retrieval gate (crawlers use it to classify and discover content). The LLM itself reads text, not raw schema. Invest in schema for discoverability, invest in text quality for citability. Don't assume adding schema will directly improve how the LLM presents your content |

---

## Part 5: The Practice Loop
Judgment isn't learned from reading — it's built through create, measure, learn, repeat.

| Practice | What It Builds |
|----------|---------------|
| Check your brand in AI answers weekly | Awareness — know where you stand before optimizing |
| Read one quality AEO source per week | Pattern recognition — the field moves fast, but filter for quality |
| Audit one page per week against the Part 2 checklists | Self-critique — catch gaps systematically |
| Log what you learn after each optimization | Articulation — forces the *why*, not just the *what* |
| Study what competitors get cited for | Strategic eye — find the gaps they're missing |
| Run one A/B test per month on content structure | Evidence — know what actually works for *your* context |

**People worth following:**
- Ethan Smith (Graphite) — practitioner with real client data, 5% framework, Lenny's Podcast appearances
- Dan Petrovic (DEJAN) — researcher, Selection Rate Optimization, grounding mechanics experiments
- Metehan Yesilyurt (AEO Vision) — reverse-engineers AI search internals (ChatGPT RRF, Perplexity ranking patterns, recency bias code, temperature zero method). The most technically rigorous AEO researcher alongside DEJAN
- Kevin Indig (Growth Memo) — strategic thinking, citation analysis across 21K+ data points
- John Mueller (Google Search Central) — primary source on Google's AI search guidance
- Rand Fishkin (SparkToro) — skeptical, data-driven voice on AI search measurement and audience research

**Blogs and newsletters:**
- [Graphite Five Percent](https://graphite.io/five-percent) — practitioner intelligence with real data
- [DEJAN Blog](https://dejan.ai/blog/) — original research and experiments
- [Growth Memo](https://www.growth-memo.com/) — Kevin Indig's strategic analysis
- [Search Engine Land AI Coverage](https://searchengineland.com/library/platforms/ai-platforms) — industry news

**Conferences:**
- [AEO Conf](https://aeoconf.com) — recordings available, practitioner-focused talks with real data (Graphite, AirOps, etc.)

---

## Part 6: Recommended Learning Path
A suggested progression — start wherever feels right, revisit as the field evolves:

### Phase 1: Build the Foundation
Understand what AEO is and why it matters.
- [ ] Read Part 0 and Part 1 of this playbook
- [ ] Read [[How AI Search Actually Works]]
- [ ] Read [[The GEO Evidence Base]]
- [ ] Read the Princeton GEO paper results section ([arXiv](https://arxiv.org/abs/2311.09735))

### Phase 2: Understand the Mechanics
Zoom into how each platform works and what content structure gets cited.
- [ ] Study [[Platform Citation Mechanics]]
- [ ] Study [[Content Structure for AI Extraction]]
- [ ] Study [[Authority and Off-Site Presence]]

### Phase 3: Build the Muscle (Ongoing)
Judgment becomes instinct through repetition.
- [ ] Apply Part 2 checklists to every piece of content you create
- [ ] Study [[AEO Measurement and Tracking]]
- [ ] Start the Practice Loop (Part 5)
- [ ] After every content piece or optimization, log what you learned below

---

## My Learnings Log

> [!info]- Logging guide (for AI and human)
> When something clicks or breaks while working on AEO, log it here. Tell Claude Code "log this learning" and it adds an entry.
>
> **Format:**
> ```
> ### YYYY-MM-DD — [tag] Sticky headline
> - Bullet points with enough context to stand on their own months later
> - Include the "why" or an example when the concept isn't self-explanatory
> - Not paragraphs, not over-simplified — enough depth to recall, concise enough to scan
> ```
>
> **Tags:** `[content]` `[technical]` `[measurement]` `[platform]` `[strategy]` `[grounding]` `[authority]` or whatever fits.
>
> **Rules:**
> - Newest entries go at the top
> - Each entry should make sense without needing the original conversation
> - Headlines should be memorable phrases that capture the core lesson
> - When this section gets long, split it into its own `[[AEO Learnings Log]]` file

### 2026-05-02 — [measurement] Ghost citations, retrieval ≠ citation, and the four-level visibility model
- Source: Indig, ["The Ghost Citation Problem"](https://www.growth-memo.com/p/the-ghost-citation-problem) — 3,981 domain appearances, 4 engines, 14 countries, 115 prompts. The cross-platform replication of his earlier ChatGPT-only attention study
- **62% of brand citations are "ghost"** — page linked but brand not named in the answer. Engine asymmetry: Gemini mentions 83.7% / cites 21.4%; ChatGPT cites 87% / mentions 20.7%. Same brand, opposite engine behavior. Single-engine tracking misses half the picture
- Comparative/evaluative content drives mentions at ~30x the rate of pure informational content. Sharpens the existing "comparative listicles = 32.5% of citations" data point — comparison format wins on the *mention* axis specifically
- Pairs with Ahrefs Apr 2026 (1.4M ChatGPT prompts): **Reddit is retrieved heavily but cited only 1.93%; 67.8% of all uncited URLs are Reddit.** Retrieval and citation are now confirmed as separate gates with measurable gaps between them. The playbook's "two gates" model (retrieval, selection) is now four levels: retrieval → mention → citation → recommendation
- Folded into Principle #8 in Part 1, full table in [[AEO Measurement and Tracking]]

### 2026-05-02 — [content] Title↔fanout cosine similarity is the strongest single citation predictor
- Source: Ahrefs, ["Why ChatGPT Cites One Page Over Another"](https://ahrefs.com/blog/why-chatgpt-cites-pages/) (Linehan, Apr 2026) — 1.4M ChatGPT prompts
- Title-to-fanout-query cosine similarity = **0.656 for cited pages vs 0.484 for uncited** — bigger lift than any authority or length signal in the study
- Natural-language URL slugs cited **89.78% vs 81.11% for opaque slugs** (e.g., `/p/2847`). Tactical: slug your URLs in human language
- 88.46% of citations come from the general search index. Pages cited by ChatGPT are real organic pages, not curated AI-specific sources. Reinforces the "Google indexation may matter more than Bing" finding from 2026-04-02
- Don't title for the head query alone — title for the *fan-out cluster*. A page titled "Best Website Builders" matches one query; "Best Website Builders for Small Business in 2026 — Webflow, Squarespace, Wix Compared" matches the actual sub-query set. Sharpens [[Content Structure for AI Extraction]]

### 2026-05-02 — [content] Shorter focused content wins on ChatGPT; structural-only edits drive +17% citation
- Source: Indig, ["Shorter, Focused Content Wins in ChatGPT"](https://www.growth-memo.com/p/shorter-focused-content-wins-in-chatgpt) (Apr 2026) — 815k query-page pairs, 16,851 queries, 353,799 pages, 10 industries
- **Pages covering 26-50% of a topic's subtopic space outperform exhaustive guides.** There's a ceiling on breadth — too much coverage hurts. New sweet spot: 500-2,000 words with 7-20 H2-H4 sections
- Direct headline-to-query match cited **41% vs 29% for loosely related** — bigger predictor than word count or domain authority
- Source: Yu et al., ["Structural Feature Engineering for GEO"](https://arxiv.org/abs/2603.29979) (Mar 2026) — structural-only edits (no copy changes) drove **+17.3% citation rate, +18.5% subjective quality** across 6 mainstream engines. Decomposes into macro/meso/micro structure
- Source: Tian et al., ["AgentGEO"](https://arxiv.org/abs/2603.09296) (Mar 2026) — diagnose-then-repair (edit only the specific failure mode) gets **>40% relative citation lift while editing only 5% of content**. Generic broad rewrites get 25% lift and actively hurt long-tail pages. Academic backing for the 5% Rule
- Synthesizes the heading-format conflict: it's not "questions vs declarative" — it's "literal match to the user query" (any format)

### 2026-05-02 — [platform] AI Overviews recovered, top-10 correlation collapsed, YouTube became #1 cited domain
- Source: Ahrefs, ["AI Overview Top-10 Citation Update"](https://ahrefs.com/blog/ai-overview-citations-top-10/) (Mar 2026)
- Top-10 citation rate dropped from ~76% (Jul 2025) to **37.9% (Mar 2026).** **31% of cited pages rank 11-100, 31% don't rank in the top 100.** "Rank top 10 to be cited" is no longer a reliable heuristic. AIO is fanning out far beyond the SERP
- YouTube grew **+34% in 6 months** and is now **AIO's #1 cited domain** (overtook Reddit/LinkedIn balance)
- Source: Seer, ["Google AI Overviews CTR Recovery"](https://searchengineland.com/google-ai-overviews-ctr-recovery-study-475566) (Apr 2026, n=53 brands, 5.47M queries, 2.43B impressions)
- AIO CTR rose from 1.3% (Dec 2025) to **2.4% (Feb 2026), +85% in two months.** The late-2025 "AIO is killing clicks" panic was a snapshot of the trough; channel recovered. AIO present in **~95% of comparison queries, ~5% of transactional**
- Updated Pitfall 7 in [[AEO Measurement and Tracking]] to reflect the corrected state

### 2026-05-02 — [platform] ChatGPT search trigger dropped to 34.5%; query uniqueness 91% across runs
- Source: Semrush, ["ChatGPT Search Insights"](https://www.semrush.com/blog/chatgpt-search-insights/) — 17-month update (Oct 2024 → Feb 2026), Apr 2026
- ChatGPT enables web search on only **34.5% of queries** (Feb 2026), down from ~46% (late 2024). **~65% of ChatGPT answers come from training data, not retrieval.** Brand saliency / parametric memory is more important than previously framed
- Outbound referrals **+206% YoY**. Avg queries/session jumped **+50% in the final four months** (1.2 → 1.75). Build for follow-up turns, not single-query lookups
- Top 10 domains take **>30% of all ChatGPT referrals**; >20% goes to Google itself. Power-law concentration — top of category matters far more than top-50
- Source: Profound, ["What AI Engines Actually Search For"](https://www.tryprofound.com/blog/what-ai-engines-actually-search-for) (Apr 2026) — 10K prompts × 14 days
- ChatGPT query uniqueness = **91%** (Perplexity 14%, Copilot 47%). Same prompt rarely fires the same internal sub-queries twice. **Move tracking cadence from monthly to weekly.** "Best [category]" queries preserve 39-65% across runs and are the most stable AEO entry points

### 2026-05-02 — [measurement] Sample-size protocol: n=10 → 5.6% mean visibility error; sequential sampling cuts 59%
- Source: Graphite/Druck, ["How To Track Entity Position in AI"](https://graphite.io/five-percent/how-to-track-entity-position-in-ai) — companion white paper to the April randomness paper
- At **n=10 runs per prompt per platform**: mean visibility error 5.6%, position error 1.06; **98.6% of prompts hit ≤10% error**. Replaces the playbook's vague "10-20 runs" with a defensible number
- **Sequential sampling cuts samples 59% on average** (135 → 55) for a 95% CI width ≤2.0. Run a pilot batch of 10, expand only for prompts where the CI is still wide (typically broad/head queries with 30-49% category consistency)
- **Visibility first, then position.** Visibility is more stable than rank order across runs. Track visibility as the primary metric and position as the secondary. Transactional prompts stabilize faster than subjective ones
- Updated [[AEO Measurement and Tracking]] core-metrics section with the sequential protocol

### 2026-05-02 — [authority] CC Rank as the upstream signal; Gemma 4 shows model-level brand-authority drift
- Source: Metehan Yesilyurt, ["The Hidden Authority Signal"](https://metehan.ai/blog/cc-rank/) (Jan 2026) — logistic regression over 607M Common Crawl domains, 2023-2025
- Domains scoring high on **Common Crawl Harmonic Centrality + PageRank** are dramatically overrepresented in LLM citations. This is upstream of platform-level trusted-domain lists — AI systems can only cite what's in the corpus, and Common Crawl is the dominant feed. Tool: `webgraph.metehan.ai`
- Source: DEJAN, ["Gemma 4 Brand Authority Map"](https://dejan.ai/blog/gemma-4-brand-authority-map/) (Apr 2026) — 14,044 runs comparing Gemma 4 (open-weight) vs Gemini (proprietary)
- **Self-reference bias is measurable.** Google ranks #4 in Gemini but **#17 in Gemma 4** (same vendor, 13-position drop). Of top 50 brands, only 39 overlap. Brand authority strategy must be model-segmented — Gemini ≠ Gemma ≠ GPT
- **Frequency ≠ salience.** Visa = highest raw mention rate (2.05x/run) but ranked #15 by salience due to late-list positioning. Position-weighted recall is the right metric, not mention count. Sharpens the visibility-percentage approach with a position-weighting refinement

### 2026-05-02 — [technical] llms.txt downgraded; agent-discovery files emerging as separate surface
- Source: AEO Engine measurement (2026) — **84 of 62,100 AI-bot requests over 90 days hit `/llms.txt` — 0.1%.** No frontier lab (OpenAI, Google, Anthropic, Meta, Mistral) has confirmed inference-time parsing
- Reframed [[Technical AI Accessibility]] llms.txt section: it's an **agent/IDE convenience file** (Cursor, Windsurf, coding agents), not a search-time inference signal. After 18 months of the spec existing, the trajectory hasn't materialized. Still cheap to add for docs sites; deprioritize for marketing sites
- Source: Addy Osmani, ["Agentic Engine Optimization"](https://searchengineland.com/agentic-engine-optimization-google-ai-director-474358) (Apr 2026)
- New emerging file conventions for AI agents: **`AGENTS.md`** (capabilities, constraints, tool calls), **`skill.md`** (reusable workflows), and clean `.md` versions of HTML pages. Mueller has pushed back on requiring separate-markdown for *search* indexing — these are agent-traffic optimization, not AEO
- AI-driven docs traffic grew **5x YoY in 2025** and is now **41% of pageviews on docs sites** (GitBook). For developer/agent audiences, agent-side optimization may compound faster than human-side AEO

### 2026-05-02 — [measurement] ChatGPT Ads now in ~20% of US responses
- Source: LLMrefs (Apr 2026) — 682K ChatGPT answers tracked since Feb 2026
- **~20% of US ChatGPT responses now contain ad placements.** Brands "winning" AI visibility may increasingly be paying for it; trackers that conflate organic citations with ad-adjacent appearances will mislead
- Tag ad-adjacent appearances separately. Watch for share-of-voice jumps that correlate with platform ad-product launches — that's a signal to dig in, not celebrate. Added as Pitfall 9 in [[AEO Measurement and Tracking]]

### 2026-04-19 — [content] Growth Memo attention study — paragraph-middle bias, H2-as-prompt, entity-density and reading-level benchmarks
- Source: Kevin Indig, Growth Memo, ["The Science of How AI Pays Attention"](https://www.growth-memo.com/p/the-science-of-how-ai-pays-attention) — ChatGPT citation analysis with randomized validation batches (P=0.0). ChatGPT-only, single study, no cross-platform validation
- **Within-paragraph attention is middle-weighted: 53% of citations from paragraph middles, only 24.5% from first sentences.** Refines (doesn't contradict) the "front-load answers" principle: section-level front-loading still wins (44% of citations come from the first 30% of a page — Principle 3), but *inside* a paragraph the model extracts wherever information gain is highest. Don't force the answer into sentence 1 of every paragraph at the cost of natural flow
- Definitive "X is Y" declarative language → 1.8x citation rate. Mechanism: direct subject-predicate relationships create stronger vector bridges in semantic space, enabling zero-shot query resolution. Quantifies the existing "quote-ready" test in Part 2
- Entity density benchmark: cited content ≈ 20.6% entity density vs 5–8% in baseline English. "Salesforce, HubSpot, Pipedrive" (30%) beats "good tools" (0%). Mechanism: entities lower perplexity and pack more bits per sentence. Concrete number to anchor the Entity Optimization deep dive
- **Question-format H2s → 2x citation rate (18% vs 8.9%); 78.4% of those citations come from the H2 + the paragraph immediately following.** The model treats interrogative headers as user prompts and prioritizes entity echoing (header mentions SEO → following paragraph should open with SEO). Strong practical pattern for FAQ-style and tail-question content
- Sentiment subjectivity sweet spot ≈ 0.47 (0 = pure fact, 1 = pure opinion). Cited content blends fact with analysis; pure Wikipedia dryness (0.1) and pure opinion (0.9) both lose. Pattern: "while X [fact], Y makes it superior for Z [analysis]"
- Reading-level target: Flesch-Kincaid 16 (college) wins; 19.1 (PhD/academic) loses. Long winding sentences with multisyllabic jargon reduce factual extractability
- Caveats: ChatGPT-only, single study, no comparison to Perplexity / Google AI / Gemini, no breakdown by content format (tables, lists, quotes). Treat as directional until cross-platform replication

### 2026-04-19 — [platform] Semrush ChatGPT clickstream — most prompts don't match keywords, search-trigger rate is dropping, search-language share is doubling
- Source: Semrush blog, ["ChatGPT Search Insights"](https://www.semrush.com/blog/chatgpt-search-insights/) — 1B+ lines of US clickstream from a 200M-user panel, Oct 2024 → Feb 2026 (desktop-skewed; mobile likely under-represented per Ethan Smith's 75-86% mobile-share point)
- 65–85% of ChatGPT prompts don't match Semrush's 27B-keyword database. Hard validation that GSC / keyword-tool imports miss most AI demand — Prompt Discovery must triangulate from sales calls, support tickets, Reddit, and synthetic generation. Reinforces the existing "Prompt Discovery" section in Part 0
- Prompt-length convergence: search-enabled prompts nearly doubled (4.7 → 8.7 words); non-search prompts roughly halved (24.9 → 13.5 words). Useful as a length-distribution prior when generating synthetic prompts. Refines the "AI queries average 23 words" stat (Graphite/Lenny's, 2026-04-02 entry) — that figure is the non-search tail, not the whole distribution
- ChatGPT enables web search on only 34.5% of queries (Feb 2026), down from ~46% (late 2024). Two product implications: (a) T=0 perception probing matters more than assumed — most ChatGPT answers come from training data, not retrieval; (b) scan-cost modeling and visibility math should account for non-grounded sessions where no citation is possible
- Citation concentration: top 10 domains ≈ 30% of all ChatGPT referrals; Google itself = 21.6%. Reinforces the 11% cross-platform overlap stat — ChatGPT's citation graph is power-law and platform-specific. Long tail expanded then contracted (71k → 260k → 170k unique cited domains over 16 months — no clear cause given)
- Share of prompts using "traditional search language" doubled (18.9% → 34.9%) Oct 2025 → Feb 2026. The conversational-vs-keyword gap is closing — prompt-discovery heuristics will need to evolve as ChatGPT shifts toward search-like inputs
- Gaps: article has no content-format data (listicles vs comparisons vs forums), no schema findings, no Perplexity/Google AI comparison, and minimal prescriptive AEO tactics

### 2026-04-16 — [measurement] AI visibility is probabilistic but measurable -- Graphite/Druck paper provides the statistical framework
- Graphite paper (Ethan Smith & Gregory Druck, "Demystifying Randomness in AI", April 2026) + related arxiv paper (2603.08924, "Quantifying Uncertainty in AI Visibility", March 2026) make the definitive case: AI visibility is a solvable statistics problem, not a mystery
- The mechanism: LLM core models deterministically produce probability distributions over next tokens. RAG retrieval is largely deterministic (search algorithms). The randomness comes from *sampling* those distributions (temperature, top-p). This is standard empirical sampling -- a well-established measurement method
- **Noise floor concept:** bootstrap confidence intervals reveal many apparent domain differences fall within measurement noise. A visibility shift from 40% to 35% may be statistically meaningless. Don't overreact to small changes without significance testing
- **Rank instability is structural:** citation rankings are unstable across samples throughout the full domain set, not just at the top. Strengthens Fishkin's finding with rigorous empirical evidence across Perplexity, SearchGPT, and Gemini
- **Adaptive sampling:** instead of flat "10-20 runs always," scale based on measured variance. Narrow categories (89-97% consistency) need fewer samples than broad ones (30-49%). Sequential sampling starts small, expands if variance is high
- **Citation distributions follow power-law patterns** with substantial variability -- a few domains dominate, most get near-zero citations. Matches the "visibility cliff" from the Ahrefs 75K brand study
- Credibility signal: Graphite explicitly notes they don't sell tracking tools, reducing incentive bias. They sell AEO services but "do not have a significant financial incentive to argue that AI visibility tracking is effective"
- Practical implication for OV: every visibility metric should ship with confidence intervals, significance indicators, and adaptive run counts. This is the differentiator against 60+ tools that report single-run point estimates as truth
- Sources: Graphite (Smith & Druck, April 2026), arxiv 2603.08924 (March 2026, 47 pages)

### 2026-04-02 — [technical] ChatGPT uses RRF (k=60), recency is deliberate, and personalization distorts everything
- ChatGPT uses Reciprocal Rank Fusion with k=60 to merge 8-16 parallel sub-queries per user prompt. The math: ranking #4-8 across 30 queries = 46x higher score than #1 for 1 query. Topical coverage breadth is the game, not single-keyword dominance (Metehan Yesilyurt, code evidence)
- Citation threshold: need 0.020+ RRF score. Minimum 2 appearances in top-40, or 3 in top-90. Build sub-query clusters, not isolated pages
- Recency bias is DELIBERATE: `use_freshness_scoring_profile: true` in ChatGPT production code. Up to 25% of relevance decisions flip on dates alone. "Seesaw effect": top-40 lifts newer content, ranks 61-100 bury older content (Waseda University, 7 models tested)
- ChatGPT's personal memory injects past conversation topics into new responses. Two users asking the same question get different brand mentions. All AEO measurement is distorted by personalization unless using fresh/logged-out sessions
- ChatGPT citations track Google's index, not Bing's. Citation metadata matched Google's indexed versions in experiment (Metehan). Google indexation may be more critical than Bing
- Perplexity revealed: XGBoost L3 reranker, hardcoded trusted domain lists (GitHub, Reddit, .edu, Amazon), topic multipliers (AI/tech boosted, entertainment penalized), early CTR window, answer-first passages under 80 tokens preferred (Metehan, browser architecture analysis)
- Temperature zero trick: at T=0, LLMs give deterministic "default truth" about brands via masking prompts. Practical brand saliency measurement for Brand Intelligence
- GSC → prompt discovery: 4-phase pipeline (collect GSC data → semantic embedding → convert to conversational prompts → validate against ChatGPT). Directly maps to Prompt Discovery with GSC integration
- 75% of 1,827 real ChatGPT prompts are task-oriented, not informational. Median 11 words, average 42 (bimodal). Commercial/local queries massively underserved
- SparkToro's prompt feature uses synthetic prompts inferred from behavioral data -- validates our triangulation approach for Prompt Discovery
- Google still 97% active search; ChatGPT 56% (SparkToro corrected methodology, old visitation-based data was inflated)
- Sources: Metehan Yesilyurt (6 articles), SparkToro (2 articles), Waseda University -- 9 sources reviewed

### 2026-04-02 — [measurement] AI brand recommendations are radically inconsistent -- rank position is meaningless, visibility percentage is the only valid metric
- SparkToro/Gumshoe study (2,961 queries, 600 volunteers): less than 1/100 chance of identical brand lists across two runs, less than 1/1,000 for identical ordering. AI recommendations are a statistical lottery, not a ranked list
- Real users with the same intent craft radically different prompts -- average semantic similarity is only 0.081. This means tracking fixed prompts captures only a narrow slice of real-world visibility. Prompt Discovery needs diverse variations, not just rephrases
- Narrow/specific sectors show 89-97% brand appearance consistency; broad categories show 30-49%. Maps to head/tail: tail queries produce more stable, actionable visibility data
- Fishkin explicitly invalidates rank position tracking ("full of baloney") and validates visibility percentage (share of voice via many runs). Our approach is validated
- Fishkin's strongest critique: "Anyone selling AI tracking should be ashamed" without transparent methodology. Open Visibility's open-source approach is a direct answer to this market gap
- Implication for product: run count may need to scale based on category breadth (10-20 for narrow, more for broad). Confidence intervals should reflect honest uncertainty
- Source: SparkToro & Gumshoe.ai (Rand Fishkin, Patrick O'Donnell), Nov-Dec 2025

### 2026-04-02 — [measurement] Tracking is commoditized, optimization is unsolved, and mentions ≠ citations ≠ recommendations
- Three distinct visibility signals: mention (brand named), citation (page linked), recommendation (brand positioned as top pick). Each requires a different fix -- off-site for mentions, retrieval for citations, content quality for recommendations
- Brand perception mapping via LLM association networks: B→E ("what does AI associate with your brand?") and E→B ("which brands does AI link to this topic?"). The grounded vs ungrounded gap is where AEO opportunities live -- it separates current web visibility from parametric memory
- AEO tool market: 60+ tools, $200M+ VC funding, but ALL do the same thing (tracking). Nobody has cracked the optimization/recommendation layer (Graphite: "this has not been figured out yet"). Validates Open Visibility's positioning
- Comparative listicles = 32.5% of all AI citations (SEOmator, 41M results). 95% of citation behavior unexplained by traffic metrics. Content format > domain authority for AI visibility
- AI Overviews reduce clicks by 34.5% on informational queries (Ahrefs, 300K keywords, difference-in-differences). But AIO coverage pulled back from 25% to 16% peak, and commercial queries grew from 8% to 18% of AIOs
- SRO full methodology: 3-phase (setup → token-level optimization → implementation). Phase 2 runs the model backward from desired outcome to find which tokens activate selection pathways. Transfers from open-weights models to production Gemini
- GA4 AI traffic: use regex filter `chatgpt|perplexity|claude|gemini|copilot` on Session Source/Medium. Caveat: significant AI traffic misattributed as "direct"
- WebMCP (DEJAN): emerging standard for sites to expose tools to AI agents via browser. Very early (Chrome flag), but directionally important for v3+ agentic commerce
- Sources: Graphite (2), DEJAN (3), Search Engine Land (2), Ahrefs, SEOmator, seoClarity, Purplex, Nick Lafferty, Superprompt -- 13 sources reviewed

### 2026-04-02 — [authority] Mentions > links, and there's a visibility cliff most brands are below
- Ahrefs 75K brand study: branded web mentions (0.664) are the #1 AI visibility factor, 3x stronger than backlinks (0.218). Top 3 factors are ALL off-site text signals. LLMs are language models -- they care about words, not links
- Visibility cliff: top 25% of web mentions = 169 median AI mentions. Bottom 50% = essentially zero. This is winner-takes-all, not a gradient. Brands below the threshold need mentions before content optimization matters
- 61% of AI brand reputation signals come from editorial media (Hard Numbers). Digital PR is the mechanism for building mentions at scale in exactly the sources AI trusts
- PR for AEO is fundamentally different from PR for SEO: it's about mentions in text (co-occurrence), not backlinks for domain authority
- Brands earning both citation AND mention are 40% more likely to resurface in subsequent LLM runs (AirOps). Sustained campaigns beat one-offs
- Herman Miller dominates "ergonomic chairs" in AI because they have 273 pages of "ergonomic" press mentions across Yahoo, CBS, CNET, etc. (Ahrefs). That's co-occurrence at scale
- Webflow template optimization formula: head question + branded term + target user + pain point on 1,500 pages = 485% QoQ. Long-tail targeting: SoV 38% → 100% within 3 weeks. Reddit workflow across 100 queries drove +135% views
- "Retrievability" as fourth stage after crawlability/indexability/rankability: Presence + Recognition + Accessibility (Search Engine Land)
- LLMs cite only 2-7 domains per response (Superlines) -- tighter competition than Google's 10 blue links
- Sources: Ahrefs (2 articles), Graphite, Search Engine Land (2), HOTH, Column Content, Conductor, Superlines -- 9 sources reviewed

### 2026-04-02 — [grounding] Only 32% of your content survives Google's filter, and indexation doesn't guarantee AI visibility
- Google's Vertex AI Search pipeline filters out ~68% of page content before the LLM ever sees it. What survives: core answers, specific details, pricing, actionable info. What gets cut: navigation, promos, boilerplate, tangential content (DEJAN, "AI Search Filter")
- Shorter pages have dramatically higher survival rates: 65% for 1,937 chars vs 22% for 8,164 chars. This strengthens the "density beats length" principle with concrete filtering data
- Being indexed in Google Search does NOT guarantee AI Mode visibility. Google's AI Mode pulls from a separate content store that lags behind the live search index. A page can rank #1 traditionally and be invisible to AI Mode (DEJAN, "AI Mode and Page Indexing")
- Three ways a ranked page fails at the selection gate: (1) wrong content extracted, (2) competitor sentences preferred, (3) thin grounding. DEJAN's tool at snippets.dejan.ai makes this visible
- AI content performance: Google cites 86% human / 14% AI content. ChatGPT/Perplexity cite 82% human / 18% AI. Only 7% of top-ranking articles are AI-generated (Graphite, Wilcoxon test p < 1e-6). AI articles surpassed human articles in volume Nov 2024 but plateaued because search engines aren't rewarding it
- AI content by category: highest AI penetration in Commerce (8%), Crypto, Tech, Productivity. Lowest in Food (< 1%), News, Travel
- Sources: DEJAN (4 articles), Graphite (3 articles) — 7 sources reviewed

### 2026-04-02 — [grounding] AI models see text, not your design -- and Google summarizes you before the LLM even reads
- AI models receive text, markdown, and basic HTML elements. They do NOT see CSS, visual layout, or schema markup in raw form. Your page design is invisible to the selection gate (DEJAN, Critchlow & Petrovic)
- Google adds an intermediate summarization layer (`additional_info` field) before the LLM processes your content. This is Google's own compressed impression of your brand -- not a quote from your site. If that summary misses your differentiators, the AI answer inherits that bias (DEJAN, "Hacking Gemini")
- Gemini grounds ALL factual claims, even common knowledge (verification-first principle). ChatGPT and Perplexity still selectively ground. This means Gemini presents citation opportunities for every query, not just time-sensitive/contested/emerging ones (DEJAN, "How Google Grounds Gemini")
- Google's 4-stage grounding pipeline: fan-out → fast search (cached web, not live) → filtering → chunk selection. Fan-out queries can themselves be hallucinated, retrieving irrelevant content
- Google grounds a single fact with multiple sources; OpenAI maps one fact to one URL. Different platform, different content strategy
- SRO simulation lets you test content selection in seconds instead of waiting weeks for crawl/index cycles. Generate synthetic snippets, run 100+ through a selection model, measure how often yours gets picked (DEJAN)
- Brand saliency via token probability: prompt "Would you recommend [Brand] for [Service]?" and measure the probability of "Yes." This measures parametric memory bias -- separate from real-time retrieval
- 3-month recency cliff for AI citations (LLMrefs). Google/AI citation overlap dropped from 70% to below 20% (Brandlight) -- rankings and AI citations are diverging fast
- Technical AEO drives near-zero ongoing impact (Ethan Smith/Graphite). Technical fixes are binary prerequisites, not ongoing work. Content and citation optimization is where compounding lives
- AI queries average 23 words vs 4 for Google. The long tail of AEO is 4x bigger than SEO (Graphite/Lenny's). LLM traffic converts at 24% vs 4% non-brand SEO at Webflow (6x)
- Sources: DEJAN (3 articles), Graphite (3 articles), LLMrefs, Semrush, Search Engine Land, Clearscope (10 sources reviewed)

### 2026-04-02 — [technical] Entity clarity and technical accessibility are missing AEO layers
- AI systems map entities (brands, products, people) and relationships, not keywords. Entity clarity affects both retrieval (are you in the candidate pool?) and selection (does AI trust you enough to cite?)
- Schema `sameAs` linking to LinkedIn, Crunchbase, Wikidata tells AI that your profiles across the web are the same entity. `mainEntityOfPage` declares what each page is about. These are more powerful than generic schema types alone
- Cross-platform consistency (same name, description, category everywhere) prevents AI from choosing silence over risking a wrong citation
- AI crawlers have two categories: search/retrieval bots (OAI-SearchBot, ChatGPT-User, PerplexityBot, ClaudeBot) that drive citations, and training bots (GPTBot, CCBot, Google-Extended) that influence model memory. Different purpose, can be controlled separately
- AI crawlers timeout at 1-5 seconds, hit 404 errors 34% of the time (vs 8% for Googlebot), and are 47x less efficient than Googlebot. Clean URLs and front-loaded content matter more than for traditional SEO
- llms.txt is an emerging standard (0.3% adoption, but adopted by Anthropic, Google A2A, Perplexity). Low effort to implement, uncertain but growing reward
- WAF/firewall rules accidentally blocking AI crawlers is a real retrieval failure most people don't check for
- Sources: Vercel AI crawler research, Search Engine Land, Search Engine Journal, Prerender.io, AnswerDotAI llms.txt spec, Mintlify, Rankability, ClickRank, Discovered Labs, SingleGrain (14 sources reviewed)

### 2026-04-02 — [strategy] Product content is the overlooked AEO surface area
- Help centers, integration pages, feature docs, use-case pages are high-ROI for AEO because they match the long-tail prompts AI users actually type
- The gap is coverage, not quality -- companies answer top FAQs but miss the "sometimes asked questions" that map to real AI prompts
- Organizational bottleneck: CS/support owns help center content, marketing/SEO strategy never reaches it
- Reddit is ~2.5% of all citations, not "half" -- the top-10 pie charts are misleading because 95% of cited domains are outside the top 10
- Source: Ethan Smith on Get Discovered podcast (Prerender.io), March 2026

### 2026-04-02 — [measurement] Split testing AEO requires logged-in data and baselines
- Logged-out API tracking (most tools) gives different results than logged-in (what users actually see) -- directionally accurate but not ground truth
- Need 2-4 weeks of baseline data before any intervention to understand natural variance
- Measurement sequence: citations in source set → visibility → position in answer → referral traffic → conversions
- "How did you hear about us?" post-conversion is a simple no-tech signal for a channel where click tracking is broken
- Source: Ethan Smith on Get Discovered podcast (Prerender.io), March 2026

### 2026-03-28 — [measurement] Most AI usage data is blind to mobile and the long tail
- Mobile accounts for 75-86% of AI usage and is excluded from most published data — real AI usage numbers are likely 4-5x what's commonly cited (Ethan Smith, AEO Conf keynote)
- Average Google search: 3.5 words. Over 60% of ChatGPT prompts: 10+ words. Most AEO tools track ~7-word prompts — measuring the head of a channel that's almost entirely tail
- The long tail of AI prompts has almost no content competing for it. This is the structural opportunity
- Source: Graphite + AirOps keynote at AEO Conf (aeoconf.com)

---

*Come back to this often. The questions won't change — but the ability to answer them gets sharper every time you create something and measure the result.*

---

*Research sources last reviewed: 2026-05-02. Principles are timeless. Resources, tools, and specific data points may age — revisit when something feels outdated.*
