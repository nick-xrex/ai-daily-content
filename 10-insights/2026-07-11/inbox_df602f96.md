---
id: inbox_df602f96
date: 2026-07-11
source_ref: "[[00-inbox/.../inbox_df602f96]]"
title: "sqlite-utils 4.1"
url: https://simonwillison.net/2026/Jul/11/sqlite-utils/#atom-everything
source: simon-willison
published_at: 2026-07-11T23:50:20+00:00
fetched_at: 2026-07-13T01:07:53.576624+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "sqlite-utils 4.1 發佈，強化資料操作靈活性與型別控制。新特性包括：(1) insert/upsert 新增 `--code` 選項，可內嵌 Python 程式碼塊定義 rows() 生成器（取代外部檔案）；(2) `--type` 選項覆蓋自動推導欄位型別（保留 ZIP 碼前導零）；(3) `drop_index()` 方法與命令；(4) query 支援從 stdin 讀取 SQL；(5) upsert 可自動推導現有表主鍵。值得注意的是，Simon Willison 運用 Codex 審查 open issues 尋找易實作功能、用 GPT-5.6 Sol xhigh Codex 實現 strict 表轉換功能，並特別強調「要求模型手動測試」(uv run python -c 逐項測試) 有效發現自動化測試遺漏的邊界情況與 bug。"
key_points:
  - "CLI 程式碼運行能力擴展：`--code` 選項內嵌 Python 行產生器無需外部檔案；GPT-5.6 Sol 生成與測試該機制，示範模型在工具補強設計上的應用"
  - "型別完整性細粒度控制：`--type` 與 strict mode 轉換(transform strict=True/False) 讓資料型別需求對齐 SQLite，提升資料完整性保障"
  - "AI 輔助開發驗證技巧：Codex 審查 issue 識別開發機會；GPT-5.6 Sol 手動測試提示(非自動化)捕捉邊界 bug—實踐「需要 AI 主動試驗而非被動測試」的驗證模式"
tags: [sqlite-utils, python, ai-assisted-coding, codex, gpt-5-6-sol]
topics: [foundation_models.gpt]
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## sqlite-utils 4.1

sqlite-utils 4.1 發佈，強化資料操作靈活性與型別控制。新特性包括：(1) insert/upsert 新增 `--code` 選項，可內嵌 Python 程式碼塊定義 rows() 生成器（取代外部檔案）；(2) `--type` 選項覆蓋自動推導欄位型別（保留 ZIP 碼前導零）；(3) `drop_index()` 方法與命令；(4) query 支援從 stdin 讀取 SQL；(5) upsert 可自動推導現有表主鍵。值得注意的是，Simon Willison 運用 Codex 審查 open issues 尋找易實作功能、用 GPT-5.6 Sol xhigh Codex 實現 strict 表轉換功能，並特別強調「要求模型手動測試」(uv run python -c 逐項測試) 有效發現自動化測試遺漏的邊界情況與 bug。

### 重點
- CLI 程式碼運行能力擴展：`--code` 選項內嵌 Python 行產生器無需外部檔案；GPT-5.6 Sol 生成與測試該機制，示範模型在工具補強設計上的應用
- 型別完整性細粒度控制：`--type` 與 strict mode 轉換(transform strict=True/False) 讓資料型別需求對齐 SQLite，提升資料完整性保障
- AI 輔助開發驗證技巧：Codex 審查 issue 識別開發機會；GPT-5.6 Sol 手動測試提示(非自動化)捕捉邊界 bug—實踐「需要 AI 主動試驗而非被動測試」的驗證模式

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/11/sqlite-utils/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# sqlite-utils 4.1

Release: sqlite-utils 4.1 
 The first dot-release since 4.0 a few days ago , introducing a number of minor new features. 
 
 
 sqlite-utils insert and sqlite-utils upsert now accept a --code option for providing a block of Python code (or a path to a .py file) that defines a rows() function or rows iterable of rows to insert, as an alternative to importing from a file. ( #684 ) 
 
 
 sqlite-utils already had features that allow you to pass blocks of Python code as CLI arguments, for example this one for the sqlite-utils convert command: 
 sqlite - utils convert content . db articles headline '
 def convert ( value ):
 return value . upper ()' 
 Allowing blocks of code to generate new rows directly was on obvious extension of that pattern: 
 sqlite - utils insert data . db creatures - - code '
 def rows ():
 yield { "id" : 1 , "name" : "Cleo" }
 yield { "id" : 2 , "name" : "Suna" }
' - - pk id 

 
 
 sqlite-utils insert and sqlite-utils upsert now accept --type column-name type to override the type automatically chosen when the table is created . This is useful for CSV or TSV columns such as ZIP codes that look like integers but should be stored as TEXT to preserve leading zeros. ( #131 ) 
 
 
 A long-standing feature request which turned out to be a simple implementation . 
 
 
 New table.drop_index(name) method and sqlite-utils drop-index command for dropping an index by name. Both accept ignore=True / --ignore to ignore a missing index. ( #626 ) 
 sqlite-utils query can now read the SQL query from standard input by passing - in place of the query, for example echo "select * from dogs" | sqlite-utils query dogs.db - . ( #765 ) 
 
 
 Two more small features. I had Codex review all open issues and highlight the easiest ones! 
 
 
 sqlite-utils upsert can now infer the primary key of an existing table, so --pk can be omitted when upserting into a table that already has a primary key. 
 
 
 Another Codex suggestion, an obvious missing CLI feature from a Python library improvement that shipped in the 4.0 release. 
 
 
 table.transform() and table.transform_sql() now accept strict=True or strict=False to change a table’s SQLite strict mode . Omitting the option preserves the existing mode. ( #787 ) 
 The sqlite-utils transform command now accepts --strict and --no-strict to change a table’s strict mode. ( #787 ) 
 
 
 These two were inspired by Prefer STRICT tables in SQLite by Evan Hahn, which did the rounds on Hacker News today. Evan pointed out that: 
 
 Unfortunately, I don’t think there’s a way to ALTER a table to make it strict. I think you have to copy the data out of the non-strict table into the strict one. 
 
 That's exactly what the sqlite-utils transform mechanism does, so I extended it to add the ability to switch tables from strict to non-strict and vice-versa. 
 Here's the GPT-5.6 Sol xhigh Codex transcript I used to implement those new strict table features. One of the most useful prompts I ran was this one: 
 
 use uv run python -c and manually exercise the new .transform(strict=) option, see if you can find any edge-cases or bugs 
 
 Effectively telling the model to manually test its work, outside of the automated tests it had already written. This turned up two minor issues that we then fixed. 
 
 
 Tags: projects , python , sqlite , sqlite-utils , annotated-release-notes , ai-assisted-programming

</details>