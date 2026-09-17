# How AI Search Actually Works

> A deep dive into the mechanics behind AI search — how LLMs find, retrieve, and cite your content. Understanding this changes how you think about every piece of content you create.

---

## The Two Modes: Memory vs Retrieval

LLMs operate in two fundamentally different modes when answering a question:

| Mode | When It Activates | Example |
|------|-------------------|---------|
| **Parametric knowledge** (from training data) | The answer is stable, well-established, unlikely to change | "What is photosynthesis?" |
| **Grounded retrieval** (pulling from external sources) | The answer changes over time, is contested, or requires recent data | "Best project management tools in 2026" |

When the model has seen the same answer repeated thousands of times across its training corpus, it's confident. It just answers. No retrieval needed. Your content won't be found because the model never goes looking.

But when a topic is **volatile, emerging, nuanced, or time-sensitive**, the model recognizes it can't rely on training data alone. That's when retrieval activates — the model searches for external sources and cites them.

**That retrieval moment is the entire opportunity for AEO.**

---

## What Triggers Grounding

Three types of queries force AI to retrieve external sources:

### 1. Time-Sensitive Queries
Anything where the answer changes regularly. The LLM *cannot* answer from training data alone — it must pull from fresh sources.

Examples: "Average SaaS churn rate 2026," "Current inflation rate," "Latest guidelines on remote work policies"

### 2. Contested or Nuanced Topics
Topics where experts disagree or multiple valid perspectives exist. The model sees conflicting signals in its training data, so it seeks external sources to ground a balanced answer.

Examples: "Is cold plunging actually beneficial?" "Should startups prioritize growth or profitability?"

### 3. Emerging or Niche Topics
Subjects with limited training data coverage. The model has low confidence in its parametric knowledge, so it *must* retrieve and cite.

Examples: "GEO optimization strategies," "AI voice cloning ethics in marketing," "Regenerative agriculture ROI for small farms"

### Platform Exception: Gemini Grounds Everything
The three triggers above apply to ChatGPT and Perplexity, which selectively ground based on confidence. **Gemini operates differently.** DEJAN's research (2025) discovered that Gemini follows a verification-first principle -- it grounds ALL factual claims, even "common knowledge." Its internal directive is: "Only use tools to verify and update even known information."

Every Gemini grounding call includes date parameters and geographic context, so freshness and location are structurally baked into every retrieval. This means Gemini presents more citation opportunities than other platforms -- your content has a chance to be retrieved even for stable knowledge queries on Google's AI surfaces.

**For Open Visibility's Prompt Discovery:** Grounding likelihood should be platform-specific. A "low grounding" prompt on ChatGPT (answered from memory) might be "high grounding" on Gemini (still triggers web search). This affects which prompts are worth tracking per platform.

**The strategic implication:** Instead of competing for queries where established sources already own the parametric answer, target queries where the model is forced to go looking. On Gemini, that's nearly every query. On ChatGPT and Perplexity, focus on time-sensitive, contested, and emerging topics.

| Low-Grounding Query | High-Grounding Query |
|---------------------|----------------------|
| "What is content marketing?" | "Content marketing conversion benchmarks by industry 2026" |
| "What is a CRM?" | "CRM feature comparison for solopreneurs Q1 2026" |
| "What is sleep hygiene?" | "New research on sleep protocols for shift workers" |

The left column — the LLM already knows the answer. The right column — the LLM *needs* a source. If your content is well-structured, fresh, and authoritative, you become that source.

---

## Google's 4-Stage Grounding Pipeline

DEJAN's research (Critchlow & Petrovic, 2025) maps the specific stages Google uses to go from user question to grounded answer:

1. **Query fan-out** -- the user's prompt is decomposed into multiple component search queries
2. **Fast search** -- Google searches a lightweight, cached version of the web (not the live web) for speed
3. **Filtering** -- a classifier narrows thousands of candidate results to a manageable set
4. **Chunk selection** -- the model extracts specific text passages ("grounding snippets") from candidate pages to construct the answer

A key behavioral difference between platforms: **Google tends to ground a single fact with multiple sources, while OpenAI often maps one fact to one URL.** This means Google AI content needs to be the best version of a common claim (to be selected from multiple candidates), while ChatGPT content benefits from being the only authoritative source for a specific fact.

### The Intermediate Summarization Layer

DEJAN's "Hacking Gemini" research (Petrovic, 2025) revealed that Google adds a processing layer between your page and the LLM. Each search result fed to Gemini includes an `additional_info` field -- **Google's own pre-summarized impression of your brand**, not a direct quote from your site.

For example, a cycling jersey company's `additional_info` said: "Mentions designing cycling jerseys online, high quality, fast delivery, and no minimum order." That's not copy from their website -- it's what Google reduced their brand to.

**Why this matters:** Your AI visibility depends not just on what you publish, but on what Google's pipeline **decides to compress your content into**. If that summary misses your key differentiators or emphasizes the wrong things, the AI answer inherits that bias.

**For Open Visibility's Brand Intelligence:** This creates a diagnostic opportunity -- surface what Google's compressed summary of a brand looks like vs. what the brand thinks it represents. That gap is actionable.

### Fan-Out Can Hallucinate

One failure mode: the query decomposition step itself can produce hallucinated sub-queries. The model may generate sub-queries about things the user never asked about, retrieving irrelevant content that dilutes the answer quality. This means optimizing for likely fan-out queries matters, but you can't predict every sub-query the model might generate.

---

## ChatGPT's Ranking Mechanism: Reciprocal Rank Fusion (k=60)

Metehan Yesilyurt (2025) discovered ChatGPT's actual ranking mechanism in its client-side code: **Reciprocal Rank Fusion (RRF)** with a k parameter of approximately 60.

**How it works:** ChatGPT doesn't run a single search. It fires **8-16 parallel sub-queries** with semantic variations (e.g., "coffee makers," "best coffee machines," "coffee maker reviews," "coffee brewing devices"). Each sub-query returns its own ranked list. RRF merges all those lists using:

`RRF score = sum of 1/(k + rank)` across all sub-queries where a page appears.

With k=60, the curve is flat -- the difference between rank #1 and #10 is tiny (0.0164 vs 0.0143). **What matters is appearing in more lists, not ranking higher in any single one.**

**The math that changes the game:**
- 1 keyword at rank #1 = 0.0164 total RRF score
- 10 related keywords at rank #5 each = 0.154 total score (**10x higher**)
- A site with 30 pages ranking #3-10 across 50 queries = **46x higher** than a single #1

**The citation threshold:** Pages need approximately 0.020+ RRF score to make it into ChatGPT's citation pool. That requires at minimum 2 appearances in top-40, or 3 appearances in top-90.

**What this means for content strategy:** Stop optimizing for position #1 on a single keyword. Build **topical coverage breadth** -- comprehensive topic clusters that rank reasonably well across many query variations. This is why Ethan Smith (Graphite) defines AEO topics as clusters of questions, not individual keywords.

**For Open Visibility's Gap Analyzer:** The diagnostic should evaluate topical coverage breadth, not single-query ranking. A brand ranking #4-8 across 30 sub-queries is performing far better than one ranking #1 for a single keyword. The Action Recommender should push toward filling coverage gaps across the topic cluster rather than obsessing over individual query positions.

---

## Query Fan-Out: How AI Decomposes Questions

When a user asks a complex question, the AI doesn't search for it as a single query. It breaks it into multiple sub-queries -- Google calls this "query fan-out."

**Example:** A user asks "What happens if I swap regular flour for wholemeal flour in a lemon drizzle?"

The AI generates fan-out queries like:
- "best flour for lemon drizzle cake"
- "how does wholemeal flour affect cake density"
- "baking with wholemeal flour tips"

Each sub-query retrieves its own sources. The AI then synthesizes all of them into a single response.

**What this means for content strategy:** You're not optimizing for one query. You're optimizing for a *cluster* of related sub-queries that AI will generate from a single user prompt. Comprehensive topic coverage from multiple angles increases the chances that your content appears across the fan-out set.

This is why Ethan Smith (Graphite) defines AEO topics as **clusters of questions** rather than individual keywords. A single page should cover the head question and the long-tail variations that AI will decompose it into.

---

## RAG: The Architecture Behind AI Search

Most AI search systems use a pattern called **Retrieval-Augmented Generation (RAG)**:

1. **User asks a question**
2. **Retrieval step:** The system searches for relevant content (using its own index, Bing, Google, or a proprietary crawl)
3. **Context assembly:** Retrieved content is combined into a context window — the "grounding material" the model will use
4. **Generation step:** The LLM generates its answer using *only* the retrieved context (not its training data)
5. **Citation step:** The model attributes claims to specific sources from the context

The key insight: the LLM's answer is constrained by what was retrieved. If your content wasn't retrieved in step 2, it cannot appear in the answer — no matter how good it is.

This means there are **two gates** your content must pass through:
1. **The retrieval gate:** Your content must be discoverable and deemed relevant enough to be retrieved
2. **The selection gate:** Once retrieved, your content must be chosen over competing sources for citation

Gate 1 is about discoverability (indexation, authority, relevance). Gate 2 is about content quality (structure, evidence, extractability). Both matter.

---

## The Grounding Budget: A Fixed Pie

Dan Petrovic at DEJAN discovered through empirical testing that Google allocates a **fixed grounding budget of roughly 2,000 words per query** to ground its Gemini AI responses. This budget is distributed across retrieved sources based on relevance ranking.

Key findings from analyzing 7,060 queries:

- **Average snippet size:** 15.5 words per extracted chunk
- **Median per-source allocation:** 377 words (~2,427 characters)
- **77% of pages** receive between 200-600 words of selection
- **Position determines share:** #1 ranked source gets ~531 words (28% of budget), #5 gets ~266 words (13%)

**The critical finding about length:** Pages under 1,000 words get 61% of their content selected for grounding. Pages over 3,000 words get only 13%. Additional content beyond roughly 540 words provides minimal incremental grounding value.

**You're competing for share of a fixed pie — not expanding the pie.** This is why density beats length. A focused 800-word page with high relevance density outperforms a padded 4,000-word page where the key insights are buried.

---

## How Each Platform Retrieves

Each AI platform has a different retrieval pipeline:

| Platform | Index Source | Retrieval Behavior |
|----------|-------------|-------------------|
| **ChatGPT** | Bing | Uses Bing's index; favors authoritative knowledge bases; averages 7.9 citations per response |
| **Google AI Overviews** | Google Search | Pulls heavily from top-ranking SERP results; 76% of cited URLs also rank in the top 10 organically |
| **Google AI Mode** | Google Search (broader) | Wider source pool than AI Overviews; only 53% of cited domains match top 10 organic results |
| **Perplexity** | Proprietary index + web crawl | Source-heavy; averages 21.9 citations per response; most freshness-sensitive |

**Critical insight:** Only 13.7% of citations overlap between Google AI Overviews and Google AI Mode — even within the same company, two AI features cite different sources. And only 11% of domains get cited by both ChatGPT and Perplexity. These are genuinely separate ecosystems.

---

## Recency Bias Is Deliberate, Not Emergent

Metehan Yesilyurt (2025) found explicit freshness scoring parameters in ChatGPT's production code:

- `use_freshness_scoring_profile: true` -- freshness is an active, deliberate ranking signal
- `reranker_model: "ret-rr-skysight-v3"` -- the post-retrieval reranker that applies the bias

Waseda University researchers (Fang et al., 2025) confirmed this across 7 AI models. The numbers are striking:

- **Up to 25% of relevance decisions flip based solely on dates**, not content quality
- Top-40 positions systematically favor newer content by 0.8-4.8 years
- Ranks 61-100 systematically bury older content by 0.5-2.0 years
- Ranks 41-60 are a neutral pivot point

This creates a "seesaw effect" -- new content gets lifted at the top while older content gets suppressed at the bottom. Critically, query intent detection fails to adjust for temporal appropriateness: a historical query gets the same freshness bias as a breaking news query.

**The practical implication:** Content freshness is now a ranking signal comparable in strength to content quality itself. The 3-month recency cliff (LLMrefs data) and the 30-day peak citation window (Perplexity/Google AI data) are expressions of this deliberate design choice.

**For Open Visibility's Action Recommender:** Content refresh recommendations should be treated as high-confidence, high-impact actions -- not optional housekeeping. Flag pages approaching 90 days since last update as priority refreshes. For competitive queries, the freshest credible content has a structural advantage.

---

## Indexation Does Not Guarantee AI Visibility -- But It Is Required

A critical finding from DEJAN (2025): Google's search index and AI Mode operate from **separate content stores**. A page can be indexed and ranking in traditional Google Search while being completely invisible to AI Mode.

In DEJAN's test, a page that was indexed in Google Search and recognized by Gemini App (which has direct search index access) was still inaccessible to AI Mode. AI Mode appears to pull from a proprietary content store that lags behind or diverges from the live search index.

Practitioner corroboration (Derek Iwasiuk): redirected pages that were no longer indexed were still being cited by AI systems -- with hallucinated content layered on top.

**What this means:** Traditional indexation is a necessary but insufficient condition for AI visibility. There's a separate content pipeline for AI systems that doesn't mirror the search index in real time.

Metehan Yesilyurt's experiment (2025) tested this from the other direction: launching a brand new site without Google or Bing indexation. For the first 10 days, no AI system cited it. ChatGPT citations only appeared after Google indexed the pages -- and the citation metadata matched Google's index, not Bing's. OpenAI's own crawler never showed up. This suggests **ChatGPT's search grounding pulls primarily from Google's index** (or a Google-derived index), contradicting the common assumption that it relies on Bing.

**The two-sided finding:** Being indexed is required but not sufficient. You need traditional indexation as the gateway, but the AI's separate content store may lag behind or diverge from the live index.

**For Open Visibility's Gap Analyzer:** The retrieval gate diagnostic should go beyond "is this page indexed?" A page could pass the indexation check but still fail AI retrieval because it hasn't made it into the AI-specific content store. Checking actual AI responses (does the page appear when you query the AI directly?) is a more reliable signal than indexation status alone.

---

## The Practical Takeaway

Understanding these mechanics changes what you optimize for:

1. **Target high-grounding queries** -- time-sensitive, contested, emerging topics where AI *must* retrieve (on Gemini, that's nearly every query)
2. **Cover topic clusters, not single keywords** -- optimize for the fan-out, not just the head query
3. **Pass both gates** -- be discoverable (retrieval gate) *and* well-structured (selection gate)
4. **Density over length** -- front-load your best insights. Only 32% of content survives Google's pre-filter, and shorter pages have dramatically higher survival rates
5. **Platform-specific indexation** -- verify you're indexed where each platform looks (Bing for ChatGPT, Google for AI Overviews), but know that indexation alone doesn't guarantee AI visibility
6. **Freshness matters** -- timestamps and updated data signal to retrieval systems that your content is current

---

**Sources:**
- DEJAN, "How Big Are Google's Grounding Chunks?" — 7,060 queries analyzed
- DEJAN, "How Google Grounds Gemini" — grounding mechanics research, verification-first principle
- DEJAN, "Hacking Gemini" — revealed the `additional_info` field and intermediate summarization layer
- DEJAN, "AI SEO Deep Dive" (Critchlow & Petrovic) — 4-stage pipeline, fan-out hallucination, platform attribution differences
- DEJAN, "AI Mode and Page Indexing" — separate content stores, indexation ≠ AI visibility
- Metehan Yesilyurt, "ChatGPT Is Using Reciprocal Rank Fusion (RRF)" — RRF k=60, multi-query fusion mechanics
- Metehan Yesilyurt, "The RRF Top-n Playbook" — citation threshold (0.020+), sub-query cluster strategy
- Metehan Yesilyurt, "Recency Bias in AI Search" — freshness scoring code, Waseda University research, seesaw effect
- Metehan Yesilyurt, "AI Citation Test Without Google/Bing" — ChatGPT citations track Google's index
- Fang et al. (Waseda University, 2025), "Recency Bias in LLM-Based Reranking" — 25% decision reversals from dates alone
- Google Search Central, "Succeeding in AI Search" — official fan-out documentation
- Graphite, "AEO Is The New SEO" — topic cluster framework
- Profound, "AI Platform Citation Patterns" — 680M citations across platforms
- Google Research, AGREE framework — self-grounding LLM architecture
