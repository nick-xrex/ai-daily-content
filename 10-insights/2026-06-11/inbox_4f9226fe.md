---
id: inbox_4f9226fe
date: 2026-06-11
source_ref: "[[00-inbox/2026-06-11/2200-simon-willison-anthropic-walks-back-policy-that-could-h-662b]]"
title: "Anthropic Walks Back Policy That Could Have ‘Sabotaged’ AI Researchers Using Claude"
url: https://simonwillison.net/2026/Jun/11/anthropic-walks-back-policy/#atom-everything
source: simon-willison
published_at: 2026-06-11T03:45:49+00:00
fetched_at: 2026-06-11T22:08:02.449037+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Anthropic 改变了 Fable 5 的前沿 LLM 开发 safeguard 政策。原本 Claude 会隐形地识别并削弱针对「前沿 LLM 开发」的请求却不通知用户，引发研究社群强烈反弹。现已改为可见化：被标记的请求将明确回退到 Opus 4.8（与网络安全及生物风险 safeguard 同级），用户每次都能看到拦截原因。API 端服务端回退推出前已返回拒绝理由。Anthropic 承认选择隐形 safeguard 是为快速部署和减少误判，但这是「错误的权衡」，优先级低于透明度。"
key_points:
  - "Fable 5 前沿 LLM 开发 safeguard 从隐形改为可见，回退至 Opus 4.8 并显示拦截原因"
  - "API 新增 reason 字段，服务端回退推出前已返回拒绝理由"
  - "Anthropic 承认隐形设计优先级低于用户透明度，改为先快速部署后持续优化"
tags: [anthropic-safeguard, claude-fable, ai-governance, transparency, llm-research]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 3
insight_type: announcement
deep_dive_candidate: true
deep_dive_approved: false
---

## Anthropic Walks Back Policy That Could Have ‘Sabotaged’ AI Researchers Using Claude

Anthropic 改变了 Fable 5 的前沿 LLM 开发 safeguard 政策。原本 Claude 会隐形地识别并削弱针对「前沿 LLM 开发」的请求却不通知用户，引发研究社群强烈反弹。现已改为可见化：被标记的请求将明确回退到 Opus 4.8（与网络安全及生物风险 safeguard 同级），用户每次都能看到拦截原因。API 端服务端回退推出前已返回拒绝理由。Anthropic 承认选择隐形 safeguard 是为快速部署和减少误判，但这是「错误的权衡」，优先级低于透明度。

### 重點
- Fable 5 前沿 LLM 开发 safeguard 从隐形改为可见，回退至 Opus 4.8 并显示拦截原因
- API 新增 reason 字段，服务端回退推出前已返回拒绝理由
- Anthropic 承认隐形设计优先级低于用户透明度，改为先快速部署后持续优化

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/11/anthropic-walks-back-policy/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Anthropic Walks Back Policy That Could Have ‘Sabotaged’ AI Researchers Using Claude 
Big scoop for Maxwell Zeff at Wired: 
 
 “We’re changing Fable 5’s safeguards for frontier LLM development to make them visible.” Anthropic said in a statement to WIRED. “We made the wrong tradeoff and we apologize for not getting the balance right.” 
 
 There's been a huge outcry about Anthropic's policy, tucked away in their system card , that Claude Fable/Mythos would identify "requests targeting frontier LLM development" and "limit effectiveness" without notifying the user. 
 It's good news that they're dropping the invisible aspect of this. It would be a whole lot better of they dropped this category of refusals entirely. 
 Update : More details from @ClaudeDevs on Twitter : 
 
 We’re rolling out changes to make Fable 5’s safeguards for frontier LLM development visible. 
 Starting this week, flagged requests will visibly fall back to Opus 4.8—the same as our safeguards for cyber and bio. You will see this every time it happens. On the API, any flagged requests will return a reason for their refusal (coming to server-side fallback in the next few days). 
 We wanted to deploy Fable 5 to our users quickly and safely. Visible safeguards can be probed, so they have to be robust, which takes time to get right. Invisible safeguards can be targeted more narrowly, allowing us to ship quickly with very few false positives. We went with invisible safeguards for this reason—and that was the wrong tradeoff. You should have visibility into the safeguards we have in place, and why. We’re sorry for not getting the balance right. 
 

 Via @zeffmax 

 Tags: ai , generative-ai , llms , anthropic , claude , ai-ethics , claude-mythos

</details>