---
id: inbox_66db491f
date: 2026-04-14
source_ref: "[[00-inbox/.../inbox_66db491f]]"
title: "Cybersecurity Looks Like Proof of Work Now"
url: https://simonwillison.net/2026/Apr/14/cybersecurity-proof-of-work/#atom-everything
source: (resumed)
published_at: 2026-04-14T19:41:48+00:00
fetched_at: 2026-04-21T02:40:32.045736+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "英國 AI Safety Institute（AISI）獨立評估發現 Claude Mythos 在發現安全漏洞方面效能優異。評估報告顯示消費的 token 數越多、審計成效越好，呈現線性相關。評論家 Drew Breunig 指出這揭露了網路安全經濟學的新面向：系統防禦成本必須超過攻擊者的利用成本。此動態直接提升開源套件的價值，因為安全審計成本可分攤於所有使用者，反駁了「廉價 AI 自動化威脅開源專案」的論點。"
key_points:
  - "AISI 確認：Claude Mythos 通過增加 token 投入找到更多漏洞（Proof-of-Work 經濟學模式）"
  - "安全防禦公式：防守花費 token 數 > 攻擊者花費 token 數，形成明確經濟激勵"
  - "開源套件價值上升：安全審計成本被多用戶攤分，增強長期競爭力"
tags: [claude-mythos, security-economics, proof-of-work, open-source, ai-security]
topics: [foundation_models.claude]
importance: 4
novelty: 3
deep_dive_candidate: false
deep_dive_approved: false
---

## Cybersecurity Looks Like Proof of Work Now

英國 AI Safety Institute（AISI）獨立評估發現 Claude Mythos 在發現安全漏洞方面效能優異。評估報告顯示消費的 token 數越多、審計成效越好，呈現線性相關。評論家 Drew Breunig 指出這揭露了網路安全經濟學的新面向：系統防禦成本必須超過攻擊者的利用成本。此動態直接提升開源套件的價值，因為安全審計成本可分攤於所有使用者，反駁了「廉價 AI 自動化威脅開源專案」的論點。

### 重點
- AISI 確認：Claude Mythos 通過增加 token 投入找到更多漏洞（Proof-of-Work 經濟學模式）
- 安全防禦公式：防守花費 token 數 > 攻擊者花費 token 數，形成明確經濟激勵
- 開源套件價值上升：安全審計成本被多用戶攤分，增強長期競爭力

**原文：** [(resumed)](https://simonwillison.net/2026/Apr/14/cybersecurity-proof-of-work/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://www.dbreunig.com/2026/04/14/cybersecurity-is-proof-of-work-now.html">Cybersecurity Looks Like Proof of Work Now</a></strong></p>
The UK's AI Safety Institute recently published <a href="https://www.aisi.gov.uk/blog/our-evaluation-of-claude-mythos-previews-cyber-capabilities">Our evaluation of Claude Mythos Preview’s cyber capabilities</a>, their own independent analysis of <a href="https://simonwillison.net/2026/Apr/7/project-glasswing/">Claude Mythos</a> which backs up Anthropic's claims that it is exceptionally effective at identifying security vulnerabilities.</p>
<p>Drew Breunig notes that AISI's report shows that the more tokens (and hence money) they spent the better the result they got, which leads to a strong economic incentive to spend as much as possible on security reviews:</p>
<blockquote>
<p>If Mythos continues to find exploits so long as you keep throwing money at it, security is reduced to a brutally simple equation: <strong>to harden a system you need to spend more tokens discovering exploits than attackers will spend exploiting them</strong>.</p>
</blockquote>
<p>An interesting result of this is that open source libraries become <em>more</em> valuable, since the tokens spent securing them can be shared across all of their users. This directly counters the idea that the low cost of vibe-coding up a replacement for an open source library makes those open source projects less attractive.


    <p>Tags: <a href="https://simonwillison.net/tags/open-source">open-source</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/drew-breunig">drew-breunig</a>, <a href="https://simonwillison.net/tags/vibe-coding">vibe-coding</a>, <a href="https://simonwillison.net/tags/ai-security-research">ai-security-research</a></p>

</details>
