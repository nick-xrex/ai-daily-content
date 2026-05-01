---
id: inbox_65d78e65
date: 2026-04-29
source_ref: "[[00-inbox/2026-04-29/1259-hackernews-hermes-md-in-commit-messages-causes-requ-12f7]]"
title: "HERMES.md in commit messages causes requests to route to extra usage billing"
url: https://github.com/anthropics/claude-code/issues/53262
source: hackernews
published_at: 2026-04-29T18:54:31+00:00
fetched_at: 2026-05-01T13:49:02.246221+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Anthropic 的 Claude Code 發現嚴重計費漏洞：提交訊息中包含大小寫敏感字串「HERMES.md」時，API 請求被錯誤路由至「額外使用額度」計費，而非 Max 20x 方案（$200/月）的包含配額。受影響用戶額外費用被消耗 $200.98，方案配額仍有 86% 未使用；額度耗盡後專案完全無法使用。觸發機制為系統提示含最近提交訊息，因而觸發伺服器端內容驅動路由邏輯。Anthropic 已為受影響用戶提供全額退款及額外一個月額度補償。"
key_points:
  - "提交訊息含『HERMES.md』（大小寫敏感）導致請求錯誤路由至額外計費，消耗 $200.98 額度"
  - "Max 20x 方案（$200/月）配額仍有 86% 未使用，額度耗盡後專案無法使用"
  - "系統提示包含最近提交而觸發伺服器端內容驅動路由邏輯；Anthropic 已全額退款並補償"
tags: [claude-code-billing-bug, api-routing-error, content-driven-pricing]
topics: [foundation_models.claude]
importance: 4
novelty: 2
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## HERMES.md in commit messages causes requests to route to extra usage billing

Anthropic 的 Claude Code 發現嚴重計費漏洞：提交訊息中包含大小寫敏感字串「HERMES.md」時，API 請求被錯誤路由至「額外使用額度」計費，而非 Max 20x 方案（$200/月）的包含配額。受影響用戶額外費用被消耗 $200.98，方案配額仍有 86% 未使用；額度耗盡後專案完全無法使用。觸發機制為系統提示含最近提交訊息，因而觸發伺服器端內容驅動路由邏輯。Anthropic 已為受影響用戶提供全額退款及額外一個月額度補償。

### 重點
- 提交訊息含『HERMES.md』（大小寫敏感）導致請求錯誤路由至額外計費，消耗 $200.98 額度
- Max 20x 方案（$200/月）配額仍有 86% 未使用，額度耗盡後專案無法使用
- 系統提示包含最近提交而觸發伺服器端內容驅動路由邏輯；Anthropic 已全額退款並補償

**原文：** [hackernews](https://github.com/anthropics/claude-code/issues/53262)