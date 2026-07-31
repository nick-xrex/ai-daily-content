---
id: inbox_2c0874b3
date: 2026-07-30
source_ref: "[[00-inbox/2026-07-30/0107-simon-willison-llm-0-32rc1-260f]]"
title: "llm 0.32rc1"
url: https://simonwillison.net/2026/Jul/30/llm-rc1/#atom-everything
source: simon-willison
published_at: 2026-07-30T15:30:20+00:00
fetched_at: 2026-07-31T01:12:40.852951+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LLM 0.32rc1 RC 版发布，完成了从 0.32a0 开始的 schema 改进工作。新的设计更好地捕捉最新模型系列的 prompt 和 response 细节。最重要的变化是使用内容可寻址的哈希 ID 来存储消息，支持数据库中的重复数据删除。这一设计使 LLM 能够表示分叉对话的消息树结构。新 schema 涉及重大变更（仅新增表，旧数据不受影响），因此建议在升级前备份现有的 logs.db 文件。RC 版本新增对 gpt-5.6-sol、gpt-5.6-terra 和 gpt-5.6-luna 的支持。"
key_points:
  - "新 schema 设计使用内容可寻址哈希 ID 存储消息，支持数据库去重和分叉对话树表示"
  - "仅涉及新表的数据库变更（旧数据不受影响），但建议升级前执行 `llm logs backup logs-backup.db` 备份"
  - "新增对三个 GPT-5.6 变体的支持：Sol（优化推理）、Terra（降价 20%）、Luna（最便宜 $0.20/$1.20）"
tags: [llm, schema-redesign, content-addressable, gpt-5-6]
topics: []
importance: 2
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## llm 0.32rc1

LLM 0.32rc1 RC 版发布，完成了从 0.32a0 开始的 schema 改进工作。新的设计更好地捕捉最新模型系列的 prompt 和 response 细节。最重要的变化是使用内容可寻址的哈希 ID 来存储消息，支持数据库中的重复数据删除。这一设计使 LLM 能够表示分叉对话的消息树结构。新 schema 涉及重大变更（仅新增表，旧数据不受影响），因此建议在升级前备份现有的 logs.db 文件。RC 版本新增对 gpt-5.6-sol、gpt-5.6-terra 和 gpt-5.6-luna 的支持。

### 重點
- 新 schema 设计使用内容可寻址哈希 ID 存储消息，支持数据库去重和分叉对话树表示
- 仅涉及新表的数据库变更（旧数据不受影响），但建议升级前执行 `llm logs backup logs-backup.db` 备份
- 新增对三个 GPT-5.6 变体的支持：Sol（优化推理）、Terra（降价 20%）、Luna（最便宜 $0.20/$1.20）

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/30/llm-rc1/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm 0.32rc1 
 This RC for LLM 0.32 finishes the work that started in LLM 0.32a0 - it adds a new schema design that does a much better job of capturing the details of the prompts and responses returned by the latest model families. 
 The most important change is the use of content-addressable hash IDs for stored messages. This allows de-duplication in the database, and means that LLM can now represent trees of messages for forked conversations. 
 Since it involves a significant schema change - new tables only, and old data should not be affected at all - it's worth running a backup of your existing logs.db before upgrading to the RC: 
 llm logs backup logs-backup.db
 
 The RC also adds support for gpt-5.6-sol , gpt-5.6-terra , and gpt-5.6-luna . 
 
 
 Tags: llm

</details>