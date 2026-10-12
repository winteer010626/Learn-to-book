# 讲义标准结构与排版规范

按此结构组织讲义；用户另有明确要求时从其要求。块类型（h1/h2/p/spans/bullet/table/pagebreak）对应 `build_handout.py` 的 spec。

## 一、内容章节（固定顺序）

1. **Wichtiger Wortschatz（核心词汇）**
   - 1.1 Nomen – 主题词（名词带冠词+复数、中文、例句/搭配）
   - 1.2 Nomen – 抽象高频词
   - 1.3 Verben（动词必须标注配格 +A/+D/sich、中文、例句）
   - 1.4 各补充模块（如教材 Modul）的新增词，按词性混排
2. **Kollokationen & Redemittel（搭配与句型）**，按交际功能分组（定义、偏好、图表、连接词等）
3. **Grammatik（语法）**：概念 → 框架结构 → 时态/形式表 → 转换步骤 → 课本原例 → 易错点；再补该级别高频延伸（如被动态+情态动词、无主语被动）
4. **Texte & Aufgaben（课文与练习）**，每篇课文依次：
   - Einstieg 讨论题（全部列出）
   - 每张图表 → 完整数据表（名次/类别/数值）+ 样本口径与来源 + 配套问题的标准答案
   - 课文内容概述
   - 标题匹配 / 选择 / 填空 / 配图：给出答案，判断题与选择题加“理由”
5. **Prüfungstipps（应试提示）**：按 Hören/Lesen/Schreiben/Sprechen 分点
6. **Mündliche Prüfung（口试必背）**
   - Teil 1 协商：建议/同意/反对/时间地点句型 + 完整示范对话
   - Teil 2 展示框架（Einleitung/Pro/Contra/Meinung/Schluss）
   - 每个可能话题给**成段可背诵模板**（含优缺点与个人观点）
   - 应急句型（请求重复、询问说法、列举）
7. **Schriftliche Prüfung（写作必背）**
   - 该课写作体裁（如图表描述）的三段框架 + 全套 Redemittel
   - ≥1 篇完整 Mustertext（每张主要图表各一篇最佳）
   - 加分句型 + 交稿自查清单

## 二、排版规范（已内置脚本，默认不改）

- 页面 A4、四边 2.5 cm；页脚居中 PAGE 域；两页以上必备
- 标题 18pt 深蓝加粗居中；副标题 10.5pt 斜体居中
- H1 14pt、H2 12pt，深蓝 `1F3A5F` 加粗
- 正文西文 Calibri、中文宋体，10.5pt，行距 1.15，段后 4pt
- 表格：表头深蓝底 `1F3A5F` + 白色加粗居中（中文用微软雅黑）；边框 `4F81BD` 0.5pt；表内 10pt；**所有单元格垂直居中**；表头行重复、各行 cantSplit、固定布局
- 文字列左对齐、数值/短分类列居中；表格下来源注 9.5pt 斜体
- 不使用命名色；颜色用十六进制；正文不出现英文直引号（中文段）

## 三、OOXML 易错点（脚本已处理，手写时务必遵守）

- `tblPr` 顺序：tblW → jc → tblBorders → tblLayout → tblLook；新节点用“按秩插入”，不要 append
- `tcPr` 顺序：tcW → shd → vAlign；底纹 shd 必须在 vAlign 之前
