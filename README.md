## What it does:

**/company-brief** : researches a company across 3 layers of depth, separating facts from educated guesses, and saves it to a searchable library.

**For whom:** people who think like **investors** or **founders**, doing research on companies for their **personal use cases** (e.g. business development, investment, recruiting). **Solve for:** Signal over noise.

## ## How it does:

**INPUT**: Simple **String** in Claude code: "/company-brief {company website URL}" - "meeting with CEO {name of CEO}". 
**BACK-END PROCESS**: **Autogenerates** company brief, **saves** it to `~/research-briefs/{company name}/{date}.md`; **log it in** a JSON index.
**OUTPUT**: company brief in Md format. Stored, indexed, editable.
**Storage**: read, write, index, edit; directly inside a **dedicated local library** `~/research-briefs.
**User interface:** readable cleanly with **Obsidian**; vault pointed to that library.

## ## ROI:

| Scenario        | Process Time | Workflow                                                                   |
| :-------------- | :----------- | :------------------------------------------------------------------------- |
| manual research | 60min        | back-to-back prompting with LLMs + parallel tabs search, stays in my head. |
| Tool use        | 4 min        | one brief generated in seconds. Saved and indexed.                         |

**Capacity unlocked**: 15x.

## Status
Active.
See [`example/Hebbia.md`](https://github.com/ballyc/company-brief/blob/main/Example/Hebbia.md) for a sample company brief generated with this skill.