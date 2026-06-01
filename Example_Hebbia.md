# Intelligence Brief: Hebbia

**Generated:** 2026-05-20
**URL:** https://www.hebbia.com/
**Meeting:** recruiting call with CEO George Sivulka

---

## Phase 1 — Company Overview

### What Is It?
Hebbia builds Matrix, an AI platform that lets knowledge workers at financial and legal firms query large private document sets — data rooms, fund documents, contracts, filings — in plain language and receive answers with source citations. The central bet is that Wall Street's information-processing problem is fundamentally a software problem, and that the firms that can analyze 50,000-page data rooms faster than their competitors win deals.

### Founders & Team
| Name           | Role          | Background                                                                                                                                                                                                                                                        |
| -------------- | ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| George Sivulka | Founder & CEO | Stanford (BS Math in 2.5 yrs with 4.0 GPA, MS Applied Physics, PhD EE — dropped out). Research scientist at NASA (2014–16), SLAC National Accelerator Lab (2017–18), BCG associate (2018), Wu Tsai Neurosciences Institute (2019–20). Founded Hebbia August 2020. |
| Aabhas Sharma  | CTO           | Joined October 2025                                                                                                                                                                                                                                               |
|                |               |                                                                                                                                                                                                                                                                   |

> **Educated guess:** The CTO hire as late as October 2025 (5 years after founding, at ~120 employees) suggests the engineering leadership structure was flat or built around Sivulka for a long time — now professionalizing.

**Team size:** ~147 as of March 2026 (per LeadIQ / multiple sources); was ~103 in 2024, ~123 in July 2025. Active EMEA expansion underway (VP EMEA hired February 2026).

**Advisors:** Eric Schmidt, Jerry Yang (also investors). No formal advisory board publicly listed.

### Funding
| Round | Amount | Date | Lead Investor |
|-------|--------|------|--------------|
| Seed | Undisclosed | 2020 | Peter Thiel, Floodgate |
| Series A | $30M | 2022 | Index Ventures |
| Series B | $130M | April 2024 | Andreessen Horowitz |

**Other investors:** Index Ventures (both rounds), GV (Google Ventures), Radical Ventures, Peter Thiel, Eric Schmidt, Jerry Yang

**Total raised:** $161M+

**Valuation:** $700M (post-money, Series B, April 2024)

**Official source:** Hebbia blog (Tier 1) — [hebbia.com/blog/hebbia-raises-usd130m-series-b](https://www.hebbia.com/blog/hebbia-raises-usd130m-series-b)

### Runway
> **Educated guess:** $161M raised at ~147 employees in NYC. At ~$25–35K/employee/month all-in (NYC rates, mix of engineers and domain experts) plus infrastructure and go-to-market, burn is roughly $4–6M/month. If the company is profitable (see Product section), the runway question may be moot — the more relevant question is whether they'll raise a Series C to accelerate growth before Harvey or Rogo gain more ground. No new funding disclosed since April 2024, which is now 25 months ago.

### Product
Matrix is Hebbia's flagship platform. Users upload document sets (PDFs, spreadsheets, presentations, data room contents) and run structured queries across all of them simultaneously — returning answers with source citations. The company describes a proprietary "ISD architecture" for complex reasoning tasks. Key metrics published on the company website (Tier 1): **$25T AUM** from using firms, **1,000+ use cases in production**, **2T+ tokens processed** by investors. The platform covers institutional investing, investment banking, professional services, and corporate finance. A 2025 acquisition of **FlashDocs** (AI slide deck generation from structured prompts) extended Matrix into the presentation delivery layer — the "last mile" of analysis workflows. In August 2025, Hebbia integrated GPT-5 through Microsoft Azure AI Foundry.

> **Educated guess:** $13M ARR with profitability at time of Series B (per TechCrunch, July 2024). Current ARR unknown but likely significantly higher given team growth from 103→147 and EMEA expansion.

### Key Risks
1. **No disclosed funding since April 2024** — 25+ months without a public round at a $700M valuation, while comparable AI companies (Harvey: $11B, AlphaSense: ~$4B) have raised at dramatically higher multiples. Either Hebbia is profitable and doesn't need to raise, or they're preparing a raise, or growth has plateaued.
2. **Harvey AI's rapid expansion** — Harvey went from $100M ARR (August 2025) to $190M ARR (January 2026) at an $11B valuation. Harvey is now actively moving into enterprise/finance use cases that directly overlap with Hebbia's legal and M&A workflows. Harvey has outpaced Hebbia on ARR velocity and funding scale.
3. **Revenue concentration** — 40%+ of the largest asset managers use Hebbia; if 2–3 anchor clients build in-house AI or switch, revenue concentration is an acute risk given ~$13M ARR baseline.

### Recruiting Framing
- **Founder quality signal:** Sivulka is a technically serious founder — Stanford quant background (Math/Physics/EE), built physical-world research tools at NASA and SLAC, spent a year at BCG understanding the domain, then dropped out of his PhD to build Hebbia. He has the rare combination of genuine research depth + enterprise distribution savvy. The early Peter Thiel + Index backing is a strong early signal.
- **Team composition:** ~147 people; mix of former bankers, consultants, and lawyers (domain experts) alongside engineers. The "Why I joined Hebbia" blog series shows a pattern of people joining from finance/law to build the tools they wished they'd had. CTO was only hired in Oct 2025 — engineering culture has likely been founder-led until recently.
- **Growth trajectory:** Active EMEA expansion (VP EMEA hired Feb 2026), Index Ventures career portal lists open engineering headcount, $25T AUM client base suggests strong enterprise traction. If a Series C comes, headcount growth will accelerate.
- **Culture signals:** Domain-first culture — they hire people who know the pain points firsthand. The company's blog emphasizes mission ("democratizing the intelligence of the world's best analyst") and urgency without the academic purity of SSI or the scale-first mentality of Harvey. Likely more commercial and execution-oriented than research labs.

---

## Phase 2 — Client & Persona Deep-Dive

### Who Buys This?
The primary buyer is a **Managing Director or Partner at a private equity or asset management firm** — specifically whoever owns the research and due diligence process. At law firms, it's a **Senior Partner or Director of Innovation** managing associate leverage. They care about: deal velocity, analyst output quality, and not getting embarrassed by a missed provision in a data room. Budget authority is typically $100K–$500K+ per team annually. They get promoted by closing more deals faster; they get fired by missing material facts that their competitors caught.

### What Do They Do Without This Product?
Without Matrix, the workflow is: junior analysts (2–4 associates) are assigned to read all documents in a data room, manually extract key terms into Excel trackers, and write summaries. A typical M&A due diligence involves 10,000–50,000 pages of documents over 3–6 weeks. Current tools include:
- Ctrl+F PDF search and Adobe Acrobat
- Kira Systems or Luminance (contract-specific clause extraction)
- iManage or NetDocuments (document management, not analysis)
- Generic GPT/Claude via copy-paste for individual docs
- Excel trackers with manually coded fields

Associates spend an estimated 60–80% of deal time on document review rather than analysis. The problem isn't reading speed — it's coverage: there's no guarantee every document was reviewed for every material provision.

### Where Does the Product Intervene?
Matrix inserts itself **between document ingestion and memo drafting** — the step where associates would otherwise spend weeks manually reading. Specifically: after documents are uploaded to a data room, before the investment committee memo is written. Matrix provides structured, citation-backed extraction across the entire document set simultaneously, replacing the "read everything and hope you didn't miss something" workflow.

### Pain Points
1. **Coverage gaps under time pressure** — Competitive processes compress due diligence to 2–3 weeks; a 30,000-page data room cannot be fully read by any human team in that window. Missing a change-of-control provision or environmental liability in an acquisition has cost firms hundreds of millions.
2. **Associate leverage** — Senior deal professionals spend disproportionate time managing document review grunt work rather than doing actual analysis. At $400K+ fully-loaded cost per senior associate, the ROI on automation is straightforward.
3. **Institutional memory loss** — Analysts rotate every 2 years; knowledge about past deals, past counterparties, and precedent terms lives in people's heads, not in searchable systems. Matrix can index historical deal documents and make them queryable.

### Named Clients or Pilots
The company's own website (Tier 1) confirms: **$25T AUM from using firms**, **40%+ of largest asset managers by AUM**.

> **Educated guess:** BlackRock, KKR, Carlyle, Centerview Partners, and MetLife are named in secondary reporting (FinanceFeeds, 2025) as active clients. These are plausible given the $25T AUM figure but have not been confirmed on Hebbia's own website or in a named press release.

A managing director quote appears on Hebbia's website (Tier 1): *"6x+ ROI on our investment with Hebbia."*

### What Gets Displaced?
- Junior analyst hours spent on document review (the most direct substitution)
- Contract review tools: Kira Systems, Luminance, Seal Software
- Basic document management / enterprise search: iManage, NetDocuments
- Ad hoc LLM use via ChatGPT/Claude (replaced by a governed, auditable platform)
- Law firm associate billing hours for due diligence review (longer-term displacement risk for law firm clients)

---

## Phase 3 — Competitive Landscape

### Direct Competitors

| Company    | Funding                                             | Positioning                                                                               | vs Hebbia                                                                                                                                                                      |
| ---------- | --------------------------------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Harvey AI  | $500M+ raised; $11B valuation (Mar 2026); $190M ARR | Legal AI agents for law firms and enterprise legal depts                                  | Harvey wins in billable-hour law firm workflows; expanding aggressively into M&A/enterprise; Hebbia wins in buy-side finance and PE; risk: Harvey is growing 15x faster on ARR |
| AlphaSense | ~$900M raised; ~$4B valuation                       | Public market intelligence: 10,000+ content sources (filings, earnings, broker research)  | AlphaSense wins on depth of public content library; Hebbia wins on private/proprietary document sets (data rooms, internal files) — different use case                         |
| Rogo       | Undisclosed (Coatue-backed); finance-specific       | IB workflow automation; acquired Subset (2025) for Excel model handling; LSEG partnership | Rogo wins on IB deliverables (memo generation, model rolling); Hebbia wins on PE/AM document breadth and enterprise scale                                                      |
| Glean      | ~$1B+ raised; $4.6B valuation                       | Horizontal enterprise AI search (Slack, Drive, Confluence, etc.)                          | Glean is infrastructure; Hebbia is vertical. Glean rarely competes head-to-head on finance-specific document analysis                                                          |
| Legora     | $5.6B valuation (April 2026)                        | European legal AI, expanding globally; direct Harvey rival                                | Legal-focused; not a primary Hebbia competitor today but competes for the same law firm budget                                                                                 |

### Differentiation Assessment

- **Claim:** *"The AI you were promised"* / multi-document synthesis across entire document sets
  **Assessment:** The multi-document synthesis angle is genuinely differentiated from single-doc Q&A tools and generic RAG setups. The "ISD architecture" claim for complex reasoning is on the website but not independently verified — treat as marketing until there's a published methodology.

- **Claim:** *"$25T AUM from using firms"* / *"40%+ of largest asset managers"*
  **Assessment:** Confirmed on company website (Tier 1). These are strong, specific, verifiable social proof numbers. If accurate, Hebbia has dominant penetration in the asset management vertical — the strongest signal of product-market fit in the brief.

- **Claim:** *"1,000+ use cases in production"*
  **Assessment:** Confirmed on company website (Tier 1). Suggests platform breadth beyond just due diligence — but "use cases" is a fuzzy metric. Doesn't tell you whether those are $5K pilots or $500K enterprise contracts.

### Genuine White Space
Hebbia occupies a real and specific niche: **multi-document synthesis across private, proprietary document sets at enterprise scale in high-stakes financial and legal workflows.** AlphaSense doesn't touch private documents. Harvey is law-firm-centric (billable hour leverage). Rogo is IB-deliverable-centric. No single well-funded competitor sits squarely in the PE/AM due diligence and research workflow at the same depth. The $25T AUM penetration confirms this isn't a hypothetical gap.

### Where It's Crowded
**Legal document analysis** — Harvey ($11B, $190M ARR, now expanding into enterprise) competes for the same M&A and transactional legal budget. Legora is also expanding. If law firms become the primary distribution channel for AI into corporate legal/finance, Hebbia's legal footprint is at risk. The shared a16z investment in both Hebbia and Harvey may create board-level tension or at minimum information asymmetry.

### Key Competitive Risk
**Harvey AI's velocity.** Harvey is at $190M ARR (Jan 2026) growing fast, $11B valuation, and explicitly expanding from law firms into enterprise customers — the exact buyer Hebbia serves. Hebbia's disclosed ARR (>$13M at Series B, April 2024) represents a 10–15x gap. If Harvey builds finance-specific features or acquires a Rogo-like asset, Hebbia faces a better-capitalized competitor with overlapping customer relationships, overlapping investors (a16z), and overlapping use cases. The next 12 months of Harvey's enterprise push is the thing to watch.
