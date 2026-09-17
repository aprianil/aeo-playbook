# AEO Measurement and Tracking

> How to measure AI visibility — the right metrics, the pitfalls that mislead, and how to know if your optimization is actually working. Based on Graphite's measurement framework, DEJAN's Selection Rate Optimization research, and practitioner data.

---

## Why Measurement Is Different

Traditional SEO measurement is deterministic: same keyword, same results, every time. Simple keyword tracking tools work fine.

AI search is **probabilistic.** Same question, different answer every time. The model samples from a probability distribution, so citations rotate across runs. A single check tells you almost nothing.

**But probabilistic does not mean unmeasurable.** The mechanism is well-understood (Graphite, Smith & Druck, 2026): the core LLM deterministically creates probability distributions over next tokens. When RAG is used, the retrieval step is largely deterministic (search algorithms). The randomness enters at the sampling stage -- temperature and other parameters control how the probability distribution gets sampled into actual text. This means visibility is a *distribution* with a measurable center and spread, not chaos. The same statistical tools that work for any probability distribution -- confidence intervals, significance tests, sequential sampling -- work here. You don't need a massive sample. You need an appropriate one.

SparkToro and Gumshoe quantified this (2,961 queries across ChatGPT, Claude, Google AI, Nov-Dec 2025):
- **Less than 1 in 100 chance** of getting identical brand lists across two runs of the same prompt
- **Less than 1 in 1,000 chance** of identical ordering
- Response length varies wildly (2-3 to 10+ recommendations per response)
- Real users with the same intent craft radically different prompts -- average semantic similarity between same-intent prompts is only **0.081** (described as "Kung Pao Chicken and Peanut Butter")

**Ranking position is meaningless.** Being "#1" in an AI response is not a reliable metric. Fishkin calls tracking position "full of baloney." The only valid metric is **visibility percentage** -- how often your brand appears across many runs.

**Category breadth affects consistency.** Narrow, well-defined sectors (specific SaaS tools, regional searches) show 89-97% brand appearance rates. Broad categories (novels, design agencies) show 30-49%. This maps to head vs tail: tail queries produce more stable, actionable data than head queries.

**For Open Visibility:** This validates our statistical sampling approach but raises the bar. The arxiv paper (2603.08924) demonstrates that single-run visibility metrics are "misleadingly precise" -- many apparent differences between domains fall within the noise floor of measurement. Three concrete implications:
1. **Adaptive sampling:** 10-20 runs for narrow/tail queries (89-97% consistency), scale to 30+ for broad/head queries (30-49% consistency). Use sequential sampling: start with a pilot batch, calculate variance, expand if confidence interval is still too wide
2. **Confidence intervals on every metric:** Report "70% share of voice +/- 12%" not just "70%." Users need to see when a change is real vs noise
3. **Significance indicators:** When comparing time periods or domains, flag whether the difference exceeds the noise floor. "Your visibility dropped from 45% to 38%" should come with "this is / is not statistically significant at 95% confidence"

Our open-source methodology is a direct answer to Fishkin's criticism that most AI tracking vendors lack transparent math.

---

## Retrieval, Mentions, Citations, and Recommendations Are Four Different Signals

Before diving into metrics, the field has formalized AI visibility into four distinct levels (Georgieva 2025; Indig "Ghost Citation Problem" 2026; Ahrefs 1.4M prompt study 2026):

| Signal | What it means | Example |
|---|---|---|
| **Retrieval** | Page pulled into the candidate set, but not used | Reddit thread retrieved, never quoted or linked |
| **Mention** | Brand named in the answer, no link | "Tools like Webflow and Squarespace offer..." |
| **Citation** | Page linked as a source | "According to Webflow's pricing page [link]..." |
| **Recommendation** | Brand positioned as a top pick | "For small teams, Webflow is the best option because..." |

These do not move together. Engines split asymmetrically on what they reward:
- **Gemini:** mentions 83.7% of the time, cites only 21.4% (Indig, Ghost Citation Problem, 3,981 domain appearances across 4 engines)
- **ChatGPT:** cites 87% of the time, mentions only 20.7% (same study)
- **Reddit on ChatGPT:** retrieved heavily, cited only 1.93% of the time. 67.8% of all uncited URLs are Reddit (Ahrefs, 1.4M prompts)

A "ghost citation" — where your page is linked but your brand isn't named — accounts for 62% of all brand citations on average. Comparative and evaluative content drives mentions at ~30x the rate of pure informational content.

These require different strategies to improve:
- **Not retrieved?** Discoverability problem (crawlers, indexation, fan-out title match — see [[Content Structure for AI Extraction]])
- **Retrieved but not mentioned?** Authority problem (Reddit-style — content is in the candidate pool but the model doesn't trust it enough to quote)
- **Mentioned but not cited?** Off-site authority signal but no on-page anchor for the link (build cite-able evidence, digital PR)
- **Cited but not recommended?** Selection problem (content structure, evidence density, competitor comparison)

**For Open Visibility's tracker:** report all four levels separately per engine, not a unified visibility number. The right diagnostic depends on which level is failing -- and engine asymmetry means a brand can be doing great on Gemini's mention axis and failing on ChatGPT's citation axis simultaneously.

**For Open Visibility's Gap Analyzer:** Track all three levels separately. The diagnostic changes entirely based on which level is failing. The Visibility Tracker should distinguish mentions from citations from recommendations in its reporting.

---

## The Core Metrics

### 1. AI Share of Voice
**What it measures:** How often your brand appears in AI-generated answers for your target queries.

**How to measure (sequential sampling protocol from Graphite/Druck, "How to Track Entity Position in AI", 2026):**
- Define your target queries (the questions your audience asks)
- Run a pilot batch of **10 queries per prompt per platform**. At n=10, mean visibility error is 5.6% and position error is 1.06; **98.6% of prompts hit ≤10% error at n=10** (Smith & Druck, "Demystifying Randomness in AI", April 2026)
- For prompts where the 95% confidence interval is still wider than ±2.0 percentage points (typically broad/head queries with 30-49% category consistency), expand the sample sequentially. Sequential sampling cuts total samples 59% on average vs. flat n=135 (135 → 55 for the same CI width)
- Calculate appearance rate with confidence intervals: "70% share of voice ±5%" not just "70%"
- **Visibility first, then position.** Visibility is more stable than rank order across runs — track visibility as the primary metric and position as the secondary
- Track weekly. ChatGPT's query rewriting has 91% uniqueness across runs (Profound, Apr 2026) — monthly cadence misses too much movement. The same prompt rarely fires the same internal sub-queries twice

This is the AI equivalent of search ranking position — but probabilistic instead of deterministic. Report uncertainty alongside every metric.

### 2. Selection Rate (SRO)
**What it measures:** How often AI *chooses* your content from the candidate sources it retrieved.

Dan Petrovic (DEJAN) defines Selection Rate as the AI search equivalent of Click-Through Rate (CTR). When LLMs review snippets from various sources, they decide which to select and how to present them. Selection Rate measures that decision.

**Why it matters:** You might be retrieved frequently (your content is in the candidate pool) but selected rarely (the AI keeps choosing competitors instead). SRO helps you diagnose this gap.

**DEJAN's SRO Simulation Process (from the Critchlow-Petrovic deep dive):**
1. **Harvest organic queries** -- pull real queries from Google Search Console
2. **Generate synthetic snippets** -- use a local LLM to create hundreds of content variations for each query
3. **Selection simulation** -- feed 100+ snippets (yours + competitors) into a model simulating AI's choice mechanism, asking "pick the best one"
4. **Measure selection frequency** -- track how often your brand's content gets selected vs. competitors
5. **Rewrite and iterate** -- rewrite underperforming snippets and re-run the simulation

The critical advantage: you iterate in seconds instead of waiting weeks for crawl/index cycles. "We aren't waiting for Google to crawl and index; we are simulating the AI's choice mechanism to find the perfect content structure."

**For Open Visibility's Gap Analyzer:** SRO simulation could power a pre-flight check -- "Will this content get picked?" before the user publishes. The Action Recommender generates a content brief, simulates its selection rate against current competitors, and adjusts before the user invests time creating it.

### 4. Brand Saliency (Parametric Memory Bias)
**What it measures:** How much the model inherently favors your brand from training data -- separate from what it retrieves in real-time.

Dan Petrovic (DEJAN) proposes measuring this by prompting: "Would you recommend [Brand] for [Service]?" and measuring the **probability of the "Yes" token** appearing. This gives a confidence score for the model's built-in bias toward your brand.

**Why it matters:** This distinguishes between two different types of AI visibility:
- **Brand mention potential** (parametric memory) -- does AI know you from training data?
- **Brand citation potential** (real-time retrieval) -- does AI find and cite your content when it searches?

A brand with high saliency but low citation rate has a memory-vs-retrieval gap. A brand with low saliency but growing citation rate is building real-time visibility that will eventually feed into future training data.

**Practical method -- the Temperature Zero Trick (Metehan Yesilyurt, 2025):**
At temperature 0.0, an LLM becomes deterministic -- it always picks the highest-probability next token. Use **masking prompts** to extract the model's "default truth":
- `"[YourBrand] is known for ___"`
- `"[YourBrand] compared to ___"`
- `"Best [service] providers include ___"`

Run these at T=0 in Google AI Studio or OpenAI Playground. The output reveals four layers:
1. **Default truth** -- the canonical knowledge about your brand
2. **Implicit biases** -- which competitors appear as defaults in your category
3. **Confidence mapping** -- detailed responses = high confidence; vague = knowledge gaps
4. **Semantic relationships** -- strongest conceptual connections the model learned

**For Open Visibility's Brand Intelligence:** Temperature-zero probing is a concrete, repeatable way to benchmark how LLMs represent a brand. Run masking prompts at T=0 across multiple models during onboarding, then track how responses change over time after optimization work.

### 5. Brand Perception Mapping (LLM Association Networks)
**What it measures:** How AI perceives your brand -- what topics it associates with you, and which brands it associates with your topics.

DEJAN's methodology (Petrovic, 2025) uses two prompt directions:
- **Brand-to-Entity (B→E):** "List ten things you associate with [Brand Name]" -- surfaces what the LLM connects to your brand
- **Entity-to-Brand (E→B):** "List ten brands you associate with [Topic/Keyword]" -- surfaces which brands the LLM connects to a concept (reveals competitors and positioning)

Run across multiple LLMs (GPT-4o, Gemini minimum) to mitigate single-model bias. Collect both **grounded** (search-backed) and **ungrounded** (pure model knowledge) responses.

**The grounded vs ungrounded gap is where AEO opportunities live:**
- **Grounded response** = what AI finds right now when it searches (current web visibility)
- **Ungrounded response** = what AI knows from training data (parametric memory)
- **Gap** = difference between the two. A brand with strong grounded visibility but weak ungrounded presence is building real-time authority that hasn't made it into training data yet. The reverse means AI "knows" you but can't find fresh evidence.

Analysis dimensions: frequency of association, average rank position, weighted score (frequency x rank), time series tracking, and competitive network overlays.

**For Open Visibility's Brand Intelligence:** The B→E prompt maps directly to brand perception auditing during onboarding. The E→B prompt powers competitive discovery -- "who does AI think your competitors are?" The grounded/ungrounded gap informs whether to prioritize on-site optimization (improve what AI finds) or off-site presence (improve what AI remembers).

### 6. AI Referral Traffic
**What it measures:** Actual visits from AI platforms to your website.

Track in GA4 by creating a custom report:
1. Reports > Library > Create New Report > Traffic Acquisition template
2. Add "Session Source / Medium" column
3. Apply a regex filter using "Matches Partial Regex": `chatgpt|perplexity|claude|gemini|copilot`
4. Save as "AI Search Traffic" for repeated access

Key referral sources to track:
- chat.openai.com (ChatGPT)
- perplexity.ai
- claude.ai
- gemini.google.com
- copilot.microsoft.com

**Attribution caveat:** A significant chunk of AI-referred traffic lands in the "direct" bucket in GA4 and never gets properly attributed. Monitor unexplained direct traffic spikes as a secondary signal.

**Important context:** AI referral traffic is currently small in absolute terms (~1.08% of total traffic), but it's growing 300% year-over-year. More importantly, it converts at significantly higher rates — Webflow saw 6x better conversion from LLM traffic vs non-brand SEO.

---

## The Three-Dimensional Tracking Framework

Ethan Smith (Graphite) proposes tracking across three dimensions to get an accurate picture:

### Dimension 1: Track By Platform
Track performance across ChatGPT, Perplexity, Google AI Overviews, and Claude separately.

Why: Each platform has different citation algorithms. Only ~11% of domains are cited by both ChatGPT and Perplexity. Different user bases too — ChatGPT skews mass market, Claude skews professional.

### Dimension 2: Track By Question Variations
An AEO topic is a cluster of hundreds or thousands of questions that share similar intent. Tracking one question tells you your performance for that one question only.

Example variations for the same intent:
- "What's the best website builder?"
- "Which website builder should I use?"
- "Top website builders for small business"
- "Website builder recommendations"

All target the same intent but may produce different citations. Track across variations.

### Dimension 3: Track By Run
Same question, same platform, multiple runs. Because AI answers are probabilistic:
- Ask the same question 10-20 times
- Calculate share of voice (appeared in 7/10 = 70%)
- Track average rank across runs
- Monitor variance over time

---

## The Pitfalls That Mislead

### Pitfall 1: Misattribution
LLM usage is growing rapidly. If traffic from ChatGPT goes up 50%, it might be entirely due to increased platform usage — not your optimizations.

**Solution:** Isolate changes to a test group. Compare against a control group with no changes. Look for statistically significant improvements in the test group vs control. Without this, you can't distinguish your work from organic platform growth.

### Pitfall 2: Relative vs Absolute Reporting
Traffic going from 1 visit/day to 10 visits/day is a 900% increase. Sounds impressive. It's 9 additional visits.

**Solution:** Always report three numbers:
- Absolute numbers (9 additional visits)
- Relative percentages (900% increase)
- Business impact (X conversions, Y revenue)

If someone only shows you the relative number, ask for the absolute.

### Pitfall 3: No Control Group
Without a control group, you can't distinguish between:
- Your optimization work
- Natural platform growth
- Seasonal variance
- Algorithm changes

**Solution:** Hold back a subset of pages as a control. Optimize the test group. Compare the two over time. This is the only way to isolate your impact.

### Pitfall 4: Point-in-Time Snapshots
40-60% of cited sources rotate monthly. A single check is a snapshot of a moving target.

**Solution:** Track over time, across multiple runs. Look for trends, not individual data points.

### Pitfall 6: Personalization Distorts Everything
ChatGPT's personal memory injects topics from a user's conversation history into new responses (Metehan Yesilyurt, 2025). When Metehan asked for "latest AI news," the response included "SEO" -- a topic not in any cited sources, pulled solely from his prior conversations. The system classifies requests as "directly related," "related," "tangentially related," or "unrelated" to the stored user profile.

**The measurement problem:** Two users asking the identical question get different brand mentions. AEO tracking tools scraping logged-in sessions measure personalized results, not the baseline. There is no way to see personalized vs non-personalized responses side by side.

**Solution:** Use fresh/logged-out sessions or API calls for tracking (as the playbook already recommends). But acknowledge that API results are directionally accurate, not what real logged-in users actually see. This is a structural limitation of all current AEO measurement.

### Pitfall 7: Assuming Google Rankings Predict AI Citations
The overlap has shrunk dramatically. **Only 37.9% of AI Overview citations come from URLs ranking in Google's top 10** (Ahrefs, Mar 2026 update) -- down from ~76% in mid-2025. 31% of cited pages rank 11-100, and 31% don't rank in the top 100 at all. AI Overviews are fanning out far beyond the SERP.

**Solution:** Track AI visibility separately from SEO rankings. They're increasingly independent signals. Don't deprioritize a page for AEO just because it's not ranking, and don't assume a top-10 page will get cited by default.

### Pitfall 7a: Treating the AIO Pullback as the Final State
A wave of late-2025 reports said AI Overviews were collapsing — trigger rate dropped from 25% to 16%, CTR fell to 1.3%. That trough was real, but **it reversed.** Seer's panel (n=53 brands, 5.47M queries, 2.43B impressions, Apr 2026) shows AIO CTR rose from 1.3% (Dec 2025) to 2.4% (Feb 2026) — **+85% in two months.** AIO is also heavily query-segmented: present in ~95% of comparison queries, ~5% of transactional. Don't write off the channel based on Q4 2025 numbers; check segment by segment.

### The 3-Month Recency Cliff
LLMrefs' analysis of 10,000 queries found a sharp drop in AI citations when content becomes more than 3 months old. This is more specific than the general "freshness matters" signal -- it suggests a concrete refresh threshold.

Combined with the existing data (Perplexity: 82% citation rate for content <30 days vs 37% for older; Google AI Overviews: 3.2x more citations for content <30 days), the freshness signal operates on two levels:
- **30-day window:** Peak citation advantage, especially on Perplexity and Google AI
- **3-month cliff:** Sharp drop-off across all platforms

**For Open Visibility's Action Recommender:** Content refresh recommendations should use these thresholds -- flag pages approaching 90 days since last update as high-priority refreshes, with the strongest urgency for pages past 30 days on freshness-sensitive platforms.

### Pitfall 8: Treating Noise as Signal
The arxiv paper (2603.08924) found that bootstrap confidence intervals across Perplexity, SearchGPT, and Gemini reveal many apparent domain differences fall within the noise floor. Citation distributions follow power-law patterns with substantial variability -- a domain appearing in 4/10 runs vs 3/10 runs is likely noise, not a real change.

**Solution:** Never act on visibility changes without checking significance. At minimum: calculate the confidence interval for each measurement period and check whether they overlap. If they do, the difference is noise. For small sample sizes (10-20 runs), even a 10-15 percentage point swing can be within the noise floor. Report uncertainty alongside every metric.

### Pitfall 9: Conflating Organic Visibility with Ad-Adjacent Visibility
ChatGPT now serves ads in **roughly 20% of US responses** (LLMrefs, Apr 2026, 682K answers tracked since Feb 2026). A brand "winning" AI visibility may increasingly be paying for placement that gets reported alongside organic citations. As more platforms monetize, the visibility number you're tracking may quietly shift from "trusted by AI" to "bid the highest."

**Solution:** Tag ad-adjacent appearances separately from organic citations in your tracker. Watch for fast jumps in share of voice that correlate with new ad-product launches at the platform — that's a signal to dig in, not celebrate.

### Pitfall 5: Fake Case Studies
The AEO space is new and full of vendors selling tools. Watch for:
- Misattribution (crediting AEO work when platform usage grew)
- Vanity metrics (keyword rankings instead of traffic/conversions)
- No control groups
- Only relative percentages with no absolute numbers
- Results from a single platform check

Apply the same skepticism you'd apply to any marketing claim.

---

## The Tool Landscape

Ethan Smith (Graphite) surveyed 50+ AEO tools and found the market largely commoditized around a shared baseline feature: **AI answer tracking.**

### Current State (Graphite, 60+ tools surveyed, 2025)
- **Tracking is fully commoditized.** Every tool does the same thing: monitor how often your brand appears in AI answers. This is the baseline feature shared across 60+ tools
- **Optimization hasn't been figured out yet.** No tool has cracked the recommendation/action layer. Content optimization, citation optimization, and technical AEO features are all still immature
- **Premium pricing is not justified.** Graphite's explicit advice: "Focus primarily on AI tracking and use the least expensive tool that completes the job"
- **No question research tools exist.** Prompt discovery is a gap in the market -- Graphite expects tools to emerge soon
- **$200M+ in VC funding** has entered the AEO tool space (Airops $60M, Profound $59M, Peec $29M, Scrunch $19M, Evertune $19M)

**For Open Visibility's positioning:** This validates our approach. The market is crowded on tracking and empty on optimization. Our playbook-driven Action Recommender -- traceable, evidence-backed recommendations with the closed loop -- is the layer nobody has built yet. The gap between "here's your visibility score" and "here's what to do about it" is exactly where we sit.

### Key Tool Categories

| Category | What It Does | Examples |
|----------|-------------|---------|
| **AI visibility tracking** | Monitor brand citations across AI platforms | Profound, Otterly.ai, Peec AI |
| **Brand monitoring** | Track brand mentions for free / low cost | Ahrefs Brand Radar (free, 250M+ prompts) |
| **Content optimization** | Suggest improvements for AI extraction | Emerging — most tools still basic |
| **Technical audit** | Check AI crawler access, schema, speed | Standard SEO tools + manual checks |

### DEJAN's Research Tools (Free/Open)
- **AI Rank** (airank.dejan.ai) — daily volatility in AI brand rankings
- **Grounding Snippet Extraction** — see what Google actually extracts from your pages
- **Knowledge Graph Checker** — verify if your brand is a known entity
- **QDG (Query Deserves Grounding)** — test which queries trigger retrieval

### Practical Recommendation
Start with **Ahrefs Brand Radar** (free) for basic monitoring. Add a paid tool only when you need deeper cross-platform tracking or have enough volume to justify the investment. The tool won't make your strategy — the strategy makes the tool useful.

---

## Setting Up Measurement (The Minimum)

### Week 1: Baseline
1. Define 20-30 target queries (the questions your audience asks AI)
2. Run each query 10x on ChatGPT and Perplexity (your two highest-priority platforms)
3. Record: which brands appear, how often, in what position
4. Set up AI referral traffic tracking in GA4 (takes 10 minutes)

### Ongoing: Weekly Pulse
1. Run your top 10 queries across platforms (5-10 runs each)
2. Track share of voice trends
3. Note any new competitors appearing
4. Log observations in your learnings log

### Monthly: Full Review
1. Run full query set across all platforms
2. Compare test group vs control group (if you've isolated changes)
3. Report absolute numbers + relative change + business impact
4. Adjust strategy based on what's working and what isn't

---

## What Good Measurement Looks Like

| Metric | What to Track | Cadence |
|--------|--------------|---------|
| **AI Share of Voice** | % appearance rate across target queries per platform | Weekly |
| **AI Referral Traffic** | Absolute visits from AI platforms in GA4 | Weekly |
| **Conversion Rate** | Signup/purchase rate from AI referral traffic vs other sources | Monthly |
| **Citation Quality** | Are you cited positively? In what context? | Monthly |
| **Competitor Movement** | Who's appearing for your target queries that wasn't before? | Monthly |
| **Content Performance** | Which pages are getting cited? Which aren't? | Monthly |

The goal isn't to track everything. It's to track enough to know whether your strategy is working and where to invest next.

---

**Sources:**
- Graphite, "AEO Is The New SEO" — three-dimensional tracking framework, measurement pitfalls
- Graphite, "AEO Tools" — 60+ tools surveyed, market assessment, $200M+ VC funding data
- DEJAN, "Selection Rate Optimization" — SRO full 3-phase methodology, token-level optimization
- DEJAN, "AI SEO Deep Dive" (Critchlow & Petrovic) — SRO simulation methodology, brand saliency measurement
- DEJAN, "Beyond Rank Tracking" — brand perception through LLM association networks, B→E/E→B methodology, grounded vs ungrounded gap
- Search Engine Land, "How to Track Visibility Across AI Platforms" — mentions vs citations vs recommendations, tool selection criteria
- seoClarity, "Track AI Search Traffic in GA4" — GA4 setup steps, regex filtering
- Ahrefs, "AI Overviews Reduce Clicks by 34.5%" — difference-in-differences methodology, 300K keywords
- Search Engine Land, "AI Overviews Surged Then Pulled Back" — Semrush 10M keyword study, AIO coverage timeline, commercial query expansion
- SEOmator/Profound, "41M AI Search Results Analysis" — 95% of citations unexplained by traffic, comparative listicles = 32.5%
- Graphite, "How Webflow Turned AI Chats Into a Growth Channel" — conversion data
- LLMrefs, "GEO 2026 Guide" — 3-month recency cliff, Google/AI citation divergence data
- SparkToro & Gumshoe, "AIs Are Highly Inconsistent When Recommending Brands" — 2,961 queries, inconsistency quantification, prompt diversity (0.081 similarity), narrow vs broad consistency
- Conductor, "AEO/GEO Benchmarks Report 2026" — market investment data
- Graphite, Smith & Druck, "Demystifying Randomness in AI" (April 2026) — mechanistic explanation of why AI visibility is measurable, incentive transparency
- Graphite, ["How To Track Entity Position in AI"](https://graphite.io/five-percent/how-to-track-entity-position-in-ai) (Druck & Smith, white paper, 2026) — sequential sampling protocol; n=10 → 5.6% mean visibility error; 59% sample reduction vs flat n=135
- arxiv 2603.08924, "Quantifying Uncertainty in AI Visibility" (March 2026) — bootstrap confidence intervals, rank stability analysis, noise floor demonstration across Perplexity/SearchGPT/Gemini, 47 pages
- Indig, ["The Ghost Citation Problem"](https://www.growth-memo.com/p/the-ghost-citation-problem) (Apr 2026) — 3,981 domain appearances, 4 engines; 62% ghost-citation rate, Gemini/ChatGPT mention-vs-citation asymmetry, comparative content drives mentions ~30x
- Ahrefs, ["Why ChatGPT Cites One Page Over Another"](https://ahrefs.com/blog/why-chatgpt-cites-pages/) (Apr 2026) — 1.4M prompts; Reddit retrieval-vs-citation gap (1.93%)
- Profound, ["What AI Engines Actually Search For"](https://www.tryprofound.com/blog/what-ai-engines-actually-search-for) (Apr 2026) — ChatGPT 91% query uniqueness; weekly tracking cadence justified
- Ahrefs, ["AI Overview Top-10 Citation Update"](https://ahrefs.com/blog/ai-overview-citations-top-10/) (Mar 2026) — 76% → 37.9% top-10 share
- Seer / Search Engine Land, ["Google AI Overviews CTR Recovery"](https://searchengineland.com/google-ai-overviews-ctr-recovery-study-475566) (Apr 2026) — AIO CTR 1.3% → 2.4% Dec 2025 to Feb 2026; comparison vs transactional split
- LLMrefs, ChatGPT Ads in US responses report (Apr 2026) — ~20% of US responses contain ad placements
