---
id: inbox_76ca68c8
date: 2026-05-14
source_ref: "[[00-inbox/.../inbox_76ca68c8]]"
title: "Not so locked in any more"
url: https://simonwillison.net/2026/May/14/not-so-locked-in/#atom-everything
source: simon-willison
published_at: 2026-05-14T22:53:49+00:00
fetched_at: 2026-05-18T03:48:20.434285+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 報導程式語言技術鎖定正在減弱。某中型科技公司用編碼代理將 iPhone 和 Android 應用重寫為 React Native，若決策失誤可隨時回遷原生開發。Mitchell Hashimoto 指出：程式語言從永久承諾轉為可互換工具，AI 代理降低遷移成本，使語言選擇不再構成長期鎖定。"
key_points:
  - "AI 代理使程式語言可互換：完整應用遷移可在數週內完成而無需完全重設"
  - "編碼代理削弱跨平台維護優勢：React Native 重寫變成可行，原生開發鎖定減弱"
  - "技術決策從永久承諾轉為臨時工具：語言選擇基於現狀，非長期策略枷鎖"
tags: [ai-agents, language-portability, code-generation, lock-in-reduction, development-economics]
topics: [agents.mcp]
importance: 3
novelty: 3
insight_quality: 5
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Not so locked in any more

Simon Willison 報導程式語言技術鎖定正在減弱。某中型科技公司用編碼代理將 iPhone 和 Android 應用重寫為 React Native，若決策失誤可隨時回遷原生開發。Mitchell Hashimoto 指出：程式語言從永久承諾轉為可互換工具，AI 代理降低遷移成本，使語言選擇不再構成長期鎖定。

### 重點
- AI 代理使程式語言可互換：完整應用遷移可在數週內完成而無需完全重設
- 編碼代理削弱跨平台維護優勢：React Native 重寫變成可行，原生開發鎖定減弱
- 技術決策從永久承諾轉為臨時工具：語言選擇基於現狀，非長期策略枷鎖

**原文：** [simon-willison](https://simonwillison.net/2026/May/14/not-so-locked-in/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Not so locked in any more

This Mitchell Hashimoto quote about Bun migrating from Zig to Rust reminded me of a similar conversation I had at a conference last week. 
 I was talking to someone who worked for a medium sized technology company with a pair of legacy/ legendary iPhone and Android apps. 
 They told me they had just completed a coding-agent driven rewrite of both apps to React Native. 
 I asked why they chose that, given that coding agents presumably drive down the cost of maintaining separate iPhone and Android apps. 
 They said that React Native has improved a lot over the past few years and covered everything their apps needed to do. 
 And... if it turned out to be the wrong decision, they could just port back to native in the future. 
 Like Mitchell said: 
 
 Programming languages used to be LOCK IN, and they're increasingly not so. 
 

 Tags: react , coding-agents , ai-assisted-programming , generative-ai , ai , llms

</details>