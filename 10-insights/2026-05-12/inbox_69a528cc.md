---
id: inbox_69a528cc
date: 2026-05-12
source_ref: "[[00-inbox/.../inbox_69a528cc]]"
title: "datasette 1.0a29"
url: https://simonwillison.net/2026/May/12/datasette/#atom-everything
source: simon-willison
published_at: 2026-05-12T23:41:06+00:00
fetched_at: 2026-05-18T03:30:56.377999+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Datasette 發佈 1.0a29 版本，引入 TokenRestrictions.abbreviated() 新工具方法用於建立 \"_r\" 字典，改進表頭與欄選項的顯示（即使在空表時），修復了 Mobile Safari 上欄操作對話框的顯示問題。最值得注意的是修復了一個複雜的 race condition bug：自動關閉機制與飛行中的查詢衝突導致分段崩潰；作者用 Codex CLI + GPT-5.5 xhigh 撰寫了最小化 Dockerfile 成功重現該 bug，加速了調試流程。"
key_points:
  - "新增 TokenRestrictions.abbreviated() 工具方法簡化 \"_r\" 字典建立流程"
  - "Race condition bug 源於自動連接關閉與線程中飛行查詢的衝突；用 Dockerfile 隔離環境重現是診斷關鍵"
  - "Codex CLI + GPT-5.5 xhigh 協助快速建構 Dockerfile 重現複雜並發 bug，展示 AI 工具在調試中的實用價值"
tags: [datasette, release, race-condition, docker, concurrent-bugs]
topics: []
importance: 3
novelty: 2
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## datasette 1.0a29

Datasette 發佈 1.0a29 版本，引入 TokenRestrictions.abbreviated() 新工具方法用於建立 "_r" 字典，改進表頭與欄選項的顯示（即使在空表時），修復了 Mobile Safari 上欄操作對話框的顯示問題。最值得注意的是修復了一個複雜的 race condition bug：自動關閉機制與飛行中的查詢衝突導致分段崩潰；作者用 Codex CLI + GPT-5.5 xhigh 撰寫了最小化 Dockerfile 成功重現該 bug，加速了調試流程。

### 重點
- 新增 TokenRestrictions.abbreviated() 工具方法簡化 "_r" 字典建立流程
- Race condition bug 源於自動連接關閉與線程中飛行查詢的衝突；用 Dockerfile 隔離環境重現是診斷關鍵
- Codex CLI + GPT-5.5 xhigh 協助快速建構 Dockerfile 重現複雜並發 bug，展示 AI 工具在調試中的實用價值

**原文：** [simon-willison](https://simonwillison.net/2026/May/12/datasette/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# datasette 1.0a29

Release: datasette 1.0a29 
 
 
 New TokenRestrictions.abbreviated(datasette) utility method for creating "_r" dictionaries. #2695 
 Table headers and column options are now visible even if a table contains zero rows. #2701 
 Fixed bug with display of column actions dialog on Mobile Safari. #2708 
 Fixed bug where tests could crash with a segfault due to a race condition between Datasette.close() and Database.close() . #2709 
 
 
 That segfault bug was gnarly . I added a mechanism to Datasette recently that would automatically close connections at the end of each test, but it turned out that introduced a race condition where an in-flight query could sometimes be executing in a thread against a connection while it was being closed. I ended up solving that by having Codex CLI (with GPT-5.5 xhigh) create a minimal Dockerfile that recreated the bug. 
 
 
 Tags: projects , datasette

</details>