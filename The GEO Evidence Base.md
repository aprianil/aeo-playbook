# The GEO Evidence Base

> What the research actually shows — the proven methods, the data, and what doesn't work. No hype, no repackaged takes. Just the studies and their findings.

---

## The Princeton GEO Study (Aggarwal et al., KDD 2024)

This is the foundational paper. Researchers from Princeton, Georgia Tech, The Allen Institute for AI, and IIT Delhi tested 9 optimization methods across 10,000 queries spanning 25 domains.

### The 9 Methods Tested

| # | Method | What It Does | Type |
|---|--------|-------------|------|
| 1 | **Authoritative** | Makes text more persuasive and confident in tone | Presentation |
| 2 | **Statistics Addition** | Replaces qualitative claims with quantitative data | Content enrichment |
| 3 | **Keyword Stuffing** | Adds more query-relevant keywords | Traditional SEO |
| 4 | **Cite Sources** | Adds citations from credible sources | Content enrichment |
| 5 | **Quotation Addition** | Adds relevant quotes from credible sources | Content enrichment |
| 6 | **Easy-to-Understand** | Simplifies language for accessibility | Presentation |
| 7 | **Fluency Optimization** | Improves writing quality and flow | Presentation |
| 8 | **Unique Words** | Incorporates distinctive vocabulary | Presentation |
| 9 | **Technical Terms** | Adds domain-specific terminology | Presentation |

### The Results

| Method | Position-Adjusted Word Count | Subjective Impression | Verdict |
|--------|----------------------------|-----------------------|---------|
| No Optimization (Baseline) | 19.3 | 19.3 | — |
| **Keyword Stuffing** | 17.7 (-8%) | 20.2 | Harmful |
| **Unique Words** | 20.5 (+6%) | 20.4 | Marginal |
| **Easy-to-Understand** | 22.0 (+14%) | 20.5 | Moderate |
| **Authoritative** | 21.3 (+10%) | 22.9 | Moderate |
| **Technical Terms** | 22.7 (+18%) | 21.4 | Good |
| **Fluency Optimization** | 24.7 (+28%) | 21.9 | Strong |
| **Cite Sources** | 24.6 (+27%) | 21.9 | Strong |
| **Statistics Addition** | 25.2 (+31%) | 23.7 | Very Strong |
| **Quotation Addition** | 27.2 (+41%) | 24.7 | Best Overall |

**The pattern is clear:** The top 3 methods — Quotation Addition, Statistics Addition, and Cite Sources — all involve enriching content with verifiable, credible information. This is a fundamentally different optimization philosophy than traditional SEO, where keywords and backlinks dominated.

**Keyword stuffing doesn't just fail — it actively hurts.** It performed 8% worse than doing nothing at all.

### Combination Effects

The researchers tested all pairwise combinations of the top methods:

| Combination | Result |
|------------|--------|
| **Fluency Optimization + Statistics Addition** | Best combination — 5.5%+ above any single method |
| **Cite Sources + any other method** | Average 31.4% improvement (stronger in combination than alone) |
| **Quotation Addition + Fluency Optimization** | Strong synergy |

**The key insight:** Cite Sources becomes significantly more powerful when layered with other methods, even though it's not the top performer individually. The recommended stack: Citations + Statistics + Quotations + Fluency = maximum visibility impact.

### The Democratization Effect

One of the most striking findings — GEO disproportionately helps lower-ranked websites:

| Method | Rank 1 | Rank 2 | Rank 3 | Rank 4 | Rank 5 |
|--------|--------|--------|--------|--------|--------|
| **Cite Sources** | -30.3% | +2.5% | +20.4% | +15.5% | **+115.1%** |
| **Quotation Addition** | -22.9% | -7.0% | +3.5% | +25.1% | **+99.7%** |
| **Statistics Addition** | -20.6% | -3.9% | +8.1% | +10.0% | **+97.9%** |

A site ranked 5th in traditional search saw visibility increases of up to 115% with GEO optimization. Meanwhile, top-ranked sites actually *lost* visibility when all sources optimized.

**Why this happens:** Traditional search rankings rely on backlinks and domain authority that favor large corporations. Generative engines evaluate content quality directly through LLMs, removing those structural advantages. GEO levels the playing field.

### Domain-Specific Findings

Different methods work better in different domains:

| Method | Best Performing Domains |
|--------|------------------------|
| **Authoritative** | Debate, History, Science |
| **Fluency Optimization** | Business, Science, Health |
| **Cite Sources** | Statements, Facts, Law & Government |
| **Quotation Addition** | People & Society, Explanation, History |
| **Statistics Addition** | Law & Government, Debate, Opinion |

**There's no one-size-fits-all GEO strategy.** Match your optimization approach to your domain.

---

## The DEJAN Grounding Study

Dan Petrovic's team at DEJAN analyzed 7,060 queries with 3+ sources, tokenizing 2,275 pages and examining 883,262 total snippets.

### Key Findings

- **Fixed grounding budget:** Google allocates roughly 2,000 words per query for grounding Gemini's responses
- **Average snippet:** 15.5 words per extracted chunk
- **Median per-source allocation:** 377 words / 2,427 characters
- **Position determines share:** #1 source gets ~531 words (28% of budget), #5 gets ~266 words (13%)

### The Length Paradox

| Content Length | Coverage Rate |
|---------------|--------------|
| Under 1,000 words | 61% of content selected |
| Over 3,000 words | 13% of content selected |

Additional content beyond roughly 540 words provides minimal incremental grounding value. The implication: **density beats length.** You're competing for share of a fixed pie — a focused page with high relevance density outperforms a long page where insights are diluted.

---

## The Profound Citation Study (680M Citations)

Nick Lafferty at Profound analyzed 680 million citations across major AI platforms from August 2024 to June 2025.

### Platform Citation Biases

| Platform | Top Citation Source | Citation Pattern |
|----------|-------------------|-----------------|
| **ChatGPT** | Wikipedia (7.8% of citations, ~48% of top-10 sources) | Favors authoritative knowledge bases |
| **Google AI Overviews** | Balanced — Reddit 2.2%, YouTube 1.9%, Quora 1.5%, LinkedIn 1.3% | Diversified across social/professional platforms |
| **Perplexity** | Reddit (6.6% of citations, ~47% of top-10 sources) | Heavily favors community-driven content |

### Domain Distribution
- .com domains: 80.41% of all citations
- .org domains: 11.29%
- Newer TLDs (.ai, .io): emerging but still small

### Cross-Platform Overlap
Only 11% of domains get cited by both ChatGPT and Perplexity. These are genuinely separate ecosystems requiring separate strategies.

---

## The Graphite AI Content Study

Ethan Smith's team at Graphite conducted a rigorous study on whether AI-generated content works for search and AI citations.

### Methodology
1. Generated thousands of AI articles using ChatGPT
2. Validated Surfer SEO's AI detector against known AI content (92% accuracy)
3. Analyzed thousands of real Google searches and ChatGPT citations with the validated detector

### Findings
- **On the open web:** AI-generated content now exceeds human-created content in volume
- **In search results and citations:** 90% of cited content is human-created or human-edited. Only 10-12% is AI-generated
- **Correlation analysis:** No positive correlation between AI content and ranking/citation success. Actually shows negative correlation in many cases

> "We essentially did a very rigorous study showing that AI content does not work. AI-assisted content edited is great... But purely 100% AI-generated does not work." — Ethan Smith

---

## The Ahrefs Brand Study (75K Brands)

Louise Linehan and Xibeijia Guan at Ahrefs analyzed 15,000 prompts across platforms and studied 75K brands for AI Overview ranking factors.

### Key Findings on Backlinks and AI Search
- High-domain authority backlinks move the needle more than volume
- The overlap between AI citations and Google's top 10 results is only 12%
- ChatGPT shows only 8% overlap with Google and Bing
- Perplexity shows the strongest proximity to traditional rankings at 28%

### Correlation Factors for AI Brand Visibility
- **YouTube mentions** show the strongest correlation with AI visibility (~0.737)
- **Brand mentions across the web** are the #1 predictor across ChatGPT, AI Mode, and AI Overviews
- **Third-party platform presence** (G2, Trustpilot, Capterra) = 3x higher citation chances
- **Reddit and Quora mentions** = roughly 4x higher citation likelihood

**Critical finding:** Ranking well in Google does NOT mean you'll be cited by AI engines. The overlap is shrinking, not growing.

---

## The Semrush Backlinks Study (1,000 Domains)

Semrush analyzed 1,000 domains to determine whether backlinks still matter for AI search.

### Findings
- **Yes, backlinks still matter** — but only high-quality, authority-building links
- High-domain authority backlinks matter more than volume
- **Image links perform as well as or better than text links** — especially for Perplexity and ChatGPT Search
- Nofollow links from high-authority sources still help
- There's a threshold effect — small link wins don't make a visible difference; you need to break through authority plateaus

### Practical Implications
- Focus on earning links from diverse, authoritative, topically relevant sites
- Invest in shareable visual assets (charts, infographics, data visualizations) that earn image-based links
- Don't dismiss nofollow links from high-authority sources
- Prioritize meaningful authority gains over incremental link building

---

## Cross-Study Synthesis: What the Evidence Actually Says

Across all these studies, the consistent findings are:

1. **Evidence-based content wins.** Statistics, citations, and expert quotes are the proven methods. Keyword optimization is either irrelevant or harmful.

2. **Density over length.** There's a fixed grounding budget. Front-load your insights. A focused 800-word page outperforms a 4,000-word ultimate guide.

3. **Human quality matters.** AI-generated content doesn't rank or get cited. Human expertise and editorial judgment are what AI systems are looking for.

4. **Off-site authority is critical.** Brand mentions, YouTube presence, Reddit engagement, and review platform profiles drive AI citation more than on-page optimization alone.

5. **Platforms are separate ecosystems.** What works on ChatGPT doesn't automatically work on Perplexity or Google AI. Only ~11% overlap.

6. **GEO democratizes visibility.** Smaller sites benefit disproportionately from GEO optimization. The playing field is more level than traditional SEO.

7. **Traditional SEO is still the foundation.** AEO builds on top of technical SEO, content quality, and domain authority — it doesn't replace them.

---

**Papers and studies referenced:**
- Aggarwal et al., "GEO: Generative Engine Optimization," KDD 2024 — [arXiv](https://arxiv.org/abs/2311.09735)
- Chen et al., "Generative Engine Optimization: How to Dominate AI Search," Sept 2025 — [arXiv](https://arxiv.org/abs/2509.08919)
- DEJAN, "How Big Are Google's Grounding Chunks?" — [dejan.ai](https://dejan.ai/blog/how-big-are-googles-grounding-chunks/)
- DEJAN, "Selection Rate Optimization" — [dejan.ai/sro](https://dejan.ai/sro/)
- Profound, "AI Platform Citation Patterns" — [tryprofound.com](https://www.tryprofound.com/blog/ai-platform-citation-patterns)
- Graphite, "AI Content and Search" — [graphite.io](https://graphite.io/five-percent/ai-content-and-search)
- Ahrefs, "AI Overview Brand Correlation" — [ahrefs.com](https://ahrefs.com/blog/ai-overview-brand-correlation/)
- Semrush, "Backlinks AI Search Study" — [semrush.com](https://www.semrush.com/blog/backlinks-ai-search-study/)
