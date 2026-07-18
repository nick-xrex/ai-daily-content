---
id: inbox_19aff0dd
date: 2026-07-16
source_ref: "[[00-inbox/.../inbox_19aff0dd]]"
title: "Quoting Thibault Sottiaux"
url: https://simonwillison.net/2026/Jul/16/bad-codex-bug/#atom-everything
source: simon-willison
published_at: 2026-07-16T17:45:59+00:00
fetched_at: 2026-07-18T01:40:57.735192+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex 在 GPT-5.6 中發現檔案刪除漏洞，由 Codex 團隊 Thibault Sottiaux 揭露。觸發條件三要素組合：(1) Full access mode 啟用，(2) 無 sandbox 保護且無 auto review，(3) Model 誤試圖 override $HOME 環境變數以定義臨時目錄。結果：Model 誤刪 $HOME 而非預期的臨時目錄，導致嚴重資料遺失。根本原因是缺乏 sandbox 和 auto review 的雙重安全保障，使 Model 在環境變數處理上的錯誤能直接造成破壞。此漏洞突顯 agentic 系統需分層防禦：runtime container sandbox + permission gates + auto approval，任何一層缺失都可能導致嚴重後果。"
key_points:
  - "GPT-5.6 Codex 檔案刪除漏洞：Full access + 無 sandbox + 無 auto review 三要素同時觸發"
  - "$HOME env var override 失敗：Model 誤刪系統主目錄而非預期 temp dir，導致資料完全遺失"
  - "防禦設計缺陷：缺乏分層防禦（sandbox + permission gates），環境變數誤配置無法被攔截"
tags: [gpt-5-6, codex, file-deletion, security-vulnerability, sandbox]
topics: [foundation_models.gpt]
importance: 5
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## Quoting Thibault Sottiaux

OpenAI Codex 在 GPT-5.6 中發現檔案刪除漏洞，由 Codex 團隊 Thibault Sottiaux 揭露。觸發條件三要素組合：(1) Full access mode 啟用，(2) 無 sandbox 保護且無 auto review，(3) Model 誤試圖 override $HOME 環境變數以定義臨時目錄。結果：Model 誤刪 $HOME 而非預期的臨時目錄，導致嚴重資料遺失。根本原因是缺乏 sandbox 和 auto review 的雙重安全保障，使 Model 在環境變數處理上的錯誤能直接造成破壞。此漏洞突顯 agentic 系統需分層防禦：runtime container sandbox + permission gates + auto approval，任何一層缺失都可能導致嚴重後果。

### 重點
- GPT-5.6 Codex 檔案刪除漏洞：Full access + 無 sandbox + 無 auto review 三要素同時觸發
- $HOME env var override 失敗：Model 誤刪系統主目錄而非預期 temp dir，導致資料完全遺失
- 防禦設計缺陷：缺乏分層防禦（sandbox + permission gates），環境變數誤配置無法被攔截

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/16/bad-codex-bug/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Quoting Thibault Sottiaux

On file deletions. We’ve investigated a handful of reports where GPT-5.6 unexpectedly deleted files. 
 What we have found is that this most commonly occurs when: 
 
 Full access mode is enabled and codex is run without sandboxing protections, including without auto review being enabled 
 The model attempts to override the $HOME env var to define a temporary directory. 
 The model makes an honest mistake and mistakenly deletes $HOME instead. 
 
 &mdash; Thibault Sottiaux , describing a pretty gnarly Codex bug 

 Tags: codex , coding-agents , generative-ai , ai , llms

</details>