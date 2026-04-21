---
id: inbox_66db491f
date: 2026-04-14
source_ref: "[[00-inbox/.../inbox_66db491f]]"
title: "Cybersecurity Looks Like Proof of Work Now"
url: https://simonwillison.net/2026/Apr/14/cybersecurity-proof-of-work/#atom-everything
source: simon-willison
published_at: 2026-04-14T19:41:48+00:00
fetched_at: 2026-04-21T03:15:52.273941+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "英國 AI 安全研究所（AISI）獨立評估 Claude Mythos 在網路安全中的能力，驗證 Anthropic 的聲稱。評估顯示模型花費的 token 越多，識別安全漏洞的效果越好，形成線性關係。此結論導出重要經濟推論：系統強化需花費超越潛在攻擊者的防禦 token，進而使開源專案價值提升（因安全投入可被所有使用者共享）。"
key_points:
  - "AISI 獨立驗證 Claude Mythos 在漏洞識別上表現突出，確認官方聲稱"
  - "安全成本與發現效果呈線性關係：token 投入越多，漏洞發現越多"
  - "開源專案價值提升，因單次安全投入可被所有依賴方受惠"
tags: [claude-mythos, cybersecurity-ai, ai-safety-research, security-economics]
topics: [foundation_models.claude]
importance: 5
novelty: 4
deep_dive_candidate: true
deep_dive_approved: false
---

## Cybersecurity Looks Like Proof of Work Now

英國 AI 安全研究所（AISI）獨立評估 Claude Mythos 在網路安全中的能力，驗證 Anthropic 的聲稱。評估顯示模型花費的 token 越多，識別安全漏洞的效果越好，形成線性關係。此結論導出重要經濟推論：系統強化需花費超越潛在攻擊者的防禦 token，進而使開源專案價值提升（因安全投入可被所有使用者共享）。

### 重點
- AISI 獨立驗證 Claude Mythos 在漏洞識別上表現突出，確認官方聲稱
- 安全成本與發現效果呈線性關係：token 投入越多，漏洞發現越多
- 開源專案價值提升，因單次安全投入可被所有依賴方受惠

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/14/cybersecurity-proof-of-work/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Cybersecurity Looks Like Proof of Work Now

<p><strong><a href="https://www.dbreunig.com/2026/04/14/cybersecurity-is-proof-of-work-now.html">Cybersecurity Looks Like Proof of Work Now</a></strong></p>
The UK's AI Safety Institute recently published <a href="https://www.aisi.gov.uk/blog/our-evaluation-of-claude-mythos-previews-cyber-capabilities">Our evaluation of Claude Mythos Preview’s cyber capabilities</a>, their own independent analysis of <a href="https://simonwillison.net/2026/Apr/7/project-glasswing/">Claude Mythos</a> which backs up Anthropic's claims that it is exceptionally effective at identifying security vulnerabilities.</p>
<p>Drew Breunig notes that AISI's report shows that the more tokens (and hence money) they spent the better the result they got, which leads to a strong economic incentive to spend as much as possible on security reviews:</p>
<blockquote>
<p>If Mythos continues to find exploits so long as you keep throwing money at it, security is reduced to a brutally simple equation: <strong>to harden a system you need to spend more tokens discovering exploits than attackers will spend exploiting them</strong>.</p>
</blockquote>
<p>An interesting result of this is that open source libraries become <em>more</em> valuable, since the tokens spent securing them can be shared across all of their users. This directly counters the idea that the low cost of vibe-coding up a replacement for an open source library makes those open source projects less attractive.


    <p>Tags: <a href="https://simonwillison.net/tags/open-source">open-source</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/drew-breunig">drew-breunig</a>, <a href="https://simonwillison.net/tags/vibe-coding">vibe-coding</a>, <a href="https://simonwillison.net/tags/ai-security-research">ai-security-research</a></p>

</details>