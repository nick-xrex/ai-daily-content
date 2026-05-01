---
id: inbox_f92da4fa
date: 2026-04-27
source_ref: "[[00-inbox/2026-04-27/youtube/1257-youtube-ai-engineer-lessons-from-scaling-github-s-remote-mcp-fb8a]]"
title: "Lessons from Scaling GitHub&#39;s Remote MCP Server — Sam Morrow, GitHub"
url: https://www.youtube.com/watch?v=0n3MKk7r60w
source: youtube-ai-engineer
published_at: 2026-04-27T22:00:06+00:00
fetched_at: 2026-05-01T13:18:25.034398+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitHub MCP 服務團隊負責人 Sam Morrow 分享擴展遠端 MCP 伺服器的經驗教訓。GitHub 於去年 4 月發布 MCP（剛滿 1 週年），當時短時間內新增 100+ 個工具致力填補功能空缺，但數週後發現 agents 對 GitHub 的使用效能反而下降、context window 快速崩塌。LangChain 2 月發表研究論文佐證「更多工具≠更聰明的 agents」，問題癥結在於工具數量直接膨脹 context。GitHub 團隊面臨的核心挑戰是在保留用戶所需工具多樣性與維持 agents 有效性之間取得平衡。"
key_points:
  - "GitHub MCP 初期追求工具廣度新增至 100+，導致 agents context 污染、效能下降——LangChain 論文已證實此現象"
  - "問題根源是工具數量直接占用 context window，而非工具功能本身缺陷；需在功能完整性和 context 效率間權衡"
  - "大規模平台（如 GitHub 支援 repos、issues、PRs、actions、projects）使工具選擇複雜化，用戶群多樣化增加定制難度"
tags: [mcp-tools-complexity, context-window-management, agent-effectiveness, platform-scaling]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Lessons from Scaling GitHub's Remote MCP Server — Sam Morrow, GitHub

GitHub MCP 服務團隊負責人 Sam Morrow 分享擴展遠端 MCP 伺服器的經驗教訓。GitHub 於去年 4 月發布 MCP（剛滿 1 週年），當時短時間內新增 100+ 個工具致力填補功能空缺，但數週後發現 agents 對 GitHub 的使用效能反而下降、context window 快速崩塌。LangChain 2 月發表研究論文佐證「更多工具≠更聰明的 agents」，問題癥結在於工具數量直接膨脹 context。GitHub 團隊面臨的核心挑戰是在保留用戶所需工具多樣性與維持 agents 有效性之間取得平衡。

### 重點
- GitHub MCP 初期追求工具廣度新增至 100+，導致 agents context 污染、效能下降——LangChain 論文已證實此現象
- 問題根源是工具數量直接占用 context window，而非工具功能本身缺陷；需在功能完整性和 context 效率間權衡
- 大規模平台（如 GitHub 支援 repos、issues、PRs、actions、projects）使工具選擇複雜化，用戶群多樣化增加定制難度

**原文：** [youtube-ai-engineer](https://www.youtube.com/watch?v=0n3MKk7r60w)