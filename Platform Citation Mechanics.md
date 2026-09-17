# Platform Citation Mechanics

> How ChatGPT, Google AI, and Perplexity each discover and cite content differently — and why the same content performs differently across them. Based on Profound's 680M citation analysis, Semrush's 80M clickstream data, and DEJAN's grounding research.

---

## The Core Reality: Separate Ecosystems

The most important finding from cross-platform research: **these are not variations of the same system.** They are fundamentally different ecosystems with different indexes, different retrieval logic, and different citation biases.

- Only **11% of domains** get cited by both ChatGPT and Perplexity
- Only **13.7% of citations** overlap between Google AI Overviews and Google AI Mode (even within Google)
- Only **12% overlap** between AI citations and Google's top 10 organic results (Ahrefs)

Optimizing for one platform does not automatically help on another.

---

## ChatGPT

### How It Retrieves
- **Index:** Uses Bing's index for web retrieval
- **Crawlers:** GPTBot (for training), OAI-SearchBot (for search features)
- **Citations per response:** Averages 7.9

### Citation Bias
ChatGPT favors **authoritative knowledge bases and established editorial sources:**
- Wikipedia accounts for 7.8% of all citations (~48% of top-10 cited sources)
- Leans heavily on encyclopedic, well-structured, high-authority content
- .com domains make up 80%+ of citations

### What Gets Cited
- Content with definite language (not vague or hedging)
- Pages with high entity density
- Balanced mix of facts and opinions
- Simple writing structures
- Content with question marks (signals direct answer orientation)
- Pages with expert quotes average 4.1 citations vs 2.4 without
- Pages rich in statistics (19+ data points) average 5.4 citations vs 2.8

### Under the Hood (Metehan Yesilyurt, 2025)
- **Ranking mechanism: Reciprocal Rank Fusion (RRF) with k=60.** ChatGPT fires 8-16 parallel sub-queries per user prompt and merges results. Consistency across many queries beats ranking #1 for one query by 46x (see [How AI Search Actually Works](<How AI Search Actually Works.md>) for the math)
- **Recency bias is deliberate:** `use_freshness_scoring_profile: true` in production code. Up to 25% of relevance decisions flip based on dates alone (Waseda University research)
- **Personal memory distorts results:** ChatGPT injects topics from a user's conversation history into new responses. Two users asking identical questions get different brand mentions. AEO tracking tools see personalized results unless using fresh/logged-out sessions
- **Citations track Google's index, not Bing's.** Despite common assumptions, Metehan's experiment showed ChatGPT citation metadata matched Google's indexed versions. Google indexation may matter more than Bing for ChatGPT visibility

### What to Know
- **Google indexation may be more critical than Bing indexation** for ChatGPT citations (based on emerging evidence). Verify both, but don't assume Bing is the sole gateway.
- **ChatGPT holds ~87.4% of AI referral traffic.** It's the biggest platform by far.
- ChatGPT users average 23-word prompts (vs 4 words on traditional search) and spend ~6 minutes per session.
- LLM-driven signups show significantly higher intent: Webflow saw 24% conversion rate from ChatGPT vs 4% from non-brand SEO (6x improvement).
- **75% of real ChatGPT prompts are task-oriented** (not informational). Median 11 words, average 42 (bimodal distribution). Content that helps people *do things* gets cited more than content that just *explains things* (Metehan, 1,827 real prompts analyzed).
- **Most ChatGPT answers don't trigger retrieval.** Web search is enabled on only **34.5% of queries** (Feb 2026), down from ~46% in late 2024 (Semrush, 17-month clickstream update Apr 2026). The remaining ~65% are answered from training data. This is why brand saliency / parametric memory measurement (T=0 probing) matters — most of ChatGPT is a memory game, not a retrieval game.
- **Power-user behavior is shifting.** Avg queries per session jumped **+50% in the final four months of the study** (1.2 → 1.75). Outbound referrals **+206% YoY**. Build for follow-up turns, not single-query lookups.
- **Concentration is brutal.** Top 10 domains take **>30% of all ChatGPT referrals**; >20% of all ChatGPT outbound traffic goes to Google itself. This is power-law distribution — being in the top 10 of your category is worth far more than being in the top 50.
- **Same prompt, different searches.** ChatGPT's query rewriting has **91% uniqueness** — the same prompt rarely fires the same internal sub-queries twice (Profound, 10K prompts × 14 days, Apr 2026). Move tracking cadence to weekly. "Best [category]" queries preserve 39-65% across runs and are the most stable AEO entry points.

---

## Google AI Overviews

### How It Retrieves
- **Index:** Google's own search index
- **Grounding:** Uses Gemini with a fixed ~2,000-word grounding budget per query
- **Trigger rate:** Appears on roughly 25% of searches (Conductor 2026 data)

### Citation Bias
Google AI Overviews favors **balanced diversity across source types:**
- Reddit: 2.2% of citations
- YouTube: 1.9%
- Quora: 1.5%
- LinkedIn: 1.3%
- No single source dominates the way Wikipedia dominates ChatGPT

### What Gets Cited
- **Top-10 correlation has dropped sharply:** 37.9% of AI Overview citations come from URLs ranking in Google's top 10 (Ahrefs, Mar 2026 update) -- down from ~76% in mid-2025. **31% of cited pages rank 11-100, and 31% don't rank in the top 100 at all.** AI Overviews are fanning out beyond the SERP; "rank top 10 to be cited" is no longer a reliable heuristic.
- **YouTube is now the #1 cited domain in AI Overviews** -- grew +34% in 6 months (Ahrefs).
- Content updated within the last 30 days receives 3.2x more citations than content older than 90 days
- Structured data matters — FAQPage schema improves citation likelihood by ~30%
- 44.2% of citations come from the first 30% of the page content
- **AIO presence is query-segmented, not flat:** present in ~95% of comparison queries vs ~5% of transactional queries (Seer, Apr 2026). If you're optimizing for transactional intent, AIO is barely a factor.

### Google AI Mode (Different from AI Overviews)
- **Broader source pool:** Only 53% of cited domains match the top 10 organic results (vs 76% for AI Overviews)
- 92% of responses include a sidebar with ~7 unique domains
- Much less overlap with AI Overviews than you'd expect — only 13.7% citation overlap between the two Google AI features

### What to Know
- AI Overview clicks are higher quality — users spend more time on sites after clicking from AI results (per Google's own data)
- Industries with highest AI Overview presence: Health Care (48.7%), Financials (25.7%), Utilities (25.4%)
- Google's official guidance (John Mueller): focus on unique, non-commodity, people-first content. AI just raises the bar for usefulness.
- **CTR is recovering, not collapsing.** AIO CTR rose from 1.3% (Dec 2025) to 2.4% (Feb 2026), +85% in two months (Seer, n=53 brands, 5.47M queries, 2.43B impressions). Earlier "AIO is killing clicks" data was a snapshot of a deeper trough than the steady state. Don't write off the channel based on Q4 2025 numbers.

---

## Perplexity

### How It Retrieves
- **Index:** Proprietary index + real-time web crawl
- **Citations per response:** Averages 21.9 (nearly 3x ChatGPT's average)
- **Transparency:** Ties every claim to a specific source in 78% of complex research questions (vs ChatGPT's 62%)

### Citation Bias
Perplexity heavily favors **community-driven and real-time content:**
- Reddit accounts for 6.6% of all citations (~47% of top-10 cited sources)
- Most freshness-sensitive platform: 82% citation rate for fresh content vs 37% for older content
- Source-heavy — gives the most citations per response of any platform

### What Gets Cited
- Recent, frequently updated content
- Community discussions with authentic participation
- Content with clear source attribution
- Niche authority content (shows strongest proximity to traditional rankings at 28% overlap with Google)

### Under the Hood (Metehan Yesilyurt, 2025)
Reverse-engineering of Perplexity's browser infrastructure revealed its ranking system:
- **L3 XGBoost reranker** at the core -- a trained ML model that reranks results post-retrieval, with a quality drop threshold below which results get removed entirely
- **Hardcoded trusted domain lists** by category: Amazon (e-commerce), GitHub/Stack Overflow (dev), Reddit (social), .edu (education), major travel sites
- **Topic multipliers** -- AI, technology, science, and business get explicit boosts; entertainment and sports are penalized
- **Early CTR window** -- new content is monitored for click-through rate immediately after publishing; early CTR performance determines whether it gets further distribution
- **Answer-first passages under 80 tokens** with clear entity disambiguation are preferred for citation
- **Memory boost** -- pages connected to a user's history/memory get boosted via `boost_page_with_memory`
- **Negative signals** -- user dislikes and no-click patterns actively suppress content

### What to Know
- Perplexity is the platform where freshness matters most. Content age is a stronger signal here than on any other platform.
- Reddit presence is disproportionately important for Perplexity visibility, reinforced by hardcoded domain trust.
- The high citation count (21.9 per response) means more opportunities to appear -- but also more competition for each citation slot.
- Launch timing matters: maximize distribution when content is first published to win the early CTR window.
- Keep content under 80 tokens per answer passage for optimal citation extraction.

---

## Platform-Specific Strategy Summary

| Factor | ChatGPT | Google AI Overviews / AI Mode | Perplexity |
|--------|---------|--------------------| ----------|
| **Index** | Bing | Google Search | Proprietary |
| **Top citation source** | Wikipedia / authority | AI Mode: LinkedIn #1 (~15%). AI Overviews: balanced (Reddit, YouTube, Quora, LinkedIn) | Reddit / community |
| **LinkedIn citation rate** | 14.3% of responses (ranked #5, up from #11) | 13.5% of responses (ranked #1 in AI Mode) | 5.3% of responses |
| **Freshness sensitivity** | Moderate | High (3.2x for content <30 days) | Highest (82% vs 37% for fresh vs old) |
| **Overlap with Google organic** | 8% | 76% (AI Overviews) / 53% (AI Mode) | 28% |
| **Avg citations per response** | 7.9 | Varies by query | 21.9 |
| **Critical indexation** | Bing | Google | Own crawl |
| **Highest-leverage tactic** | Authority + structured knowledge | Traditional SEO + freshness + schema + LinkedIn | Reddit engagement + freshness |

---

## The Cross-Platform Playbook

Given that these are separate ecosystems, the practical approach is:

1. **Verify indexation on each platform's source.** Bing for ChatGPT. Google for AI Overviews. Perplexity crawls independently but check their index too.

2. **Don't assume cross-platform transfer.** Getting cited on ChatGPT tells you nothing about Perplexity or Google AI. Track each separately.

3. **Match your off-site strategy to the platform.**
   - For ChatGPT visibility: build authority signals, ensure Wikipedia-quality content structure, LinkedIn presence (14.3% citation rate)
   - For Google AI Mode visibility: LinkedIn is #1 cited domain (~15%) — original LinkedIn articles are high-leverage here
   - For Google AI Overviews visibility: traditional SEO still matters most, supplement with schema and freshness
   - For Perplexity visibility: Reddit engagement is critical, freshness is non-negotiable

4. **Prioritize based on audience.** Where does your target audience actually search? Start there. Expand to other platforms once you've built a baseline.

5. **Track platform-specifically.** Same question, same run count, but across each platform separately. Share of voice on ChatGPT is independent from share of voice on Perplexity.

---

**Sources:**
- Profound, "AI Platform Citation Patterns" — 680M citations (Aug 2024 - Jun 2025)
- Profound, ["What AI Engines Actually Search For"](https://www.tryprofound.com/blog/what-ai-engines-actually-search-for) (Apr 2026) — ChatGPT 91% query uniqueness across 10K prompts × 14 days
- Semrush, ["ChatGPT Search Insights"](https://www.semrush.com/blog/chatgpt-search-insights/) — 17-month clickstream update Apr 2026; 34.5% search-trigger rate, +206% YoY referrals, queries/session jump
- Ahrefs, ["Why ChatGPT Cites One Page Over Another"](https://ahrefs.com/blog/why-chatgpt-cites-pages/) (Apr 2026) — 1.4M prompts; title-fanout cosine, URL slug effect, Reddit retrieval-vs-citation gap
- Ahrefs, ["AI Overview Top-10 Citation Update"](https://ahrefs.com/blog/ai-overview-citations-top-10/) (Mar 2026) — 76% → 37.9% top-10 share, YouTube as #1 AIO domain
- DEJAN, "How Big Are Google's Grounding Chunks?" — 7,060 queries
- Conductor, "AEO/GEO Benchmarks Report 2026" — 21.9M Google searches analyzed
- Ahrefs, "AI Overview Brand Correlation" — 75K brands, 15K prompts
- Seer / Search Engine Land, ["Google AI Overviews CTR Recovery"](https://searchengineland.com/google-ai-overviews-ctr-recovery-study-475566) (Apr 2026) — CTR 1.3% → 2.4% Dec 2025-Feb 2026
- Google Search Central, "Succeeding in AI Search" — official guidance
- Graphite, "How Webflow Turned AI Chats Into a Growth Channel" — Webflow case study
