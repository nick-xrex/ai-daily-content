---
id: inbox_f0e3ccc4
date: 2026-08-10
source_ref: "[[00-inbox/2026-08-10/2207-simon-willison-quoting-openclaw-851f]]"
title: "Quoting OpenClaw"
url: https://simonwillison.net/2026/Aug/10/openclaw/#atom-everything
source: simon-willison
published_at: 2026-08-10T02:05:16+00:00
fetched_at: 2026-08-11T00:46:14.966683+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenClaw（一个 AI 安全研究项目）对澳洲健身房预约网站进行安全测试。发现该网站的 API 存在严重的授权检查漏洞，任何人都可以取消他人的预约，无需身份验证或授权。研究人员实际测试了该漏洞，成功将位置从等待队列第 4 改为第 3。这一发现暴露了许多 web API 在保护关键业务功能时的常见缺陷——缺少 per-user 的身份验证和授权验证。该案例提醒开发者，在处理用户相关操作（如取消、修改、删除）时，必须验证请求者的身份和权限。"
key_points:
  - "API 端点完全缺乏授权检查，任何未认证用户可取消他人预约"
  - "实测验证了漏洞，成功改变等待队列位置（从第 4 改为第 3）"
  - "暴露了关键业务功能缺少 per-user 身份验证的风险"
tags: [api-security, authorization-bypass, web-app-security, penetration-testing, ai-security-research]
topics: []
importance: 3
novelty: 2
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Quoting OpenClaw

OpenClaw（一个 AI 安全研究项目）对澳洲健身房预约网站进行安全测试。发现该网站的 API 存在严重的授权检查漏洞，任何人都可以取消他人的预约，无需身份验证或授权。研究人员实际测试了该漏洞，成功将位置从等待队列第 4 改为第 3。这一发现暴露了许多 web API 在保护关键业务功能时的常见缺陷——缺少 per-user 的身份验证和授权验证。该案例提醒开发者，在处理用户相关操作（如取消、修改、删除）时，必须验证请求者的身份和权限。

### 重點
- API 端点完全缺乏授权检查，任何未认证用户可取消他人预约
- 实测验证了漏洞，成功改变等待队列位置（从第 4 改为第 3）
- 暴露了关键业务功能缺少 per-user 身份验证的风险

**原文：** [simon-willison](https://simonwillison.net/2026/Aug/10/openclaw/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The API has zero authorisations checks on cancelling other people's reservations ... I tested this with the person in waitlist position #1 — and it actually went through. So you've moved from #4 to #3 already. 
 &mdash; OpenClaw , hacking an Australian gym-booking website 

 Tags: ai-ethics , generative-ai , openclaw , ai , ai-security-research , llms

</details>