# Authority and Off-Site Presence

> How AI systems decide which brands to trust — and why what happens off your website matters more than what's on it. Based on Ahrefs' 75K brand analysis, Profound's 680M citation study, Semrush's backlinks research, and the Webflow case study from Graphite.

---

## The Core Finding

On-page optimization gets you into the candidate pool. Off-site authority is what gets you selected.

The Ahrefs Brand Radar study is unambiguous: **YouTube mentions show the strongest correlation with AI visibility (~0.737)**, outperforming every other factor across ChatGPT, AI Mode, and AI Overviews. Brand mentions across the web — not just backlinks — are the #1 predictor of whether AI cites you.

AI systems trust what the web trusts. If authoritative third-party sources mention your brand, AI engines treat you as a credible source worth citing. If the only place your brand appears is your own website, AI has no external signal to validate you.

---

## The Authority Stack

Research points to a clear hierarchy of off-site signals that drive AI citation:

### The Correlation Hierarchy (Ahrefs, 75K Brands)

The Ahrefs study (2025) analyzed 75,000 brands and measured which factors correlate most with AI Overview visibility using Spearman rank correlation:

| Factor | Correlation | Category |
|---|---|---|
| **Branded web mentions** | **0.664** | Off-site text |
| **Branded anchors** | **0.527** | Off-site text |
| **Branded search volume** | **0.392** | Off-site text |
| Domain Rating | 0.326 | Domain |
| Referring domains | 0.295 | Domain |
| Backlinks | 0.218 | Domain |
| URL rating | 0.18 | Domain |

**The top 3 factors are all off-site, text-based signals.** Backlinks correlate 3x weaker than brand mentions. This makes sense: LLMs are language models trained on text. They derive brand understanding from words on pages -- the prevalence of your brand name, the co-occurrence with relevant topics, and the context in which those words appear.

### The Visibility Cliff: Winner-Takes-All

The same Ahrefs study revealed a brutal power law when breaking branded web mentions into quartiles:

| Web Mention Quartile | Median AI Overview Mentions |
|---|---|
| Bottom 25% | **0** |
| 25-50% | **3** |
| 50-75% | **14** |
| **Top 25%** | **169** |

The top quartile earns **10x more AI mentions** than the next quartile. If your brand is in the bottom 50% of web mentions for your category, you are essentially invisible to AI. Visibility breeds more visibility -- this is a threshold you need to cross, not a gradient you gradually climb.

**For Open Visibility's Gap Analyzer:** This informs how we frame off-site recommendations. For brands in the bottom 50%, the diagnosis isn't "optimize your content better" -- it's "you need more web mentions before content optimization matters." The Action Recommender should prioritize off-site presence building for brands below the visibility threshold.

### The Upstream Signal: Common Crawl Rank

Before AI systems decide whether to cite your domain, they're working from a corpus that's already been filtered. Metehan Yesilyurt's "CC Rank" research (Jan 2026, logistic regression over 607M Common Crawl domains 2023-2025) found that domains scoring high on **Common Crawl Harmonic Centrality + PageRank** are dramatically overrepresented in LLM citations across platforms. This is the upstream-of-everything authority signal: AI systems can only cite what's in their training/retrieval corpus, and Common Crawl is the dominant source.

The Perplexity hardcoded trusted-domain list (GitHub, Reddit, Stack Overflow, .edu, Amazon — see [Platform Citation Mechanics](<Platform Citation Mechanics.md>)) is a curated, model-specific version of this same idea. CC Rank is the measurable upstream version that applies broadly.

**Practical implication:** Domains with high CC Rank get a structural advantage that no on-page optimization can replicate. For new or low-CC-Rank brands, the path is the same as the Ahrefs visibility cliff — earn mentions on already-trusted domains rather than trying to lift your own domain into the trusted set. Free tool: `webgraph.metehan.ai`.

### 1. Brand Mentions Across the Web
More web mentions across different contexts (blog posts, anchor text, video transcripts, descriptions, titles) = more visibility across every AI platform studied.

This isn't just about backlinks. **Mentions without links still matter.** AI systems process text broadly -- if your brand name appears in a respected publication, a YouTube transcript, or a Reddit discussion, that registers even without a hyperlink. Ryan Law (Ahrefs): "Unlinked mentions have very little impact on SEO, but a much bigger impact on GEO."

### 2. YouTube Presence
YouTube is the most cited domain in Google AI Overviews. Mentions in video titles, transcripts, and descriptions show the strongest correlation with AI visibility of any single factor.

**You don't need to run a YouTube channel.** You need your brand *mentioned* in other people's videos:
- Identify YouTubers in your niche who produce tutorials, reviews, and comparisons
- Offer free product/access for honest reviews
- Pitch inclusion in "best of" roundup videos
- Provide expert quotes and data they can use in their content

The Webflow case study showed YouTube mentions contributed significantly to their 485% QoQ growth in LLM signups.

### 3. LinkedIn
LinkedIn is the **#2 most-cited domain overall** across ChatGPT, Google AI Mode, and Perplexity — and **#1 for professional queries** (Profound, 1.4M citations across 6 platforms). 11% of all AI responses reference a LinkedIn URL (Semrush, 325K prompts, Jan-Feb 2026).

The growth trajectory is steep: LinkedIn climbed from #11 to #5 on ChatGPT between November 2025 and February 2026 — the largest authority shift observed that year. On Google AI Mode, LinkedIn is the single most-cited domain at ~15% of responses.

**What gets cited:**
- **95% of cited LinkedIn content is original** — not reshares or reposts
- Articles of **500-2,000 words** are cited most frequently
- Content-type shift: posts and articles grew from 27% to 35% of LinkedIn citations, while profile page citations dropped from 34% to 15%
- This means AI is increasingly citing what you *write* on LinkedIn, not just that you *exist* on LinkedIn

**What to do:**
- Publish original, substantive articles and posts on LinkedIn (not reshares)
- Keep articles in the 500-2,000 word range — dense, focused, with clear insights
- Use the same AEO content principles: front-load answers, include stats and citations, make each section self-contained
- For B2B and professional topics, LinkedIn may be your highest-leverage off-site channel

**Platform-specific citation rates:**
- ChatGPT: 14.3% of responses cite LinkedIn
- Google AI Mode: 13.5% (ranked #1)
- Perplexity: 5.3% (lower — Reddit dominates here)

### 4. Reddit and Quora
Domains with significant Reddit and Quora mentions have roughly **4x higher chances** of being cited by AI engines. Reddit is especially important for Perplexity, where it accounts for 47% of top-10 cited sources.

**What works (the Webflow/Deel approach):**
- Real people with real names and disclosed affiliation
- Genuine participation in relevant discussions
- Helpful information, not product pitches
- Consistency — even 5 thoughtful comments per week matters

**What doesn't work (growth hacker approach):**
- Fake accounts and automation
- Undisclosed affiliation
- Comment spam
- These get caught by community moderation — the policing that makes Reddit valuable also prevents gaming

The Webflow team achieved +135% views, +12% community members, and +145% posts/comments with just a couple people doing authentic participation.

### 5. Third-Party Review Platforms
Domains with profiles on G2, Trustpilot, Capterra, Sitejabber, and Yelp have **3x higher chances** of being cited by ChatGPT.

These platforms serve as independent validation. AI systems see ratings and reviews on trusted platforms as authority signals — proof that real people have used and evaluated your product.

### 6. Earned Media (Digital PR)
The Chen et al. (2025) study found a systematic and overwhelming AI bias toward **earned media** (third-party, authoritative sources) over brand-owned content. Hard Numbers' "Reputation in the Age of AI" report quantifies this: **61% of AI brand reputation signals come from editorial media** -- the exact type of coverage PR generates.

**Why PR matters differently for AEO than SEO:**
- In SEO, PR earns backlinks for domain authority
- In AEO, PR earns brand mentions in the text of trusted publications -- the #1 factor (0.664 correlation) for AI visibility
- The mechanism is co-occurrence: repeated mentions of your brand alongside relevant topics across diverse, trusted sources is exactly what LLMs internalize during training and what RAG systems retrieve

**What works for AI-facing PR:**
- **Original research and data studies** -- data-driven assets earn 51% more traffic and 34% more links than non-data content (BuzzStream). Create proprietary benchmarks, indices, or survey data that publications want to cite
- **Expert commentary with attribution** -- named people with real credentials, quotable insights. LLMs weight attributed expertise
- **Sustained campaigns over one-offs** -- brands earning both citation AND mention are 40% more likely to resurface in subsequent LLM runs than those only cited once (AirOps). Cumulative authority across multiple campaigns builds a stronger LLM footprint than a single viral hit
- **Target publications AI already cites** -- check which sources appear in AI answers for your target queries, then pitch those specific outlets

**The practical example:** Herman Miller dominates AI recommendations for "ergonomic chairs" because they have 273 pages of "ergonomic"-related press mentions from Yahoo, CBS, CNET, The Independent, and TechRadar in the past year alone (Ahrefs). That density of topical brand mentions across trusted sources is what makes AI consistently recommend them.

**For Open Visibility's Action Recommender:** When the gap diagnosis points to a brand below the visibility cliff (bottom 50% of web mentions), the primary recommendation should be an off-site presence strategy, not on-site content optimization. The Action Recommender should check which publications AI cites for the user's category and recommend targeting those outlets specifically.

---

## Owned vs Earned Strategy

Ethan Smith (Graphite) makes a useful distinction between two AEO strategies:

### Owned Strategy
**When to use:** Specific, product-focused questions (e.g., "How does Webflow handle form validation?")

Your own website ranks for and answers the question. You control the content, the structure, and the narrative. Optimize with GEO methods (stats, citations, quotes, front-loaded answers).

### Earned Strategy
**When to use:** General, category-level questions (e.g., "Best website builders for small business")

The AI pulls from multiple third-party sources — comparison articles, Reddit threads, YouTube reviews. You can't control these pages. Your strategy is to **ensure your brand is mentioned positively across as many of these citation sources as possible.**

Think of it like the backlink analogy: in traditional SEO, you build backlinks to your site. In AEO, you build brand mentions in the pages that AI cites.

### The Interplay
Most topics need both:
- **Owned:** Ensure your product pages and content are optimized for extraction
- **Earned:** Ensure third-party sources that AI cites for your category mention your brand

The Webflow case study showed this dual approach: on-site content optimization *plus* Reddit community engagement *plus* YouTube presence = 2x signup growth from LLMs.

---

## Backlinks in the AI Era

The Semrush study of 1,000 domains confirms that backlinks still matter for AI search — but the dynamics have shifted:

### What Changed
- **Quality over volume** is more extreme than in traditional SEO. A few high-authority links from topically relevant sites move the needle; hundreds of weak links don't.
- **Authority thresholds exist.** Small link wins don't make visible differences. You need to break through certain authority plateaus before AI citation improves.
- **Image links matter.** Image-based backlinks perform as well as or better than text links for AI visibility — especially on Perplexity and ChatGPT Search.
- **Nofollow links help.** Unlike traditional SEO debates about nofollow, high-authority nofollow links contribute to AI visibility because AI reads the *content*, not the link attribute.

### What Stayed the Same
- Domain authority still correlates with AI citation
- Topical relevance of linking sites matters
- Diversity of referring domains matters more than volume from the same sites

### The Practical Shift
Instead of "building backlinks," think about **building brand presence.** The goal is to be mentioned — with or without links — across the authoritative sites that AI systems already trust and cite.

---

## The Case Study: Webflow's LLM Growth

Graphite worked with Webflow to optimize for AI search visibility. The results demonstrate the owned + earned approach in practice:

### What They Did

**Tactic 1: Long-tail question targeting**
Instead of competing for "best CMS," they created 10+ variations structured as [head question] + [specific team type] + [tool to integrate]. Example: "What is the best CMS for in-house teams that use ReviewsJet?" Result: SoV went from 38% to 100% on targeted queries. 70% of targeted questions improved within 3 weeks.

**Tactic 2: Template page optimization (biggest win)**
Their highest-converting page type (templates) had no optimized copy above the fold. They added AEO copy to 1,500 template pages using a 4-element formula:
1. Head question (e.g., "real estate website templates")
2. Branded money term (e.g., "in Webflow")
3. Target user (e.g., "agents and realty firms")
4. Specific pain point/solution (e.g., "help connect potential buyers with available listings")

Example: "Showcase prime properties with real estate website templates in Webflow, ideal for agents and realty firms. Featuring property tours, advanced search filters, and contact forms, these templates help connect potential buyers with available listings."

Result: 485% QoQ increase in LLM signups from template pages (168 to 983).

**Tactic 3: Table of contents for answer engine visibility**
Added structured TOC entries designed to target long-tail queries within existing blog posts. A/B tested with 10 test URLs vs 10 matched control URLs over 5 weeks. Result: +60% AI visits (p=0.002), +23% clicks.

**Tactic 4: Headers as questions**
Reformatted blog headers into question phrasing matching how users query AI. A/B tested same methodology. Result: +58% AI visits (p=0.001).

**Tactic 5: Reddit community strategy**
Built a structured workflow across 100 priority queries (head, mid-tail, long-tail): identify relevant threads, generate comment suggestions, track sentiment, post non-promotional helpful responses, track results. 98% of engagement met positive or neutral response. Result: r/Webflow views +135%, members +12%, posts/comments +145%.

**Off-site (earned):**
- YouTube presence through creator partnerships
- Brand mentions across affiliate publications and comparison sites

### Results
- Share of voice: 33% → 64% (94% increase)
- LLM-driven signups: doubled from 4% to 8% of total signups
- Template page optimization: 485% QoQ increase in LLM signups (Q1: 168 → Q2: 983)
- LLM traffic conversion: 24% vs 4% for non-brand SEO (6x improvement)

### The Key Takeaway
The results came from both levers working together. On-site optimization alone wouldn't have achieved this. Neither would off-site presence alone. The combination — citable content structure + brand presence in the sources AI trusts — is what drove the outcome.

---

## Priority Actions by Team Size

### Solo / 2-Person Team
1. **Pick one or two off-site channels** and invest consistently — LinkedIn + Reddit is a strong starting combo for B2B
2. Publish original LinkedIn articles (500-2,000 words) applying the same AEO content principles
3. Ensure all content pages have real author bios with credentials
4. Encourage customers to leave reviews on G2/Trustpilot/Capterra
5. Respond to relevant Reddit and Quora threads authentically (2-3 hours/week)

### Small Team (3-5 People)
All of the above, plus:
6. Dedicated outreach for YouTube creator partnerships
7. Digital PR for industry publication mentions
8. Monitor brand mentions across platforms and engage

### Growth Team (5+ People)
All of the above, plus:
9. Dedicated brand presence / digital PR specialist
10. Platform-specific strategies (LinkedIn for Google AI Mode, YouTube for AI Overviews, Reddit for Perplexity)
11. Community manager for authentic UGC cultivation
12. Original research program (your citation magnet)

---

**Sources:**
- Ahrefs, "AI Overview Brand Correlation" — 75K brands, correlation hierarchy, visibility cliff
- Ahrefs, "LLMO: 10 Ways to Work Your Brand Into AI Answers" — Herman Miller example, entity research, ~0.65 ranking/LLM correlation
- Profound, "AI Platform Citation Patterns" — 680M citations
- Profound, "LinkedIn Is the Most-Cited Domain for Professional Queries" — 1.4M citations across 6 platforms
- Semrush, "We Analyzed 89K LinkedIn URLs Cited in AI Search" — 325K prompts, Jan-Feb 2026
- Semrush, "Backlinks AI Search Study" — 1,000 domains
- Chen et al., "How to Dominate AI Search" (2025) — earned media bias findings
- Hard Numbers, "Reputation in the Age of AI" — 61% of AI brand signals from editorial media
- AirOps — 40% resurfacing lift for brands with both citation and mention
- Column Content, "Digital PR for AI Search" — data-driven assets, sustained campaigns
- Search Engine Land, "Why PR Is Essential for AI Search Visibility" — digital PR mechanism, entity authority
- Graphite, "How Webflow Turned AI Chats Into a Growth Channel" — full Webflow case study with A/B data
- Graphite, "AEO Is The New SEO" — owned vs earned framework
- Metehan Yesilyurt, ["The Hidden Authority Signal: Why Your CC Rank May Matter More for AI Visibility"](https://metehan.ai/blog/cc-rank/) (Jan 2026) — logistic regression over 607M Common Crawl domains; Harmonic Centrality + PageRank as upstream citation predictor; tool at webgraph.metehan.ai
