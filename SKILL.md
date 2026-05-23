---
name: finance-ppt-from-excel
description: Create financial and operating-review PPTs from Excel workbooks, supporting documents, old decks, and progress tables. Use when the task is a financing report, business review, budget review, bank/channel progress report, management reporting deck, or any data-heavy PPT where numbers, units, tables, totals, pagination, and low-noise financial wording matter more than generic slide design. This skill is the primary workflow layer for finance decks. It should absorb data from Excel/documents, normalize financial rules, generate a report structure, and then optionally apply a visual output layer such as guizang-ppt-skill. Use grill-me style behavior to lock decisions when page structure, metric scope, or report emphasis is still unclear.
---

# Finance PPT From Excel

## What This Skill Does

Build a finance-style presentation from structured source material.

This skill is not a pure design skill and not a generic PPT maker. It exists to:

- read Excel and document sources
- identify total / segment / detail / progress tables
- normalize units, totals, precision, and display rules
- generate a management-report structure
- reduce noisy wording
- paginate detail-heavy pages safely
- output content that can later be rendered in HTML, PDF, or PPT

Use this skill as the **main workflow** for financial decks.

If the user also names a visual deck skill such as `guizang-ppt-skill`, do not let that visual skill drive the content logic. Finish the finance workflow first, then apply the visual layer second.

If the user also names `grill-me`, use its behavior as the decision-making mode:

- resolve structural ambiguity before polishing
- ask less when the answer is already discoverable from the workbook/files
- lock one branch of the decision tree before moving to the next

---

## Core Positioning

This skill has three layers:

1. `grill-me` layer
Purpose: lock scope, structure, deletions, emphasis, and report decisions

2. `finance-ppt-from-excel` layer
Purpose: transform Excel/documents into a finance-report content system

3. visual output layer such as `guizang-ppt-skill`
Purpose: render already-structured financial content into a styled deck

Important:

- `guizang-ppt-skill` is **not** the main logic engine for finance decks
- it is only the final visual skin
- many of its defaults must be overridden for finance readability

Read [references/guizang-finance-adaptation.md](references/guizang-finance-adaptation.md) before using a guizang-style output.

---

## Working Contract

Always follow this order:

1. lock the reporting task
2. inspect Excel/doc sources
3. build a data map
4. normalize financial display rules
5. propose or infer page structure
6. reduce wording noise
7. paginate detail pages
8. hand off to the output format layer

Never start from slide styling.

If the user already has a partially built deck, still re-check the source workbook before editing the deck.

---

## Step 1 · Lock The Reporting Task

Before making pages, lock these items:

- report topic
- audience
- usage scene
- output format
- whether the deck is mostly data presentation
- whether PDF and PPT outputs are needed

If the user does not specify clearly, assume:

- audience: internal management / operating review
- style: concise, low-noise, data-first
- output: at least one review format plus one editable format

For structure questions, prefer making a reasonable assumption from the workbook and current deck instead of asking broad open-ended questions.

Use `grill-me` style discipline:

- confirm the branch that changes slide count, section order, or the list of required projects
- do not stop on cosmetic questions too early

---

## Step 2 · Inspect Excel And Documents Before Designing

Read the workbook first.

Build a source map with four buckets:

1. total summary sheets
2. segment summary sheets
3. detail sheets
4. progress / blocker / action sheets

For each relevant sheet, identify:

- the reporting role of the sheet
- the header row
- numeric columns
- text progress columns
- columns suitable for page display
- columns that should stay in notes only

If documents or old decks exist:

- use them as wording / context aids
- do not let them override workbook facts unless explicitly instructed

If a progress table exists, prefer it over invented commentary.

---

## Step 3 · Build A Data Map

Create a working data map mentally or in notes before page building.

The data map must answer:

1. what is the total picture
2. what are the segment-level metrics
3. which tables produce detail pages
4. which items belong to next-month plan / pipeline / priority list
5. where the latest factual progress wording comes from

Typical finance buckets:

- target
- landed / realized
- month-added
- reserve / pipeline
- next-month plan
- owner
- current progress
- blocker
- action

Do not start styling until the map is stable.

---

## Step 4 · Normalize Financial Display Rules

Before making slides, normalize:

- units
- precision
- thousands separators
- totals
- percentage display
- special text values
- highlight rules

Default rules:

- amount unit: `万元` unless the user explicitly wants another unit
- amount precision: integer by default
- use thousands separators for displayed amounts
- every table must have `总计` when totals are meaningful
- special text values such as `AIC`, `待定`, `-` remain as text
- do not force non-numeric pipeline labels into numeric totals

If multiple units exist in the workbook, unify them before page writing.

Read [references/data-normalization.md](references/data-normalization.md).

---

## Step 5 · Generate The Report Structure

Use the workbook and the reporting topic to infer the page structure.

Default financial structure:

1. cover
2. total overview
3. segment overview
4. detail pages by channel / business block
5. next-month plan or key projects
6. blockers and actions

For financing reports, the preferred structure is:

1. financing overview
2. financing blocks / channels
3. channel details
4. next-month plan projects
5. blockers and actions

For operating reviews, prefer:

1. total KPIs
2. business segments
3. variance / anomaly page
4. next-month focus
5. actions

Read [references/page-structures.md](references/page-structures.md).

---

## Step 6 · Reduce Wording Noise

Finance decks should not sound like AI narration.

Remove, in this order:

1. prompt-like text
2. summary-sounding filler
3. explanatory long headlines
4. sentences that only repeat visible data
5. decorative English mini-headings unless required by the chosen style

Allowed copy types:

- titles
- data labels
- short factual notes
- progress statements
- action statements

For progress pages:

- prefer fact sentences
- prefer action sentences
- avoid vague evaluative language

Bad:

- 项目稳步推进，预计很快取得积极进展

Good:

- 盖章资料已整理，用印中
- 已提交总行审批，预计 2-3 周反馈

---

## Step 7 · Paginate Detail Pages Safely

When a detail page does not fit:

1. reduce row height
2. reduce font size
3. shorten column labels
4. if still not enough, paginate

Never:

- hide part of the detail set silently
- truncate rows
- force unreadable small type to keep one page

For all detail-heavy finance pages, completeness is higher priority than visual symmetry.

Read [references/detail-page-rules.md](references/detail-page-rules.md).

---

## Step 8 · Use Progress Tables As Fact Sources

If the workbook includes weekly updates, reserve details, pipeline notes, or project trackers:

- pull the latest valid progress from those tables
- only clean lightly for readability
- do not write fresh synthetic commentary unless the source is missing

Preferred order:

1. latest update column
2. prior update column if the latest is blank
3. blocker column
4. shortest conservative fallback wording

This is one of the biggest anti-AI-noise rules in the skill.

---

## Step 9 · Apply A Visual Output Layer

Only after the finance workflow is stable should you apply a visual layer.

Possible output layers:

- `guizang-ppt-skill`
- a standard business PPT style
- a minimal management-report HTML style

If using `guizang-ppt-skill`, first read:

- [references/guizang-finance-adaptation.md](references/guizang-finance-adaptation.md)

That file defines what must be overridden:

- typography rules for finance reading
- tabular number treatment
- table grammar
- page-type grammar
- wording rules
- unit / total / highlight conventions

Important:

Do not let guizang defaults control:

- numeric formatting
- unit handling
- table completeness
- pagination logic
- progress page language

---

## Step 10 · Output Deliverables

Default output recommendation:

- working source deck: HTML or editable PPT source
- review format: PDF

If collaboration or circulation is needed:

- also create PPTX

Typical mapping:

- HTML: best for iterative building
- PDF: best for viewing / sending
- PPTX: best for handoff / speaking / downstream editing

---

## Mandatory Quality Rules

The deck fails if any of these happen:

- mixed units without explicit explanation
- missing totals on meaningful tables
- no thousands separators where required
- detail pages truncated without pagination
- progress pages use vague AI-sounding summary text
- visual style overpowers readability
- guizang layout choices break finance clarity
- segment and total values do not reconcile

---

## Recommended File Reading Order

1. read this `SKILL.md`
2. read [references/data-normalization.md](references/data-normalization.md)
3. read [references/page-structures.md](references/page-structures.md)
4. read [references/detail-page-rules.md](references/detail-page-rules.md)
5. if using guizang output, read [references/guizang-finance-adaptation.md](references/guizang-finance-adaptation.md)

Do not load every reference file unless needed.

---

## Output Philosophy

This skill is a finance reporting engine first and a deck skill second.

Its priorities are:

1. correctness
2. structure
3. readability
4. completeness
5. style

When style and finance clarity conflict, finance clarity wins.

