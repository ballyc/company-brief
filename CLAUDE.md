# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

A single Claude Code skill (`/company-brief`) that generates structured pre-meeting intelligence briefs for companies. The entire skill logic lives in `SKILL.md`. `Example/Hebbia.md` is a reference output showing the expected brief format and quality bar.

## Skill Architecture

The skill executes in a fixed pipeline:

1. **Parse args** — extract URL, `--quick`, `--update`, `--meeting` flags
2. **Slug + path derivation** — generates a filesystem-safe slug from the URL, sets `~/research-briefs/{slug}/{TODAY}.md` as the output path
3. **Index check** — reads/writes `~/research-briefs/index.json`; `--update` requires a pre-existing entry
4. **Phase 1** (always) — parallel web searches → Company Overview, Founders, Funding, Runway, Product, Key Risks + meeting-type framing block → saved immediately
5. **Phase 2** (skipped with `--quick`) — Client & Persona Deep-Dive → appended immediately
6. **Phase 3** (skipped with `--quick`) — Competitive Landscape → appended immediately
7. **Index update** — upserts entry in `~/research-briefs/index.json`
8. **Completion report** — prints summary to console

Each phase saves to disk before the next phase runs, so partial output is preserved on failure.

## Key Design Constraints

**Source discipline:** Every factual claim must be labeled as either Confirmed (from company website, official press release, Crunchbase/PitchBook) or `> **Educated guess:**` (secondary sources, calculations, inference). This is the core quality invariant — never relax it.

**Controlled theme vocabulary:** Tags in the index are drawn from a fixed list in `SKILL.md`. Do not add new tags without updating the vocabulary section.

**`--update` mode:** Re-runs Phase 1 only, prepends a "Changes Since {date}" diff section, then appends old Phases 2–3 verbatim from the previous brief. It errors (does not create a new entry) if no prior brief exists.

## Output Storage

- Briefs: `~/research-briefs/{slug}/{YYYY-MM-DD}.md`
- Index: `~/research-briefs/index.json` — one entry per company per run; history is preserved (old entries are never deleted)
- Multiple runs of the same company produce versioned entries (`"version": 1`, `"version": 2`, …) in the same `briefs` array

## Querying the Index

```bash
# All companies
jq '.briefs[] | {company, date, meeting_type, funding_stage}' ~/research-briefs/index.json

# Filter by theme
jq '.briefs[] | select(.themes[] == "ai-science") | {company, date}' ~/research-briefs/index.json

# Most recent 5
jq '.briefs | sort_by(.date) | reverse | .[0:5] | .[] | {company, date}' ~/research-briefs/index.json
```

## Editing the Skill

`SKILL.md` is the only file that defines behavior. Changes to section ordering, output templates, or phase logic all live there. The `Example/Eleven Labs.md` file is a static reference — update it manually when the output format changes significantly.
