## What is it

A single Claude Code skill (`/company-brief`) that generates structured pre-meeting intelligence briefs for companies. Saved and indexed.

**For whom:** people who think like **investors** or **founders**, doing research on companies for their **personal use cases** (e.g. business development, investment, recruiting). **What for:** instant signal-over-noise search.

The skill executes in a fixed 8-step pipeline. See [`CLAUDE.md`](https://github.com/ballyc/company-brief/blob/main/CLAUDE.md) or [`SKILL.md`](https://github.com/ballyc/company-brief/blob/main/SKILL.md) for details (e.g. skill architecture, design constraints,...).

---

## What's in a brief

Each full brief contains three phases:

1. **Company overview** — product, founders credentials, team, funding, runway, key risks, and a meeting-specific framing block (recruiting / investor / BD).
2. **Client & persona deep-dive** — who buys it, their current workflow, where the product intervenes, pain points, named clients, what gets displaced.
3. **Competitive landscape** — direct competitors, differentiation assessment, genuine white space, where it's crowded, and the key competitive risk.

Every claim follows a strict source discipline: facts confirmed on the company's own site, an official press release, Crunchbase/PitchBook, or a named investor announcement are stated plainly; everything else — secondary news, calculations, inferences — is explicitly labeled `> **Educated guess:**`.

---

## How it works

**Input:** a single string in Claude Code — `/company-brief {company URL} --meeting "{context}"`.

**Process:** Claude Code reads `SKILL.md` and follows it, using its built-in **web search**, **web fetch**, and **file** tools to research the company, then writes the brief and updates an index. No API keys, no database, no external dependencies.

**Output:** a company brief in Markdown — stored, indexed, and editable.

**Storage:** briefs are read, written, indexed, and edited inside a dedicated local library at `~/research-briefs`.

**Reading:** open `~/research-briefs` as a vault in [Obsidian](https://obsidian.md) to read briefs cleanly.

---

## Installation

### Prerequisites
- [Claude Code](https://docs.claude.com/en/docs/claude-code) installed and signed in (Claude Pro, Max, Team, or Enterprise account).
- That's it. Web search, web fetch, and file writing are built into Claude Code already.

### Install (1 minute)

Clone the repo into Claude Code's skills folder:

```bash
git clone https://github.com/ballyc/company-brief.git ~/.claude/skills/company-brief
```

Restart Claude Code, you're ready.

---
## How to use it

In Claude Code, type:

```
/company-brief https://example.com --meeting "recruiting call with the CEO"
```

| Flag | Effect |
|------|--------|
| _(none)_ | Full brief — all 3 phases (~3 min) |
| `--quick` | Phase 1 only, company overview (~90 sec) |
| `--update` | Re-run against an existing brief; outputs a "Changes since [date]" header |
| `--meeting "..."` | Sets the angle — `recruiting`, `investor`, or `bd`, inferred from the text |

**Examples:**

```
/company-brief https://unreasonablelabs.ai --meeting "catchup call with co-founder Markus Buehler"
/company-brief https://unreasonablelabs.ai --meeting "Series A investor diligence"
/company-brief https://unreasonablelabs.ai --quick
/company-brief https://unreasonablelabs.ai --update
```
---

### Output

On the first run, the skill creates the `~/research-briefs/` library and `index.json` automatically. Each brief saves to `~/research-briefs/{company}/{date}.md`, and each run appends an entry to `~/research-briefs/index.json` — the searchable log of every company you've briefed.

Query the index with `jq`:

```bash
# All companies researched
jq '.briefs[] | {company, date, meeting_type, funding_stage}' ~/research-briefs/index.json

# All companies with a specific theme
jq '.briefs[] | select(.themes[] == "enterprise-saas") | {company, date}' ~/research-briefs/index.json
```

---


## ## ROI:

| Scenario        | Process Time | Workflow                                                                   |
| :-------------- | :----------- | :------------------------------------------------------------------------- |
| manual research | 60min        | back-to-back prompting with LLMs + parallel tabs search, stays in my head, forget it after a few days. |
| Tool use        | 4 min        | one brief generated in seconds. Saved and indexed.                         |

That a 15x multiple reclaimed for strategic thinking prep.

## Status
Active.
See [`example/Eleven Labs.md`](https://github.com/ballyc/company-brief/blob/main/Example/Eleven Labs.md) for a sample company brief generated with this skill.