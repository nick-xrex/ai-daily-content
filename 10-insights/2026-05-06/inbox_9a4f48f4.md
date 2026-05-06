---
id: inbox_9a4f48f4
date: 2026-05-06
source_ref: "[[00-inbox/2026-05-06/1002-medium-tag-claude-ai-scope-creep-why-your-pull-requests-ar-9f0a]]"
title: "AI Scope Creep: Why Your Pull Requests Are Quietly Getting Bigger"
url: https://medium.com/@pramida.tumma/ai-scope-creep-why-your-pull-requests-are-quietly-getting-bigger-8d2c827667aa?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-06T08:34:19+00:00
fetched_at: 2026-05-06T10:19:43.768481+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "文章指出 Claude 等 AI 助手缺乏自我限制機制，當要求修復 40 行 bug 時，會同時進行無關改進（重新命名函數、重整 import、加型別提示），導致 PR 膨脹至 400 行。問題不止於審查雜亂，更導致機構知識腐蝕——分散的無關變更使 git blame 失效，開發者 6 個月後無法追蹤代碼歷史。作者建議分層解決方案：prompt 明確約束、專案規則標記重構機會、自動化工具執行、審查紀律優先評估範圍、拆分 PR。核心論點：「AI 不是降低工程標準，而是提高標準」，責任落在開發者驗證與決策上。"
key_points:
  - "AI scope creep 模式：修復 40 行代碼導致 400 行 PR，包含無關改進（重命名、重整 import、型別提示）"
  - "問題影響：分散變更使 git blame 失效，開發者 6 個月後無法追蹤為何代碼存在"
  - "解決方案五層次：prompt 約束、專案規則、自動化執行、審查紀律、PR 分割，強調人工驗證責任"
tags: [ai-scope-creep, pr-management, engineering-discipline, git-history, claude]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## AI Scope Creep: Why Your Pull Requests Are Quietly Getting Bigger

文章指出 Claude 等 AI 助手缺乏自我限制機制，當要求修復 40 行 bug 時，會同時進行無關改進（重新命名函數、重整 import、加型別提示），導致 PR 膨脹至 400 行。問題不止於審查雜亂，更導致機構知識腐蝕——分散的無關變更使 git blame 失效，開發者 6 個月後無法追蹤代碼歷史。作者建議分層解決方案：prompt 明確約束、專案規則標記重構機會、自動化工具執行、審查紀律優先評估範圍、拆分 PR。核心論點：「AI 不是降低工程標準，而是提高標準」，責任落在開發者驗證與決策上。

### 重點
- AI scope creep 模式：修復 40 行代碼導致 400 行 PR，包含無關改進（重命名、重整 import、型別提示）
- 問題影響：分散變更使 git blame 失效，開發者 6 個月後無法追蹤為何代碼存在
- 解決方案五層次：prompt 約束、專案規則、自動化執行、審查紀律、PR 分割，強調人工驗證責任

**原文：** [medium-tag-claude](https://medium.com/@pramida.tumma/ai-scope-creep-why-your-pull-requests-are-quietly-getting-bigger-8d2c827667aa?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<div class="medium-feed-item"><p class="medium-feed-image"><a href="https://medium.com/@pramida.tumma/ai-scope-creep-why-your-pull-requests-are-quietly-getting-bigger-8d2c827667aa?source=rss------claude-5"><img src="https://cdn-images-1.medium.com/max/1536/1*YGNrmuqcRNTQ8WNZ24unVg.png" width="1536" /></a></p><p class="medium-feed-snippet">I asked Claude to fix one bug.</p><p class="medium-feed-link"><a href="https://medium.com/@pramida.tumma/ai-scope-creep-why-your-pull-requests-are-quietly-getting-bigger-8d2c827667aa?source=rss------claude-5">Continue reading on Medium »</a></p></div>

</details>