# finance-ppt-from-excel

An open skill for turning Excel workbooks and supporting documents into financial PPTs.

This skill is designed for:

- financing reports
- operating reviews
- budget reviews
- bank / channel progress decks
- management reporting decks
- any data-heavy PPT where units, tables, totals, pagination, and low-noise wording matter more than generic slide design

## What It Does

This skill works as the main workflow layer for finance decks:

1. reads Excel and document sources
2. identifies total / segment / detail / progress tables
3. normalizes units, precision, totals, and numeric formatting
4. generates a finance-report page structure
5. reduces noisy or AI-sounding wording
6. paginates detail-heavy pages safely
7. hands off to a visual output layer such as `guizang-ppt-skill`

## Positioning

This project treats a financial presentation as a three-layer system:

1. `grill-me`
   Decision-locking layer for narrowing structure, scope, deletions, and emphasis

2. `finance-ppt-from-excel`
   Content and workflow layer for converting Excel/documents into a financial report system

3. Visual output layer such as `guizang-ppt-skill`
   Styling layer for rendering the already-structured content

Important:

- `guizang-ppt-skill` is not used here as the main finance logic engine
- it is treated as a visual skin that must be adapted for finance readability

## Repository Structure

```text
finance-ppt-from-excel/
├── SKILL.md
├── README.md
├── LICENSE
└── references/
    ├── data-normalization.md
    ├── detail-page-rules.md
    ├── guizang-finance-adaptation.md
    └── page-structures.md
```

## Included References

- `data-normalization.md`
  Financial display rules for units, separators, totals, precision, and special text values

- `page-structures.md`
  Default page structures for financing and operating-review decks

- `detail-page-rules.md`
  Pagination and readability rules for detail-heavy finance pages

- `guizang-finance-adaptation.md`
  Rules for adapting `guizang-ppt-skill` into a finance-compatible output layer

## Recommended Usage

Use this skill when the deck should be driven by data structure first, not visual style first.

Recommended sequence:

1. lock the reporting task
2. inspect the workbook and documents
3. build a data map
4. normalize the financial display rules
5. generate the page structure
6. reduce wording noise
7. paginate detail pages
8. apply a visual output layer
9. export HTML / PDF / PPT as needed

## License

MIT

