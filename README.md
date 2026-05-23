# finance-ppt-from-excel

中文｜English

一个把 Excel 工作簿、配套文档、旧版汇报材料转成财务风格 PPT 的开源 skill。它不是泛用型 PPT 美化器，而是一套更贴近融资汇报、经营分析、预算复盘、银行渠道进展汇报的内容工作流。

An open skill for turning Excel workbooks, supporting documents, and legacy reporting materials into finance-style presentation decks. It is not a generic slide beautifier, but a workflow designed for financing reports, operating reviews, budget reviews, and bank/channel progress decks.

---

## Overview｜项目概览

这个项目解决的是“财务 PPT 不是普通 PPT”这个问题。

很多设计型 skill 擅长做风格化页面，但财务汇报真正难的是：

- 先把 Excel 里的总表、分类表、明细表、进展表读清楚
- 统一金额单位、千分位、精度和总计口径
- 决定哪些数据适合做总览，哪些必须分页做明细
- 把“像提示词”的文案和 AI 总结腔去掉
- 最后才进入视觉包装

This project exists because financial decks are not the same as generic slide decks.

Design-oriented skills are often strong at styling, but finance decks usually require:

- reading total, segment, detail, and progress sheets correctly
- normalizing units, separators, precision, and totals
- deciding what belongs in summary slides vs. detail pages
- removing prompt-like or AI-sounding wording
- applying visual styling only after the reporting logic is stable

---

## What This Skill Is For｜适用场景

适合以下类型的汇报：

- 融资情况汇报
- 经营分析汇报
- 预算复盘
- 银行 / 渠道进展汇报
- 管理层经营汇报
- 任何“数据密度高、表格多、口径严、需要低噪音文案”的 PPT

Typical use cases:

- financing reports
- operating reviews
- budget reviews
- bank or channel progress decks
- management reporting decks
- any data-heavy PPT where numbers, tables, totals, pagination, and low-noise wording matter more than generic slide design

---

## Why This Exists｜为什么要单独做这个 Skill

`guizang-ppt-skill` 这类视觉 skill 很适合观点型、演讲型、杂志感页面，但并不天然适合财务汇报。

财务 PPT 通常还需要额外规则：

- 金额默认统一到 `万元`
- 数字按千分位展示
- 表格需要 `总计`
- 明细过长时要自动分页
- 进展文案以事实和动作表达为主
- 表格优先，不强行卡片化

`guizang-ppt-skill` and similar visual skills are excellent for editorial, talk-driven, and magazine-like slides, but finance reporting needs extra rules:

- amounts usually normalized to `万元`
- thousands separators for displayed numbers
- explicit `总计` rows in tables
- safe pagination for long detail pages
- factual progress and action wording
- table-first presentation where needed

---

## Core Positioning｜项目定位

这个项目把财务 PPT 拆成三层：

1. `grill-me`
   负责锁定范围、结构、删页、重点和决策分支

2. `finance-ppt-from-excel`
   负责把 Excel / 文档转成财务汇报内容系统

3. 视觉输出层，例如 `guizang-ppt-skill`
   负责把已经结构化好的内容渲染成 HTML / PDF / PPT 风格成品

This project treats a finance deck as a three-layer system:

1. `grill-me`
   decision-locking layer for scope, structure, deletions, and emphasis

2. `finance-ppt-from-excel`
   workflow layer for converting Excel and documents into a finance reporting system

3. visual output layer such as `guizang-ppt-skill`
   rendering layer for turning structured content into a styled deliverable

重要说明｜Important:

- `finance-ppt-from-excel` 才是主工作流
- `guizang-ppt-skill` 在这里不是主逻辑引擎
- 它只负责最后一层视觉输出，而且必须做财务化改写

- `finance-ppt-from-excel` is the main workflow layer
- `guizang-ppt-skill` is not the main finance logic engine here
- it should be used only as the final visual layer, after finance-specific adaptation

---

## Workflow｜推荐流程

推荐顺序：

1. 锁定汇报任务
2. 检查 workbook 和配套文档
3. 建立数据映射
4. 统一财务展示规则
5. 生成页面结构
6. 做文案降噪
7. 对明细页分页
8. 最后再贴视觉风格
9. 导出 HTML / PDF / PPT

Recommended sequence:

1. lock the reporting task
2. inspect the workbook and supporting documents
3. build a data map
4. normalize financial display rules
5. generate the page structure
6. reduce wording noise
7. paginate detail pages
8. apply the visual layer
9. export HTML / PDF / PPT

---

## How To Use With `grill-me` And `guizang-ppt-skill`｜如何与 `grill-me` / `guizang-ppt-skill` 联用

推荐组合方式：

- `grill-me` 用来先锁定结构和决策
- `finance-ppt-from-excel` 用来读 Excel、做口径统一、生成财务汇报内容
- `guizang-ppt-skill` 用来在最后一层做 HTML/PPT 风格输出

Recommended combination:

- use `grill-me` to lock structure and decisions first
- use `finance-ppt-from-excel` to read Excel, normalize finance rules, and build the reporting content
- use `guizang-ppt-skill` only for final deck rendering

示例提示词｜Example prompt:

```text
[$grill-me] [$finance-ppt-from-excel] [$guizang-ppt-skill]

基于当前 Excel 工作簿和配套文档，做一份融资情况汇报 HTML PPT。

要求：
1. 先按 grill-me 的方式锁定页面结构、删页和重点项目
2. 再按 finance-ppt-from-excel 的规则统一金额单位、千分位、总计和明细分页
3. 文案以数据呈现和事实进展为主，去掉提示词感和 AI 总结腔
4. 最后再用 guizang-ppt-skill 做视觉输出，但保留财务汇报的表格可读性
5. 同时准备可导出的 PDF / PPT 版本
```

使用原则｜Usage rule:

- 先做财务逻辑，后做视觉包装
- 先锁结构，再调样式
- 如果 workbook 和现有 deck 冲突，以最新 Excel 数据为准，除非用户明确指定别的口径

- finance logic first, visual styling second
- structure first, polish second
- if the workbook conflicts with an existing deck, prefer the latest Excel data unless the user explicitly says otherwise

---

## Repository Structure｜仓库结构

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

---

## Reference Files｜参考文件说明

- `references/data-normalization.md`
  财务数字展示规则：单位、精度、千分位、总计、特殊文本值

  Financial display rules for units, separators, precision, totals, and special text values

- `references/page-structures.md`
  财务类和融资类汇报的默认页面结构

  Default page structures for financing and operating-review decks

- `references/detail-page-rules.md`
  明细页分页、压缩和可读性规则

  Pagination and readability rules for detail-heavy finance pages

- `references/guizang-finance-adaptation.md`
  如何把 `guizang-ppt-skill` 改成适合财务汇报的输出层

  Rules for adapting `guizang-ppt-skill` into a finance-compatible output layer

---

## Design Principles｜设计原则

- 数据优先，不先做风格
- 表格优先，不盲目卡片化
- 文案降噪，不写提示词式总结
- 口径统一，避免数字表达混乱
- 事实优先，进展页尽量写动作和状态

- data first, style later
- tables first when the content demands it
- low-noise wording over decorative copy
- normalized financial display rules
- factual progress and action wording over generic summaries

---

## License

MIT
