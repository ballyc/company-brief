## What is it

A single Claude Code skill that generates structured pre-meeting intelligence briefs on companies — saved, indexed, and built for people who think like investors or founders.

**For whom:** anyone doing company research for their own high-stakes use cases — recruiting, business development, investment.
**What for:** instant signal-over-noise. One command instead of 60 minutes of parallel tabs.

**See a full example:** [`Example/Elevenlabs.md`](https://github.com/ballyc/company-brief/blob/main/Example/Elevenlabs.md) — the output speaks for itself.

---

## What's in a brief

Three phases, each written to disk immediately so partial output is never lost on failure:

1. **Company overview** — product thesis, founders' credentials, funding, runway estimate, key risks, and a meeting-specific framing block (recruiting / investor / BD).
2. **Client & persona deep-dive** — who buys it, their current workflow, where the product intervenes, pain points, named clients, what gets displaced.
3. **Competitive landscape** — direct competitors, differentiation assessment, genuine white space, where it's crowded, key competitive risk.

### Source discipline

Every factual claim is labeled at the point of writing:

- **Confirmed** — sourced from the company's own website, an official press release, Crunchbase/PitchBook, or a named investor announcement. Stated plainly.
- **`> **Educated guess:**`** — secondary news coverage, calculations, inferences. Explicitly flagged inline.

The reason: an unlabeled wrong fact destroys trust before a high-stakes meeting. A labeled guess that turns out to be right is harmless. The discipline is baked into the prompt so it can't be quietly skipped under time pressure.

---

## How it works

**Input:** a single string in Claude Code — `/company-brief {company URL} --meeting "{context}"`.

**Process:** Claude Code reads `SKILL.md` and follows it, using its built-in **web search**, **web fetch**, and **file** tools to research the company, then writes the brief and updates an index. No API keys, no database, no external dependencies.

**Output:** a structured Markdown brief — stored, indexed, and editable.

**Storage:** briefs live in a dedicated local library at `~/research-briefs`.

**Reading:** open `~/research-briefs` as a vault in [Obsidian](https://obsidian.md) to read briefs cleanly.

---

## Installation

### Prerequisites
- [Claude Code](https://docs.claude.com/en/docs/claude-code) installed and signed in (Claude Pro, Max, Team, or Enterprise account).
- That's it. Web search, web fetch, and file writing are built into Claude Code already.

### Install (1 minute)

```bash
git clone https://github.com/ballyc/company-brief.git ~/.claude/skills/company-brief
```

Restart Claude Code, you're ready.

---

## How to use it

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

## Output

On the first run, the skill creates the `~/research-briefs/` library and `index.json` automatically. Each brief saves to `~/research-briefs/{company}/{date}.md`, and each run appends an entry to `~/research-briefs/index.json` — a searchable log of every company you've briefed.

The index is plain JSON — queryable with `jq` by date, funding stage, meeting type, or theme tags.

---

## ROI

| Scenario | Time | Workflow |
|:---------|:-----|:---------|
| Manual research | ~60 min | Back-to-back LLM prompting + parallel tab search. Stays in your head, forgotten after a few days. |
| This skill | ~4 min | One command. Saved, indexed, retrievable. |

15x faster. The reclaimed time goes to actual thinking, not information gathering.

---

## Status

Active.
The working loop: use the skill; notice what's off, tighten the instruction. To tighten: list it under the skill.md's *Gotcha section*.
