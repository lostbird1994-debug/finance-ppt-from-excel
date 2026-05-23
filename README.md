# finance-ppt-from-excel

中文｜English

一个面向财务汇报场景的开源 skill，用来把 Excel 工作簿、配套文档、旧版材料整理成更适合内部经营会、融资汇报、预算复盘、银行渠道进展汇报的 PPT。

An open skill for turning Excel workbooks, supporting documents, and old reporting materials into finance-style presentation decks.

---

## 这个 Skill 适合做什么｜What This Skill Is For

适用场景：

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
- bank / channel progress decks
- management reporting decks
- any data-heavy PPT where units, tables, totals, pagination, and low-noise wording matter more than generic slide design

---

## 它解决的核心问题｜What It Solves

这个 skill 不是一个“泛 PPT 美化器”，而是一套财务汇报工作流：

1. 读取 Excel 和配套文档
2. 识别总表、分类表、明细表、进展表
3. 统一金额单位、精度、千分位、总计规则
4. 生成财务汇报结构
5. 清理 AI 味和解释性废话
6. 对明细页做可读性分页
7. 最后再交给视觉输出层，例如 `guizang-ppt-skill`

This skill is not a generic slide beautifier. It acts as the workflow layer for finance decks:

1. reads Excel and supporting documents
2. identifies total / segment / detail / progress tables
3. normalizes units, precision, separators, and totals
4. generates a finance-report structure
5. removes noisy or AI-sounding wording
6. paginates detail-heavy pages safely
7. hands off to a visual output layer such as `guizang-ppt-skill`

---

## 项目定位｜Project Positioning

这个项目把财务 PPT 拆成三层：

1. `grill-me`
   负责锁定范围、结构、删页、重点和决策分支

2. `finance-ppt-from-excel`
   负责把 Excel / 文档转成财务汇报内容系统

3. 视觉输出层，例如 `guizang-ppt-skill`
   负责把已经结构化好的内容渲染成 HTML / PPT 风格成品

This project treats a financial presentation as a three-layer system:

1. `grill-me`
   decision-locking layer for narrowing scope, structure, deletions, and emphasis

2. `finance-ppt-from-excel`
   content and workflow layer for converting Excel/documents into a financial reporting system

3. visual output layer such as `guizang-ppt-skill`
   styling layer for rendering already-structured content

重要说明｜Important:

- `guizang-ppt-skill` 在这里不是主逻辑 skill
- 它只是最终视觉皮肤
- 它必须经过“财务化改写”后才能适合财务汇报

- `guizang-ppt-skill` is not used here as the main finance logic engine
- it is treated as a final visual skin
- it must be adapted for finance readability before use

---

## 仓库结构｜Repository Structure

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

## 参考文件说明｜Included References

- `data-normalization.md`
  财务数字展示规则：单位、精度、千分位、总计、特殊文本值

  Financial display rules for units, separators, totals, precision, and special text values

- `page-structures.md`
  财务类和融资类汇报的默认页面结构

  Default page structures for financing and operating-review decks

- `detail-page-rules.md`
  明细页分页、压缩和可读性规则

  Pagination and readability rules for detail-heavy finance pages

- `guizang-finance-adaptation.md`
  如何把 `guizang-ppt-skill` 改成适合财务汇报的输出层

  Rules for adapting `guizang-ppt-skill` into a finance-compatible output layer

---

## 推荐使用方式｜Recommended Usage

推荐顺序：

1. 先锁汇报任务
2. 再检查 workbook 和文档
3. 建立数据映射
4. 统一财务展示规则
5. 生成页面结构
6. 做文案减法
7. 做明细分页
8. 再贴视觉风格
9. 最后导出 HTML / PDF / PPT

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

---

## 为什么不是直接用 guizang｜Why Not Use Guizang Directly

`guizang-ppt-skill` 非常适合做杂志感、演讲感、观点型页面，但并不天然适合财务汇报。

财务 PPT 需要额外处理：

- 数字千分位
- 单位统一
- 总计逻辑
- 明细分页
- 事实型进展文案
- 表格优先而不是卡片优先

`guizang-ppt-skill` is strong for editorial, magazine-like, and talk-driven slides, but it is not finance-native by default.

Financial reporting needs additional rules for:

- thousands separators
- unit normalization
- totals
- detail-page pagination
- factual progress wording
- table-first presentation where needed

---

## License

MIT
