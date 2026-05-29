---
id: inbox_e1ab808c
date: 2026-05-28
source_ref: "[[00-inbox/2026-05-28/0140-ruflo-releases-v3-10-4-statusline-generator-fix-5efa]]"
title: "v3.10.4 — statusline generator fix"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.4
source: ruflo-releases
published_at: 2026-05-28T00:47:12+00:00
fetched_at: 2026-05-28T01:43:34.934666+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.4 修復狀態欄產生器問題。狀態欄生成器現委派至 hooks statusline --json 而非脆弱本地讀者，ADR 計數修正為統計 v3/docs/adr/ 與 v3/implementation/adrs/ 兩目錄，總計 128 項（先前漏計 87 項，誤差 41 項）。新增 CI 防守機制防止此類迴歸。同時發佈至 @claude-flow/cli、claude-flow、ruflo 三個套件及 latest/alpha/v3alpha 發行版標籤。"
key_points:
  - "v3.10.4 修復狀態欄產生器委派至 hooks（改善可靠性）"
  - "ADR 計數修正：統計兩個目錄，總計 128 項（先前為 87，漏計 41 項）"
  - "新增 CI 防守機制，發佈至三套件及三個發行版標籤"
tags: [ruflo, bugfix, statusline, adr-counting, ci-guard]
topics: [agents.mcp]
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.10.4 — statusline generator fix

Ruflo v3.10.4 修復狀態欄產生器問題。狀態欄生成器現委派至 hooks statusline --json 而非脆弱本地讀者，ADR 計數修正為統計 v3/docs/adr/ 與 v3/implementation/adrs/ 兩目錄，總計 128 項（先前漏計 87 項，誤差 41 項）。新增 CI 防守機制防止此類迴歸。同時發佈至 @claude-flow/cli、claude-flow、ruflo 三個套件及 latest/alpha/v3alpha 發行版標籤。

### 重點
- v3.10.4 修復狀態欄產生器委派至 hooks（改善可靠性）
- ADR 計數修正：統計兩個目錄，總計 128 項（先前為 87，漏計 41 項）
- 新增 CI 防守機制，發佈至三套件及三個發行版標籤

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Fixes #2195 : statusline generator delegates to hooks statusline --json instead of fragile local readers. ADR count now sums both v3/docs/adr/ and v3/implementation/adrs/ directories (128 total, not 87). New CI guard prevents regressions of this bug class. 
 Published to all three packages (@claude-flow/cli, claude-flow, ruflo) with latest/alpha/v3alpha dist-tags.

</details>