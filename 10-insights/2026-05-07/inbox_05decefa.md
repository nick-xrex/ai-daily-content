---
id: inbox_05decefa
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/youtube/0737-youtube-ai-engineer-vibe-engineering-effect-apps-michael-arn-d4a5]]"
title: "Vibe Engineering Effect Apps — Michael Arnaldi, Effectful"
url: https://www.youtube.com/watch?v=Wmp2Tku2PrI
source: youtube-ai-engineer
published_at: 2026-05-07T15:00:06+00:00
fetched_at: 2026-05-08T07:47:07.210930+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Michael Arnaldi (Effectful) 展示如何與 AI 模型協作開發 Effect 應用。核心洞察是「克隆該死的 repo」—— 將依賴庫直接複製到項目中，而非依賴模型的訓練知識，因為模型被優化以關注自有代碼而非 node_modules。演示從零構建包含 HTTP API、SQLite 持久化、測試的完整應用，建立 agents.md (command reference)、patterns/*.md (best practices) 和 lint rules (約束模型行為) 三層結構。強調通過 ESLint 規則禁止反模式 (如 `as any`、`as never`)，搭配迴圈式 spec-driven 開發，使 AI 模型在大規模複雜代碼庫上表現更佳。"
key_points:
  - "克隆依賴庫到項目目錄 (repos/effect)，讓模型學習具體實現而非訓練知識"
  - "三層結構：agents.md (commands + rules) + patterns/*.md (best practices) + ESLint lint rules (禁止反模式)"
  - "GPT-4.1 vs Claude Opus 權衡：GPT-4.1 簡潔且速度快，但可能快速捷徑 (如 `as any`)；需要 ~1000 行自訂 lint rules 驅動良好代碼"
tags: [effect, ai-driven-development, prompt-engineering, lint-rules, spec-driven-development]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Vibe Engineering Effect Apps — Michael Arnaldi, Effectful

Michael Arnaldi (Effectful) 展示如何與 AI 模型協作開發 Effect 應用。核心洞察是「克隆該死的 repo」—— 將依賴庫直接複製到項目中，而非依賴模型的訓練知識，因為模型被優化以關注自有代碼而非 node_modules。演示從零構建包含 HTTP API、SQLite 持久化、測試的完整應用，建立 agents.md (command reference)、patterns/*.md (best practices) 和 lint rules (約束模型行為) 三層結構。強調通過 ESLint 規則禁止反模式 (如 `as any`、`as never`)，搭配迴圈式 spec-driven 開發，使 AI 模型在大規模複雜代碼庫上表現更佳。

### 重點
- 克隆依賴庫到項目目錄 (repos/effect)，讓模型學習具體實現而非訓練知識
- 三層結構：agents.md (commands + rules) + patterns/*.md (best practices) + ESLint lint rules (禁止反模式)
- GPT-4.1 vs Claude Opus 權衡：GPT-4.1 簡潔且速度快，但可能快速捷徑 (如 `as any`)；需要 ~1000 行自訂 lint rules 驅動良好代碼

**原文：** [youtube-ai-engineer](https://www.youtube.com/watch?v=Wmp2Tku2PrI)