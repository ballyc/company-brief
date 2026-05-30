# company-brief — Company Intelligence Brief

Generates a structured pre-meeting intelligence brief for a company.
Saves briefs to disk. Maintains a searchable JSON index.

## Usage

```
/company-brief <url> [options]

Options:
  --quick              Phase 1 only (company overview). ~90 seconds.
  --update             Re-run Phase 1 against existing brief, emit "Changes since [date]:" header.
  --meeting "<text>"   Meeting context. Adjusts brief emphasis. Default: "recruiting".

Examples:
  /company-brief https://unreasonablelabs.ai
  /company-brief https://unreasonablelabs.ai --quick
  /company-brief https://unreasonablelabs.ai --update
  /company-brief https://unreasonablelabs.ai --meeting "Series A investor diligence"
  /company-brief https://unreasonablelabs.ai --meeting "recruiting call with co-founder Yuan Cao"
```

---

## Step 0 — Parse Arguments

From the user's invocation, extract:

1. **URL** (required) — the company URL
2. **QUICK** — true if `--quick` is present
3. **UPDATE** — true if `--update` is present
4. **MEETING_CONTEXT** — text after `--meeting "..."`, defaults to `"recruiting call"`

Derive **MEETING_TYPE** from MEETING_CONTEXT:
- Contains "investor", "fund", "diligence", "vc" → `investor`
- Contains "bd", "business development", "partner", "partnership" → `bd`
- Everything else → `recruiting`

---

## Step 1 — Derive Slug and Set Up Paths

### Slug algorithm

From the URL:
1. Strip protocol (`https://`, `http://`)
2. Strip `www.`
3. Take the hostname (everything before the first `/`)
4. Strip the TLD — the final `.something`: `unreasonablelabs.ai` → `unreasonablelabs`
5. Apply word segmentation using your best judgment to produce a readable slug:
   - `unreasonablelabs` → `unreasonable-labs`
   - `isomorphiclabs` → `isomorphic-labs`
   - `futurehouse` → `futurehouse`
   - `anthropic` → `anthropic`
   - `openai` → `openai`
6. Lowercase, replace any remaining non-alphanumeric characters with `-`

**Collision handling:** If the slug already exists in the index with a DIFFERENT URL, append `-2` (then `-3`, etc.) until the slug is unique.

### Paths

```
BRIEFS_DIR  = ~/research-briefs
SLUG_DIR    = ~/research-briefs/{slug}
INDEX_FILE  = ~/research-briefs/index.json
TODAY       = current date, YYYY-MM-DD
BRIEF_FILE  = ~/research-briefs/{slug}/{TODAY}.md
```

Run:
```bash
mkdir -p ~/research-briefs/{slug}
```

---

## Step 2 — Index Check

Read `~/research-briefs/index.json`.
If the file does not exist, treat it as: `{"version": "1.0", "briefs": []}`.

Find any existing entry where `slug` matches.

**If `--update` AND no existing entry:**
```
ERROR: No prior brief for '{slug}'.
Run without --update to create the first brief:
  /company-brief {url}
```
Stop. Do not continue.

**If `--update` AND existing entry found:**
- Read the file at the entry's `brief_path` (the most recent one if multiple versions exist)
- Store as `OLD_BRIEF_CONTENT`
- Store entry's `date` as `LAST_BRIEF_DATE`

---

## SOURCE DISCIPLINE RULES — Read Before Every Phase

These rules apply to every single claim in the brief. No exceptions.

### Confirmed (write normally, no label)
A fact is confirmed ONLY if found verbatim on:
- **Tier 1:** Company's own website, official company press release, official company blog
- **Tier 2:** Crunchbase company profile, PitchBook entry, or a named investor's official announcement (e.g., investor blog post announcing the deal)

### Educated Guess (MUST label)
Label ANY fact that is:
- From secondary news coverage (TechCrunch, VentureBeat, HPCwire, Bloomberg, etc.)
- Calculated or estimated by you (e.g., runway = funding / estimated burn)
- Stated without direct company attribution
- Your own synthesis, inference, or extrapolation

**Label format:** Prefix the claim with `> **Educated guess:** `

**Examples:**
```markdown
The company raised $13.5M in March 2026, led by Playground Global.
← No label. Source: BusinessWire press release (Tier 1).

> **Educated guess:** At ~8-10 employees in Palo Alto with significant compute costs,
> burn is estimated at $600K–$1M/month, implying 12–20 months of runway.
← Labeled. Calculation based on team size + location, not public data.
```

**When in doubt, label it.** A labeled guess that's later confirmed is harmless. An unlabeled wrong fact destroys trust before a high-stakes meeting.

---

## CONTROLLED THEME VOCABULARY

Pick **3–7 tags** from this list ONLY. Do not invent new tags.

**Stage:** `pre-seed` `seed` `series-a` `series-b` `growth-stage` `public` `profitable`

**Sector:** `ai-science` `deep-tech` `pharma` `biotech` `materials-science` `energy-transition` `climate-tech` `semiconductors` `robotics` `fintech` `healthtech` `edtech` `developer-tools` `enterprise-saas` `infrastructure` `data-analytics` `consumer` `defense` `security-cybersecurity` `open-source`

**Business model:** `b2b` `b2c` `marketplace` `research-platform` `hardware`

**Company characteristics:** `recently-launched` `stealth-or-emerging` `research-spinout` `technical-founders` `phd-led-team` `recently-funded` `hiring-aggressively` `small-team` `mid-size-team`

---

## Phase 1 — Company Intelligence

**Always runs** (both default and `--quick` mode).

### Searches (run ALL in parallel — one turn, multiple WebSearch calls)

1. `site:{domain} about team` — company About/Team page
2. `"{company name}" funding raised investors 2024 2025 2026` — funding data
3. `"{company name}" launch announcement press release` — official announcements
4. `"{company name}" product 2025 2026 crunchbase` — recent product/company news

If WebSearch results are thin, visit the company homepage directly with WebFetch.

### Phase 1 Output Template

```markdown
# Intelligence Brief: {Company Name}

**Generated:** {TODAY}
**URL:** {url}
**Meeting:** {MEETING_CONTEXT}

---

## Phase 1 — Company Overview

### What Is It?
{1–2 sentence plain-English description of the product and core thesis.
What does it do? Who does it do it for? What's the central bet?}

### Founders & Team
| Name | Role | Background |
|------|------|-----------|
| {Name} | {Title} | {Prior company, credential, relevant signal} |

**Team size:** {N} (or: `> **Educated guess:** ~{N} based on LinkedIn/team page`)
**Advisors:** {Names and why they matter — or "None publicly listed"}

### Funding
| Round | Amount | Date | Lead Investor |
|-------|--------|------|--------------|
| {Series X} | ${Xm} | {month year} | {investor} |

**Other investors:** {names}
**Total raised:** ${Xm}

### Runway
> **Educated guess:** {Calculation with reasoning. Example: "$13.5M raised, team of ~8 in Palo
> Alto with significant compute spend → estimated burn $600K–$1M/month → 12–20 months runway.
> Series A likely needed by [estimated date]."}

### Product
{2–4 sentences on what the product actually does. Technical if relevant.
Not marketing copy — concrete description of what a user actually does with it.}

### Key Risks
1. {Risk — specific, not generic. "Pre-revenue" is a risk. "Highly competitive space" is not.}
2. {Risk}
3. {Risk}
```

**Append recruiting/investor/bd framing block based on MEETING_TYPE:**

If `recruiting`:
```markdown
### Recruiting Framing
- **Founder quality signal:** {Assessment of founder background, domain expertise, credibility}
- **Team composition:** {Technical depth? PhD-heavy? Previous startup experience?}
- **Growth trajectory:** {Hiring aggressively? Just funded? Signs of product traction?}
- **Culture signals:** {What can you infer about how they work from the team page, blog, job postings?}
```

If `investor`:
```markdown
### Investor Framing
- **Market size:** {TAM estimate with reasoning — label if educated guess}
- **Moat assessment:** {What's defensible? What's not?}
- **Revenue model:** {How do they make money? Confirmed or educated guess?}
- **Burn & runway:** {See Runway section above}
- **Key diligence question:** {The one thing you'd want to verify before investing}
```

If `bd`:
```markdown
### BD Framing
- **Client profile:** {Who are their clients? Named if possible, inferred otherwise}
- **Pricing signals:** {Any public pricing? Typical deal size — educated guess if unknown}
- **Partnership potential:** {What would a partnership look like? Complementary or competitive?}
- **Decision maker:** {Who would sign a BD deal? CEO? VP Sales? VP Product?}
```

### Save Phase 1 immediately

Write the Phase 1 content to `~/research-briefs/{slug}/{TODAY}.md` now.
Do not wait for Phases 2–3. If the process fails later, Phase 1 is already saved.

**If `--quick` mode:** Stop here. Skip to "Update Index."

---

## Phase 2 — Client & Persona Deep-Dive

**Runs by default. Skipped with `--quick`.**

### Searches (run ALL in parallel)

1. `"{company name}" customers clients case study pilot` — named client evidence
2. `{main sector} R&D workflow pain points 2024 2025 2026` — industry pain point research
3. `{main sector} software tools used by {target persona role}` — what they use today

### Phase 2 Output Template

```markdown
## Phase 2 — Client & Persona Deep-Dive

### Who Buys This?
{Real buyer role. Not "enterprises" — a person. Title, department, budget authority.
What gets them promoted? What gets them fired? What do they care about in a vendor?}

### What Do They Do Without This Product?
{Concrete current workflow. Name specific tools if known. How many hours per week?
What gets missed or done poorly because the product doesn't exist?}

### Where Does the Product Intervene?
{The specific step in the workflow where {company} replaces or augments the existing process.
Be specific: "between step 2 (literature review) and step 3 (hypothesis formation)"}

### Pain Points
1. {Pain — specific, quantified if possible}
2. {Pain}
3. {Pain}

### Named Clients or Pilots
{List any named clients, pilot partners, or case studies with source.}
{If none public:}
> **Educated guess:** No named clients publicly disclosed as of {TODAY}.
> Company mentions pilots in {sector(s) mentioned}.

### What Gets Displaced?
{What tools/services/processes does this replace? What do users stop paying for?
What internal headcount becomes unnecessary?}
```

### Save Phase 2 immediately

Append Phase 2 content to `~/research-briefs/{slug}/{TODAY}.md`.

---

## Phase 3 — Competitive Landscape

**Runs by default. Skipped with `--quick`.**

### Searches (run ALL in parallel)

1. `"{company name}" competitors alternatives comparison` — competitive landscape
2. `{sector} AI startup {year} funding competitive` — recent entrants and funding
3. `{main competitor if identifiable} vs "{company name}"` — direct comparison evidence

### Phase 3 Output Template

```markdown
## Phase 3 — Competitive Landscape

### Direct Competitors

| Company | Funding | Positioning | vs {Company Name} |
|---------|---------|-------------|-------------------|
| {name} | ${Xm} | {one line} | {key difference — who wins at what} |

### Differentiation Assessment
For each major claim {company} makes about being different:

- **Claim:** "{their differentiation claim, verbatim from their site}"
  **Assessment:** {Is this real and defensible, or is it marketing?
  Who else makes this claim? What would it take to verify it?}

### Genuine White Space
{What gap do they fill that no well-funded competitor currently occupies?
Be honest — if the white space is narrow, say so.}

### Where It's Crowded
{Where better-funded or more established players are already competing.
Who has the advantage there and why?}

### Key Competitive Risk
{The one competitor, business model shift, or market dynamic most likely to threaten them.
Not generic "big tech could enter" — something specific.}
```

### Save Phase 3 immediately

Append Phase 3 content to `~/research-briefs/{slug}/{TODAY}.md`.

---

## --update Mode: Changes Section

If UPDATE mode, prepend this section to the brief BEFORE Phase 1 content:

```markdown
## Changes Since {LAST_BRIEF_DATE}

*(Phase 1 re-run on {TODAY}. Phases 2–3 carried forward from {LAST_BRIEF_DATE}.)*

### What's New
- {Change 1 — specific, with source tier}
- {Change 2}
{If nothing material changed:}
- No material changes detected in company overview, funding, or team since {LAST_BRIEF_DATE}.

> **Educated guess:** {Any probable-but-unconfirmed changes you noticed, e.g., new job postings
> suggesting a product pivot, or LinkedIn updates suggesting team growth}

---
```

Then write the updated Phase 1 content.
Then append: `---\n## Phases 2 & 3 (from {LAST_BRIEF_DATE})\n` followed by the Phase 2 and Phase 3 content from `OLD_BRIEF_CONTENT` verbatim.

---

## Update Index

Read `~/research-briefs/index.json`. If it doesn't exist, start with:
```json
{"version": "1.0", "briefs": []}
```

### Select themes (3–7 tags from the controlled vocabulary above)

Based on everything you've learned, pick the most accurate tags. Do not pick more than 7.

### For a new company (no existing entry): append this object to the `briefs` array:

```json
{
  "slug": "{slug}",
  "company": "{Company Name}",
  "url": "{url}",
  "date": "{TODAY}",
  "meeting_type": "{MEETING_TYPE}",
  "phases_run": [1, 2, 3],
  "themes": ["{tag1}", "{tag2}"],
  "funding_stage": "{stage-tag}",
  "brief_path": "~/research-briefs/{slug}/{TODAY}.md",
  "version": 1
}
```

Use `[1]` for `phases_run` if `--quick` mode was used.

### For an existing company (re-run or --update): add a new entry preserving the old one:

Add a new entry with the same slug, today's date, and `"version": {previous_version + 1}`.
Keep the old entry in the array — history is preserved.

Write the updated JSON back to `~/research-briefs/index.json`.

---

## Completion Report

Print:

```
Brief saved: ~/research-briefs/{slug}/{TODAY}.md
Index: ~/research-briefs/index.json ({N} total companies)
Phases: {Phase 1 only / Phases 1–2 / Phases 1–3}
Meeting: {MEETING_CONTEXT}
Themes: {tag1}, {tag2}, ...
Funding stage: {stage}
```

If `--update` mode, also print:
```
Previous brief: {LAST_BRIEF_DATE}
Changes section: included
```

---

## Querying the Index

The index is plain JSON. Query examples:
```bash
# All companies researched
jq '.briefs[] | {company, date, meeting_type, funding_stage}' ~/research-briefs/index.json

# All seed-stage companies
jq '.briefs[] | select(.funding_stage == "seed") | .company' ~/research-briefs/index.json

# All companies with a specific theme
jq '.briefs[] | select(.themes[] == "ai-science") | {company, date}' ~/research-briefs/index.json

# Most recently researched
jq '.briefs | sort_by(.date) | reverse | .[0:5] | .[] | {company, date}' ~/research-briefs/index.json
```
