---
id: inbox_4a213d37
date: 2026-06-21
source_ref: "[[00-inbox/2026-06-21/0106-simon-willison-temporary-cloudflare-accounts-for-ai-age-5fbc]]"
title: "Temporary Cloudflare Accounts for AI agents"
url: https://simonwillison.net/2026/Jun/21/temporary-cloudflare-accounts/#atom-everything
source: simon-willison
published_at: 2026-06-21T22:01:04+00:00
fetched_at: 2026-06-22T01:11:32.140915+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Cloudflare 推出臨時帳戶功能，允許透過 `npx wrangler deploy --temporary` 無需建立正式帳戶即可部署 Workers 應用。自動生成 60 分鐘有效的臨時部署鏈結，適合原型開發和短期測試。部署後提供領取頁面，用戶可選擇升級為永久專案。該特性對 AI agent 短期任務部署和開發測試尤為實用。文章作者用 LLM 快速原型化 HTTP redirect 工具，驗證臨時部署的實用性。"
key_points:
  - "`npx wrangler deploy --temporary` 無帳戶部署，60 分鐘有效期自動失效"
  - "支援事後領取升級為永久專案"
  - "適用原型開發、測試、AI agent 短期任務"
tags: [cloudflare-workers, deployment, temporary-hosting, developer-tools]
topics: []
importance: 3
novelty: 3
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Temporary Cloudflare Accounts for AI agents

Cloudflare 推出臨時帳戶功能，允許透過 `npx wrangler deploy --temporary` 無需建立正式帳戶即可部署 Workers 應用。自動生成 60 分鐘有效的臨時部署鏈結，適合原型開發和短期測試。部署後提供領取頁面，用戶可選擇升級為永久專案。該特性對 AI agent 短期任務部署和開發測試尤為實用。文章作者用 LLM 快速原型化 HTTP redirect 工具，驗證臨時部署的實用性。

### 重點
- `npx wrangler deploy --temporary` 無帳戶部署，60 分鐘有效期自動失效
- 支援事後領取升級為永久專案
- 適用原型開發、測試、AI agent 短期任務

**原文：** [simon-willison](https://simonwillison.net/2026/Jun/21/temporary-cloudflare-accounts/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Temporary Cloudflare Accounts for AI agents 
The announcement says this is "for AI agents" but (as is pretty common these days) the AI hook isn't really necessary, this is an interesting feature for everyone else as well. 
 Short version: you can now create a Cloudflare Workers project and run this, without even creating a Cloudflare account: 
 npx wrangler deploy --temporary
 
 Cloudflare will deploy the application to a new, ephemeral project which will stay live for 60 minutes. 
 I had GPT-5.5 xhigh in Codex Desktop build this test application providing a tool for following HTTP redirects and returning the final destination. The temporary deployment worked as advertised. 
 Running the deployment spits out the URL to a page for claiming the new project, for if you want it to last for more than 60 minutes. Here's what that claim screen looks like: 
 

 Via Hacker News 

 Tags: cloudflare

</details>