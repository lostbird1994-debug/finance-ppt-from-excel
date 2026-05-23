# Guizang Finance Adaptation

`guizang-ppt-skill` is a visual style layer, not a finance reporting logic layer.

Use this file when applying guizang styling to financial decks.

## What Guizang Gives You

- editorial HTML deck structure
- strong serif title language
- mono metadata
- hero / divider rhythm
- magazine-like pacing

## What Must Be Overridden For Finance

### 1. Typography

- keep serif titles
- switch tables and numeric content to tabular-friendly numerals
- do not let decorative type choices reduce numeric comparability

### 2. Numeric Display

- always enforce thousands separators
- always enforce the chosen reporting unit
- preserve meaningful totals

### 3. Tables

- finance tables need explicit headers, totals, compact spacing, and pagination
- do not reuse loose editorial cards when a table is the correct proof object

### 4. Page Types

Financial decks need custom page grammars:

- overview page
- segment summary page
- detail table page
- next-month plan page
- blockers and actions page

Do not rely only on generic guizang layouts.

### 5. Wording

- remove speech-like lead paragraphs when they add no value
- remove decorative mini-summaries
- use factual short notes instead of essay copy

### 6. Highlight Logic

Use highlight by finance meaning, not only by aesthetics.

Recommended:

- target = red
- next-month plan = yellow

## Best Use Pattern

Correct order:

1. finance workflow skill structures the content
2. finance rules normalize the data
3. guizang visual language is applied to the stable content

Wrong order:

1. guizang layout first
2. finance content stuffed into it later

That usually creates a pretty but less readable finance deck.

