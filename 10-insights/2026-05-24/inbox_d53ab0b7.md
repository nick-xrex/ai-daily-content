---
id: inbox_d53ab0b7
date: 2026-05-24
source_ref: "[[00-inbox/2026-05-24/0011-simon-willison-quoting-armin-ronacher-42d4]]"
title: "Quoting Armin Ronacher"
url: https://simonwillison.net/2026/May/24/armin-ronacher/#atom-everything
source: simon-willison
published_at: 2026-05-24T18:46:53+00:00
fetched_at: 2026-05-25T00:16:55.597063+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Armin Ronacher 評論指出一個嚴重問題：LLM 改寫的軟體 issue report 充滿錯誤且失去原汁原味。這些被「改寫機」(clanker) 處理過的報告通常包含不準確的結論、虛假的最小化重現 (minimal repro)、錯誤的實作建議及無關的程式碼類比，導致根本原因分析淪為猜測。Ronacher 主張 issue 報告應簡化為四點：執行命令、預期結果、實際結果、確切錯誤或日誌，確保人為觀察成為報告核心。"
key_points:
  - "LLM 改寫問題：失去人的聲音，充滿信心但不準確的推測"
  - "報告品質崩壞：虛假 repro、錯誤根本原因、無關的程式碼類比"
  - "簡化四步驟：命令→預期→實際→錯誤日誌，以人的觀察為中心"
tags: [ai-slop, issue-reporting, github-issues, ai-limitations, open-source]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting Armin Ronacher

Armin Ronacher 評論指出一個嚴重問題：LLM 改寫的軟體 issue report 充滿錯誤且失去原汁原味。這些被「改寫機」(clanker) 處理過的報告通常包含不準確的結論、虛假的最小化重現 (minimal repro)、錯誤的實作建議及無關的程式碼類比，導致根本原因分析淪為猜測。Ronacher 主張 issue 報告應簡化為四點：執行命令、預期結果、實際結果、確切錯誤或日誌，確保人為觀察成為報告核心。

### 重點
- LLM 改寫問題：失去人的聲音，充滿信心但不準確的推測
- 報告品質崩壞：虛假 repro、錯誤根本原因、無關的程式碼類比
- 簡化四步驟：命令→預期→實際→錯誤日誌，以人的觀察為中心

**原文：** [simon-willison](https://simonwillison.net/2026/May/24/armin-ronacher/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The most frustrating failure mode right now is that people submit issues that are not in their own voice. They contain an observed problem somewhere, but it has been thrown into a clanker and the clanker reworded it and made a huge mess of it. Typically, it was prompted so badly that the conclusions produced are more often than not inaccurate but always full of confidence. The result is complete guesswork on root causes, fake-minimal repros, suggested implementation strategies, analogies to adjacent but often the wrong code, and long lists of error classes that might or might not matter. [...] 
 So at least personally, I increasingly want issue reports to be condensed to what the human actually observed: 
 
 I ran this command. 
 I expected this to happen. 
 This happened instead. 
 Here is the exact error or log. 
 
 &mdash; Armin Ronacher , on slop issues filed against Pi 

 Tags: ai , github-issues , llms , ai-ethics , open-source , coding-agents , generative-ai , armin-ronacher , pi , slop

</details>