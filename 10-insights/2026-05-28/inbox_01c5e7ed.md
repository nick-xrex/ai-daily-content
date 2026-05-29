---
id: inbox_01c5e7ed
date: 2026-05-28
source_ref: "[[00-inbox/2026-05-28/0001-medium-tag-llm-tame-llm-hallucinations-how-to-write-doc-0102]]"
title: "Tame LLM Hallucinations: How to Write Docs for Retrieval-Augmented Generation"
url: https://medium.com/appian-tech-blog/tame-llm-hallucinations-how-to-write-docs-for-retrieval-augmented-generation-33b2745beb18?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-28T13:44:24+00:00
fetched_at: 2026-05-29T00:12:54.721140+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "技术文档架构对 RAG 系统幻觉率影响超过模型选择。文章提出五大 RAG 优化写作原则，直接改变文档结构而非重构向量数据库。(1) **消除代词**：「它」「这」会在分块后失败指代消解，改为重复主语（atomic content）。(2) **显式消歧**：删除「通常」「目前」等模糊词，强制版本号或RFC 2119 标准（must/may）。(3) **表格去范式**：每行重复分类列，防止合并单元格造成的孤立行。(4) **If/Then 逻辑锚**：分支条件用显式「If...Then」语法，比段落叙述更易被模型捕捉。(5) **键值对结构**：密集段落拆分为列表，每项以粗体键开头。实测表现：重写优于重架构。"
key_points:
  - "文档设计直接影响 RAG 准确度：分块时丧失人类叙事流、指代关系、表格结构意义"
  - "五大原则操作化：原子内容（无代词）、版本锚定（版本号+RFC 2119）、表格去范式、If/Then 条件、键值配对"
  - "可验证实践：从单份最常检索文档开始，应用原则后测量检索准确度提升"
tags: [rag-documentation, hallucination-reduction, content-engineering, technical-writing, chunking-strategy]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: technique
deep_dive_candidate: true
deep_dive_approved: false
---

## Tame LLM Hallucinations: How to Write Docs for Retrieval-Augmented Generation

技术文档架构对 RAG 系统幻觉率影响超过模型选择。文章提出五大 RAG 优化写作原则，直接改变文档结构而非重构向量数据库。(1) **消除代词**：「它」「这」会在分块后失败指代消解，改为重复主语（atomic content）。(2) **显式消歧**：删除「通常」「目前」等模糊词，强制版本号或RFC 2119 标准（must/may）。(3) **表格去范式**：每行重复分类列，防止合并单元格造成的孤立行。(4) **If/Then 逻辑锚**：分支条件用显式「If...Then」语法，比段落叙述更易被模型捕捉。(5) **键值对结构**：密集段落拆分为列表，每项以粗体键开头。实测表现：重写优于重架构。

### 重點
- 文档设计直接影响 RAG 准确度：分块时丧失人类叙事流、指代关系、表格结构意义
- 五大原则操作化：原子内容（无代词）、版本锚定（版本号+RFC 2119）、表格去范式、If/Then 条件、键值配对
- 可验证实践：从单份最常检索文档开始，应用原则后测量检索准确度提升

**原文：** [medium-tag-llm](https://medium.com/appian-tech-blog/tame-llm-hallucinations-how-to-write-docs-for-retrieval-augmented-generation-33b2745beb18?source=rss------large_language_models-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

We have all been there. You ask an internal AI chatbot a highly specific question about a deployment configuration, and it confidently&#x2026; Continue reading on Appian Tech Blog »

</details>