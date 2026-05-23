# Data Normalization

Use these rules before slide writing.

## Unit Rules

- Default amount unit: `万元`
- If the workbook mixes `元 / 万元 / 亿元`, normalize to one visible reporting unit
- If the user explicitly wants `亿元`, convert consistently and note precision rules

## Precision Rules

- Amounts: integer by default
- Rates / percentages: preserve meaningful precision, usually 1-2 decimals
- For very large summary numbers, do not show noisy decimals unless required

## Formatting Rules

- Use thousands separators on displayed amounts
- Keep text placeholders such as `AIC`, `待定`, `-` as text
- Do not convert text placeholders into zero

## Totals

- Every meaningful finance table should have `总计`
- Totals may use business totals from the source workbook rather than displayed-row arithmetic if the workbook’s reporting logic requires it
- If text values such as `AIC` appear in numeric columns, exclude them from numeric totals

## Highlight Rules

Recommended default:

- `目标` = red highlight
- `下月计划` = yellow highlight

Apply only to high-signal pages, not everywhere.

