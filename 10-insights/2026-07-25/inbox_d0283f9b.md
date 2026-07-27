---
id: inbox_d0283f9b
date: 2026-07-25
source_ref: "[[00-inbox/2026-07-25/0123-simon-willison-ruff-v0-16-0-48e8]]"
title: "Ruff v0.16.0"
url: https://simonwillison.net/2026/Jul/25/ruff/#atom-everything
source: simon-willison
published_at: 2026-07-25T22:44:05+00:00
fetched_at: 2026-07-27T01:35:26.434894+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Astral 旗下的 Ruff Python linter 在 v0.16.0 版本大幅擴展預設檢查規則。新版本啟用 413 條規則（相比舊版本 59 條，增幅 600%），總規則庫自 v0.1.0 以來從 708 條增至 968 條。上次預設規則修改距今已有版本跨度（自 v0.1.0），新規則涵蓋語法錯誤、立即運行時錯誤等嚴重問題。Simon Willison 對三個主要項目（Datasette、sqlite-utils、LLM）測試，發現大量違反新規則的問題。以 sqlite-utils 為例，ruff check 報告 1618 個錯誤，其中 1538 條透過 --fix --unsafe-fixes 自動修復，80 條保留待人工處理。"
key_points:
  - "預設啟用規則從 59 增至 413（增幅 600%）；總規則庫增至 968 條，上次默認變更在 v0.1.0"
  - "sqlite-utils 測試：1618 個檢測錯誤，1538 自動修復率（94.9%），保留 80 項人工審核，展示新規則在成熟項目中的廣泛覆蓋"
  - "新規則涵蓋 DTZ005（datetime.now() 缺 tz 參數）、BLE001（盲異常捕捉）、B018（無用屬性訪問），每個錯誤均有具體修復建議"
tags: [ruff, python-linting, static-analysis, astral, code-quality]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Ruff v0.16.0

Astral 旗下的 Ruff Python linter 在 v0.16.0 版本大幅擴展預設檢查規則。新版本啟用 413 條規則（相比舊版本 59 條，增幅 600%），總規則庫自 v0.1.0 以來從 708 條增至 968 條。上次預設規則修改距今已有版本跨度（自 v0.1.0），新規則涵蓋語法錯誤、立即運行時錯誤等嚴重問題。Simon Willison 對三個主要項目（Datasette、sqlite-utils、LLM）測試，發現大量違反新規則的問題。以 sqlite-utils 為例，ruff check 報告 1618 個錯誤，其中 1538 條透過 --fix --unsafe-fixes 自動修復，80 條保留待人工處理。

### 重點
- 預設啟用規則從 59 增至 413（增幅 600%）；總規則庫增至 968 條，上次默認變更在 v0.1.0
- sqlite-utils 測試：1618 個檢測錯誤，1538 自動修復率（94.9%），保留 80 項人工審核，展示新規則在成熟項目中的廣泛覆蓋
- 新規則涵蓋 DTZ005（datetime.now() 缺 tz 參數）、BLE001（盲異常捕捉）、B018（無用屬性訪問），每個錯誤均有具體修復建議

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/25/ruff/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Ruff v0.16.0 
Astral shipped a significant new version of their Ruff Python linting tool a few days ago on July 23rd. I noticed today because my various CI jobs all started failing thanks to new default Ruff checks and my unpinned "ruff" dev dependency. 
 From Brent Westbrook's announcement post: 
 
 Ruff now enables 413 rules by default, up from 59 in previous versions. 
 Since Ruff's default rule set was last modified in v0.1.0 , the number of rules in Ruff has grown from 708 to 968. Many of these rules catch severe issues, including syntax errors and immediate runtime errors but were not previously enabled by default. With the new rule set, Ruff will bring these issues and many others to your attention without any Ruff configuration. 
 
 Here's a one-liner for trying it on any Python project: 
 uvx ruff@latest check .
 
 I ran the latest Ruff against my three biggest projects - Datasette , sqlite-utils , and LLM - and it found hundreds of minor issues that breached the new default rules. 
 All three projects have very comprehensive test suites, executed in CI against Python 3.10 through Python 3.14, so upgrades like this are pretty safe. The following command did the bulk of the upgrades: 
 uvx ruff@latest check . --fix --unsafe-fixes
 
 Against sqlite-utils , that command reported: 
 Found 1618 errors (1538 fixed, 80 remaining).
 
 As an illustrative example, here are three of the remaining issues. Ruff does a nice job of explaining each one: 
 DTZ005 `datetime.datetime.now()` called without a `tz` argument
 --&gt; tests/test_duplicate.py:17:10
 |
15 | "datetime_col" TEXT)""")
16 | # Insert one row of mock data:
17 | dt = datetime.datetime.now()
 | ^^^^^^^^^^^^^^^^^^^^^^^
18 | data = {
19 | "text_col": "Cleo",
 |
help: Pass a `datetime.timezone` object to the `tz` parameter

BLE001 Do not catch blind exception: `Exception`
 --&gt; tests/test_plugins.py:16:12
 |
14 | db.execute("select * from pragma_function_list()")
15 | return True
16 | except Exception:
 | ^^^^^^^^^
17 | return False
18 | finally:
 |

B018 Found useless attribute access. Either assign it to a variable or remove it.
 --&gt; tests/test_update.py:46:5
 |
44 | def test_update_invalid_pk(fresh_db, pk, update_pk):
45 | table = fresh_db["table"]
46 | table.insert({"id1": 5, "id2": 3, "v": 1}, pk=pk).last_pk
 | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
47 | with pytest.raises(NotFoundError):
48 | table.update(update_pk, {"v": 2})
 |
 
 Unsurprisingly, given Astral's new home at OpenAI , this output provides everything a coding agent would need to fix the problems. 
 I had Codex (GPT-5.6 Sol high) upgrade LLM and sqlite-utils , and Claude Code (with Opus 5) upgrade Datasette .

 Tags: python , ruff , astral

</details>