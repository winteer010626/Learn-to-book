---
name: textbook-to-handout
description: 把用户上传的教材内容（课本/讲义照片、扫描页、CSV 表格、对话或帖子链接，如德语 Goethe B1 的 Lektion 分页图）整理成一份排版统一、可直接背诵的 Word 学习讲义/笔记。当用户说“把这些教材/课本/图片整理成讲义/笔记、按之前的格式、查漏、整理词汇/语法/课文/口语/写作、做 Lektion X 笔记、放桌面”时使用。产出含词汇（带冠词复数/配格）、搭配句型、语法（含转换与易错点）、课文练习答案、口试模板、写作框架与范文，并保证零语法错误。
---

# 教材 → Word 讲义

把上传教材转成与既往讲义同款排版、零语法错误、考点无遗漏的 Word 学习笔记。

## 硬性要求（用户明确强调）

- **零语法错误**：所有外语句子逐句核对，用户“不能背错误的东西”。
- **尽可能详细、不漏考点**；口语和写作积累必须完善（成段模板 + 完整范文）。
- **不编造**：听力等依赖音频/外部材料的答案，无材料时只列题、标注“需要音频”。
- 数字、百分比照抄来源，分清单位；中文沟通，正文外语 + 中文释义。
- 排版与既往讲义一致；成品放用户指定位置（未指定默认桌面），用 present_files 交付。

## 工作流

1. **读全输入**：逐张查看所有照片/扫描页，读取 CSV、链接（必要时用对应工具或浏览器）。不清晰的图放大或分区重读；不凭印象。
2. **逐页提取并查漏**：按 [quality-checklist.md](references/quality-checklist.md) 逐项过，登记词汇、图表数据、题目与答案、讨论题、语法点。
3. **规划讲义结构**：按 [handout-structure.md](references/handout-structure.md) 的固定章节组织；图表先转成完整数据表，题目给出答案与理由。
4. **写 spec（JSON）**：参照 [spec_example.json](references/spec_example.json)，用 h1/h2/p/spans/bullet/table/pagebreak 描述全部内容。
5. **生成 Word**：
   ```
   python scripts/build_handout.py spec.json out.docx
   ```
   排版常量（深蓝表头 1F3A5F、边框 4F81BD、Calibri/宋体、A4、页脚 PAGE）已内置。
6. **校验**：用 word skill 的 `audit.py` 审计（必须 0 错误，改完重跑）；用 `read.py` 回读核对章节、表格行数与关键答案。
7. **交付**：保存到指定位置（默认桌面），present_files 交付，并说明验证结果与仍缺材料（如音频）。

## 参考文件

- [references/handout-structure.md](references/handout-structure.md)：讲义章节模板、排版规范、OOXML 顺序要点。
- [references/quality-checklist.md](references/quality-checklist.md)：逐页漏项排查、考点覆盖、零语法错误、交付前清单。
- [references/spec_example.json](references/spec_example.json)：spec 完整示例。

## 备注

- 手写/改 OOXML 时遵守节点顺序：`tblPr` 为 tblW→jc→tblBorders→tblLayout→tblLook；`tcPr` 为 tcW→shd→vAlign，禁止盲目 append。
- 若用户要编辑的是已存在的 Word（而非新建），改用 word skill 的对应流程，先取最新态再改。
