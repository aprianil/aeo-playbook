# Content Structure for AI Extraction

> How to structure content so AI systems can find, extract, and cite it. Based on DEJAN's grounding research, the Princeton GEO study, and practitioner findings from Graphite and Semrush.

---

## The Extraction Problem

When AI generates an answer, it doesn't read your entire page and write a summary. It extracts **chunks** -- small, self-contained pieces of text that it can slot into its response with a citation.

If your content isn't structured for extraction, the AI might retrieve your page but fail to cite it. You passed the retrieval gate but failed the selection gate.

Understanding how extraction works changes how you write everything.

## The AI Search Filter: Only 32% Survives

Before the LLM ever sees your content, Google's pipeline filters it. DEJAN's research (2025) on Google's Vertex AI Search grounding found that only **32% of a page's content makes it through** to the model. The rest -- roughly two-thirds -- gets discarded.

The 5-step pipeline:
1. User enters a prompt
2. Google executes fan-out queries
3. **The system generates abbreviated versions of source page texts (this is the filter)**
4. Filtered snippets are supplied to the model as context
5. The model generates an answer and applies citations

Step 3 is where most of your content dies. The filter operates before the LLM processes anything.

### What Survives the Filter
- Core service descriptions that directly answer the query
- Specific details: pricing, process steps, customization options
- Actionable, practical information
- Content with direct relevance to the user's immediate need

### What Gets Filtered Out
- Navigation and structural elements (menus, headers, footers)
- Promotional claims ("Up to 50% off")
- Tangential content unrelated to the specific query
- Customer feedback scores and review aggregates
- Copyright and legal boilerplate
- Generic/boilerplate content

### Shorter Pages Have Higher Survival Rates

| Page Size (chars) | Characters Cited | Survival Rate |
|---|---|---|
| 1,937 | 1,255 | **65%** |
| 2,608 | 547 | 21% |
| 5,530 | 2,490 | 45% |
| 8,164 | 1,793 | **22%** |

The page with the least content had the highest survival rate. More content does not mean more gets through -- it means a lower percentage of your work actually reaches the model.

**For Open Visibility's Gap Analyzer:** The selection gate diagnostic should consider content survival rate, not just content presence. A page might have great information buried under boilerplate that the filter strips away. Recommending "cut the filler, front-load the answer" is more specific than "improve content quality."

### Three Grounding Visibility Gaps

DEJAN's snippet extraction tool (snippets.dejan.ai) reveals three ways a ranked page can still fail at the selection gate:

1. **Wrong content extracted** -- your page ranks, but the AI pulls a sentence that doesn't represent your key message
2. **Competitor sentences preferred** -- a competitor's phrasing wins the grounding slot over yours, even if you rank higher
3. **Thin grounding** -- the AI extracts very few sentences from your page compared to competitors

Use the tool to diagnose which gap you're hitting for specific queries. It shows the exact sentences Google extracts from each URL, making the selection gate visible.

---

## Grounding Chunks: What AI Actually Extracts

DEJAN's research on 7,060 queries with 883,262 total snippets reveals the mechanics:

### Chunk Size
- **Average extracted snippet:** 15.5 words
- **Median allocation per source:** 377 words (~2,427 characters)
- AI doesn't extract paragraphs — it extracts sentences and sentence fragments

### The Fixed Budget
- Google allocates roughly **2,000 words total** per query for grounding
- This budget is distributed across multiple sources based on relevance ranking
- #1 source gets ~531 words (28%), #5 source gets ~266 words (13%)

### What This Means for Structure
Every section of your content should be written as if it might be extracted on its own — because it will be. The AI won't include the paragraph before it for context. The AI won't follow your "as mentioned above" reference. Each chunk must stand alone.

---

## Semantic Compression

Dan Petrovic (DEJAN) and Tom Critchlow coined the term **semantic compression** for the principle that makes content AI-extractable:

**Every content section must be contextually self-contained.**

### What Breaks Extraction

- **Pronouns without referents:** "It performs well in these conditions" — extracted alone, the reader (and the AI) has no idea what "it" refers to
- **Cross-references:** "As we discussed in the pricing section above..." — the AI extracts the section without the pricing section
- **Vague language:** "This approach works better" — better than what? The comparison was three paragraphs ago

### What Survives Extraction

- **Explicit entity naming:** "Webflow's free plan supports up to 5 users" — stands alone perfectly
- **Self-contained claims:** "Pages with expert quotes average 4.1 citations versus 2.4 without (Princeton GEO study)" — everything needed is in the sentence
- **Direct answers:** "The grounding budget is approximately 2,000 words per query" — extractable, citable, clear

### The Rule
Write every section as if it will be ripped out of context and dropped into an AI-generated answer with no surrounding material. If it still makes sense, it's semantically compressed.

---

## Title and URL: Match the Fan-Out, Not Just the User Query

Ahrefs' 2026 study of **1.4 million ChatGPT prompts** (Linehan, Apr 2026) found the strongest single predictor of citation isn't authority, length, or schema -- it's how closely your **page title matches the AI's internal sub-queries**:

- Cited pages had **title-to-fanout-query cosine similarity of 0.656** vs 0.484 for uncited pages
- Pages with **natural-language URL slugs were cited 89.78% of the time** vs 81.11% for opaque URLs (e.g., `/best-website-builders-small-business` beats `/p/2847`)
- Crucially: 67.8% of all uncited URLs are Reddit. Reddit gets retrieved heavily but cited only 1.93% of the time on ChatGPT -- the model pulls it into the candidate pool but rarely names it as the source

**The practical lever:** Don't title pages for the head query alone. Title them for the *fan-out* -- the sub-queries ChatGPT generates from a head query (see [How AI Search Actually Works](<How AI Search Actually Works.md>) for the RRF mechanics). A page titled "Best Website Builders" matches one query. A page titled "Best Website Builders for Small Business in 2026 — Webflow, Squarespace, Wix Compared" matches the actual fan-out cluster.

This connects to the title-as-citation-anchor pattern: AI models use the title both for retrieval (does this page belong in the candidate set?) and selection (which sentence do I pull and from which page?). A precise, fan-out-matching title earns both gates with one signal.

---

## Front-Loading: The First 30% Rule

Research consistently shows that the beginning of your content matters disproportionately:

- **44.2% of all LLM citations** come from the first 30% of the text (intro section)
- **31.1%** from the middle
- **24.7%** from the conclusion

AI models favor content that provides immediate classification — clear entities and direct answers up front. If your substance isn't surfaced early, it's less likely to appear in AI answers.

### The Answer-First Pattern

For every section that answers a question:

1. **Verdict sentence:** Direct answer in 15 words or fewer. No setup.
2. **Evidence sentence:** The specific fact, metric, or comparison that proves it.
3. **Context sentence:** Who this applies to, or when it doesn't.

**Good:**
> "Webflow's free plan supports up to 5 users with unlimited tasks and 3 active projects. Paid plans start at $29/user/month and include unlimited projects and native time tracking. For teams under 10, the free plan covers time tracking without upgrade."

**Bad:**
> "When it comes to project management tools, there are several options available. Webflow has addressed the need for team collaboration by including various features that many users find helpful for managing their workflows."

The good example is extractable. The bad example says nothing in its first 40 words.

---

## Content Format: Comparative Listicles Dominate

SEOmator/Profound's analysis of 41M+ AI search results (177M cited sources, 2025) found that **comparative listicles account for 32.5% of all AI citations** (57.6M citations) -- far ahead of blogs/opinion pieces at 9.9%. AI systems strongly favor structured comparison formats.

This reinforces the "extraction-friendly" principle: comparison tables, ranked lists, and side-by-side evaluations are what AI most naturally pulls from. For Open Visibility's Action Recommender, when the gap diagnosis points to a commercial query, the default content recommendation should lean toward comparison/listicle format.

Another finding from the same analysis: **95% of AI citation behavior cannot be explained by website traffic metrics.** Sites with near-zero traffic get 900+ citations. Traditional authority signals (backlinks, domain rating) are weak predictors -- content format and structure are stronger signals.

---

## Heading Structure: Match the Query, Not a Format

Three studies once looked like they conflicted on heading format. The synthesis is now clear: it's not "question vs declarative" -- it's **literal match to the user's query**.

- **Indig, "Shorter Focused Content Wins" (Apr 2026, 815k query-page pairs):** Pages with a direct headline-to-query match are cited **41% of the time vs 29% for loosely related** -- a bigger lift than word count or domain authority.
- **Webflow/Graphite A/B test:** Headers reformatted as questions produced a **+58% uplift in AI visits** (p=0.001). The mechanism wasn't "questions are magic" -- the questions matched how users phrased their AI prompts.
- **Semrush/ChatGPT:** Question-style headings earned 3.4 vs 4.3 citations for straightforward headings. The straightforward headings happened to match the underlying queries more literally.

### The Practical Takeaway
- Forget the "questions vs statements" debate. Make the H2 echo the literal query, in whatever form the user types it.
- Specificity beats both: "Pricing Comparison: Webflow vs Squarespace 2026" beats both "Pricing" and "What Does It Cost?"
- Indig's data also shows: 78.4% of citations come from the H2 + the paragraph immediately following it. Make the answer entity-dense and front-loaded under each matching header.

---

## Content Length: The Density Sweet Spot

The research converges on a clear pattern:

| Finding | Source |
|---------|--------|
| Pages under 1,000 words: 61% content coverage in grounding | DEJAN |
| Pages over 3,000 words: 13% content coverage in grounding | DEJAN |
| Content plateau at ~540 words: minimal incremental grounding value beyond this | DEJAN |
| Short articles (<800 words): average 3.2 ChatGPT citations | Semrush |
| Long-form (>2,900 words): average 5.1 ChatGPT citations | Semrush |
| **26-50% subtopic coverage beats exhaustive guides on ChatGPT** | Indig (815k pairs) |
| **Sweet spot: 500-2,000 words with 7-20 H2-H4 sections** | Indig (815k pairs) |
| Near-zero correlation between word count and AI Overview citations | Multiple studies |

**The synthesis:** Longer content gets more total citations on ChatGPT (because it covers more subtopics), but two things go down with length: the *density* of grounding, and the *focus* the model rewards. Indig's 2026 study found that pages covering 26-50% of a topic's subtopic space outperform exhaustive guides -- there's a ceiling on how much breadth helps before it starts hurting.

The new sweet spot:
- **For AI Overview citation:** Focused, 800-1500 word pages with high relevance concentration.
- **For ChatGPT citation:** 500-2,000 words, 7-20 H2-H4 sections, covering 26-50% of the fan-out subtopic space -- not 100%.
- **Always:** No filler. Every paragraph earns its place.

This refines the existing "density beats length per page, breadth wins across the cluster" principle: breadth still wins across the cluster, but each page should aim for moderate-coverage focus, not exhaustive coverage.

---

## What AI Actually Sees (And Doesn't See)

A critical finding from the Critchlow-Petrovic deep dive (DEJAN, 2025): when AI generates an answer, the model receives **text, markdown, and basic HTML elements** (like `<b>` tags or `<div>` structures). It does NOT see:
- CSS or visual layout
- Your page design or formatting
- Schema markup in its raw JSON-LD form
- Images (unless the platform specifically processes them)

Your beautiful page design is invisible to the model. Only text content and basic structural HTML matters for the selection gate.

**But schema still matters -- just at a different gate.** Schema helps at the **retrieval gate**: crawlers and indexing systems use structured data to classify, discover, and prioritize your content. The `additional_info` field Google generates (see [How AI Search Actually Works](<How AI Search Actually Works.md>)) may be influenced by schema. But the LLM that writes the final answer reads text, not schema.

**The practical takeaway:** Invest in schema for discoverability (retrieval gate). Invest in text quality and structure for citability (selection gate). Don't assume that adding schema will directly improve how the LLM presents your content -- it improves whether the LLM sees your content at all.

**For Open Visibility's Gap Analyzer:** This clarifies the two-gate diagnostic. Schema presence/quality is a retrieval gate check. Content text quality (front-loading, semantic compression, evidence density) is the selection gate check. They're separate diagnostics with separate fixes.

---

## Schema Markup

Structured data helps AI systems classify and discover your content at the retrieval layer:

- **FAQPage schema** improves AI citation likelihood by approximately 30%
- **Article schema** with publication and modification dates signals freshness
- **Organization schema** reinforces entity recognition
- **Person schema** on author bios strengthens E-E-A-T signals

### Priority Implementation
1. Article schema on all content pages (with datePublished and dateModified)
2. FAQ schema on pages with Q&A content
3. Organization schema on your about/company page
4. Person schema on author bio pages

Validate with Google's Rich Results Test before publishing.

---

## Technical Requirements for AI Crawlers

AI crawlers have limitations that traditional web crawlers handle fine:

### JavaScript Rendering
Most AI crawlers **cannot execute JavaScript.** If your content is rendered client-side (React, Vue, Angular without SSR), AI crawlers see an empty page. Server-side rendering or static generation is required.

### Robots.txt Configuration
Allow these crawlers explicitly:
- **GPTBot** — OpenAI (ChatGPT)
- **ClaudeBot** — Anthropic (Claude)
- **PerplexityBot** — Perplexity
- **Bingbot** — Microsoft (feeds ChatGPT's index)
- **Googlebot** — Google (feeds AI Overviews)

**Nuance:** You can differentiate between training and indexing. Block AI from training on your content if you want, but allow indexing for citations. Use robots.txt to make this distinction.

### Page Speed
Target First Contentful Paint (FCP) under 0.4 seconds. Slow pages get deprioritized in both traditional and AI search.

### llms.txt
An emerging standard — a machine-readable summary of your site that helps LLMs understand your content structure. Low implementation effort, unclear impact so far, but worth having as the standard matures.

---

## Diagnose Before You Rewrite

A 2026 paper (Tian et al., AgentGEO, arxiv 2603.09296) tested two approaches to citation optimization on the same content set:

- **Diagnose-then-repair:** identify the specific failure mode for each page (wrong content extracted, competitor preferred, thin grounding, missing fan-out match) and edit only the problem. Resulted in **>40% relative citation lift while editing only 5% of content.**
- **Generic rewrite:** rewrite pages broadly using best-practice prompts. Resulted in 25% lift -- and **actively hurt** long-tail pages where the original content was already well-targeted.

This is the academic backing for the playbook's existing 5% Rule: most pages don't need optimization, and broad rewrites are a worse use of budget than surgical edits. Use DEJAN's snippet extraction tool (snippets.dejan.ai) to see which failure mode you're hitting before deciding what to change.

A separate 2026 paper (Yu et al., arxiv 2603.29979) found that **structural-only edits** -- no copy changes, just architecture and chunking -- drove **+17.3% citation rate and +18.5% subjective quality** across 6 mainstream generative engines. Decomposes into macro (document architecture), meso (chunking and headings), and micro (visual emphasis). This means the diagnose step should explicitly include "is the structure broken?" before assuming it's a content problem.

---

## The Formatting Checklist

Before publishing any content optimized for AI citation:

```
Structure
- [ ] Core answer in first 40-60 words of each section
- [ ] Each section self-contained (no cross-references, no unresolved pronouns)
- [ ] Explicit entity names used throughout (not "it," "this tool," "the platform")
- [ ] Statistics with sources and sample sizes embedded inline
- [ ] Expert quotes with full attribution (name, credentials, organization)

Formatting
- [ ] Direct topical headings (specific > generic)
- [ ] Comparison tables where relevant (AI loves extracting tables)
- [ ] No filler paragraphs — every paragraph earns its place
- [ ] White space between sections for scannability

Technical
- [ ] Schema markup added and validated
- [ ] Server-side rendered (AI crawlers can't execute JS)
- [ ] AI crawlers allowed in robots.txt
- [ ] Publication date and "Last Updated" timestamp visible
- [ ] Author bio with real credentials linked
- [ ] Page speed under 0.4s FCP
```

---

**Sources:**
- DEJAN, "How Big Are Google's Grounding Chunks?" — 7,060 queries, 883,262 snippets
- DEJAN, "AI SEO Deep Dive" (Critchlow & Petrovic) — semantic compression framework, models see text not CSS/schema
- DEJAN, "Hacking Gemini" — intermediate summarization layer, `additional_info` field
- DEJAN, "How Much of Your Content Survives the AI Search Filter?" — 32% survival rate, 5-step filter pipeline
- DEJAN, "Grounding Snippet Extraction Tool" — three visibility gaps, snippets.dejan.ai
- Princeton GEO study (Aggarwal et al., KDD 2024) — 9 methods across 10K queries
- Ahrefs, ["Why ChatGPT Cites One Page Over Another"](https://ahrefs.com/blog/why-chatgpt-cites-pages/) (Linehan, Apr 2026) — 1.4M prompts; title-to-fanout cosine similarity, URL slug effect, Reddit retrieval-vs-citation gap
- Indig, ["Shorter, Focused Content Wins in ChatGPT"](https://www.growth-memo.com/p/shorter-focused-content-wins-in-chatgpt) (Apr 2026) — 815k query-page pairs; 26-50% subtopic coverage, 7-20 H2-H4 sweet spot, headline-to-query match 41% vs 29%
- Yu et al., ["Structural Feature Engineering for GEO"](https://arxiv.org/abs/2603.29979) (Mar 2026) — structural edits +17.3% citation rate across 6 engines
- Tian et al., ["AgentGEO: Diagnosing and Repairing Citation Failures"](https://arxiv.org/abs/2603.09296) (Mar 2026) — diagnose-then-repair: 40% lift editing 5% of content
- Semrush, "ChatGPT Search Insights" — heading structure and content length data
- Graphite, "How Webflow Turned AI Chats Into a Growth Channel" — A/B testing data
- Google Search Central, "Succeeding in AI Search" — technical requirements
- Prerender, "How to Optimize Your Website for AI Crawlers" — JS rendering limitations
