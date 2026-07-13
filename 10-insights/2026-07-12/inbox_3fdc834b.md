---
id: inbox_3fdc834b
date: 2026-07-12
source_ref: "[[00-inbox/.../inbox_3fdc834b]]"
title: "v0.31.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.31.0
source: repowise-releases
published_at: 2026-07-12T11:52:12+00:00
fetched_at: 2026-07-13T01:07:53.573041+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.31.0 發佈，核心新功能為測試覆蓋率驅動的智能信號（per-test 環境、coverage-backed missing-test signal）與 `repowise impacted-tests` 命令、從 agent 會話文字紀錄挖掘持久決策並在 SessionStart/編輯時注入相關度排序的決策、以及錨定在實際程式碼體的答案生成（grounded get_answer）。MCP 層面強化會話存續、響應預算箝制、答案聯合以處理同音符號；新增 shell 語言 AST 解析（函式、來源邊、複雜度）、agent 共同作者偵測、hooks 指南與使用者行為學習能力。另支援 MCP-only Docker 映像與改進符號界線驗證。"
key_points:
  - "覆蓋率驅動測試智能：per-test 環境映射與 coverage-backed missing-test signal，新指令 `repowise impacted-tests` 識別程式碼變更的受影響測試"
  - "Agent 決策挖掘與注入：從 agent 會話記錄提取持久決策，在 SessionStart 與編輯時以相關度排序注入，增加開發決策可追蹤性"
  - "錨定答案與 MCP 硬化：get_answer 回應根據實際程式碼體精化，處理同音符號聯合答案、遺漏別名鍵與資料形狀缺口，強化 MCP 響應預算和會話存續"
tags: [repowise, test-coverage-intelligence, agent-decision-mining, mcp-hardening, shell-ast]
topics: [agents.mcp]
importance: 4
novelty: 4
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.31.0

Repowise v0.31.0 發佈，核心新功能為測試覆蓋率驅動的智能信號（per-test 環境、coverage-backed missing-test signal）與 `repowise impacted-tests` 命令、從 agent 會話文字紀錄挖掘持久決策並在 SessionStart/編輯時注入相關度排序的決策、以及錨定在實際程式碼體的答案生成（grounded get_answer）。MCP 層面強化會話存續、響應預算箝制、答案聯合以處理同音符號；新增 shell 語言 AST 解析（函式、來源邊、複雜度）、agent 共同作者偵測、hooks 指南與使用者行為學習能力。另支援 MCP-only Docker 映像與改進符號界線驗證。

### 重點
- 覆蓋率驅動測試智能：per-test 環境映射與 coverage-backed missing-test signal，新指令 `repowise impacted-tests` 識別程式碼變更的受影響測試
- Agent 決策挖掘與注入：從 agent 會話記錄提取持久決策，在 SessionStart 與編輯時以相關度排序注入，增加開發決策可追蹤性
- 錨定答案與 MCP 硬化：get_answer 回應根據實際程式碼體精化，處理同音符號聯合答案、遺漏別名鍵與資料形狀缺口，強化 MCP 響應預算和會話存續

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.31.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.31.0

What's Changed 
 
 test(vscode): fix flaky home-sidebar summary-failure assertion by @swati510 in #766 
 feat(mcp): session-survival hardening for the tool surface by @RaghavChamadiya in #767 
 feat(languages): parse shell to AST (functions, source edges, complexity) by @RaghavChamadiya in #768 
 fix(mcp): keep non-path node ids out of get_answer fallback_targets by @RaghavChamadiya in #769 
 fix(mcp): honesty signals for zero-exact search and filename-only get_symbol by @RaghavChamadiya in #770 
 feat(mcp): clamp response budget under the live MCP host token cap by @RaghavChamadiya in #771 
 feat(mcp): answer-by-union for homonym symbols in get_answer by @RaghavChamadiya in #772 
 feat(core): shared agent-transcript layer core/sessions by @RaghavChamadiya in #774 
 feat(core): mine durable decisions from agent session transcripts by @RaghavChamadiya in #775 
 feat: relevance-ranked decision delivery, SessionStart + edit-time injection with usage feedback by @RaghavChamadiya in #776 
 feat(cli): shared hook efficacy ledger + read-after-served adoption KPI by @RaghavChamadiya in #777 
 feat(mcp): ground get_answer synthesis in the body it serves; slim low-confidence misses by @RaghavChamadiya in #778 
 feat(mcp): ground data-shape questions in the field set mined from source by @RaghavChamadiya in #779 
 feat(mcp): surface alias keys a documented data-shape omits by @RaghavChamadiya in #780 
 feat(generation): FAQ-weighted docs budget tilts depth toward asked-about modules by @RaghavChamadiya in #781 
 Fix CI: track widened augment matcher in hook config tests by @RaghavChamadiya in #782 
 docs: hooks guide + "learns from your usage" section by @RaghavChamadiya in #784 
 feat(coverage): per-test contexts ingestion substrate (test-to-code map) by @RaghavChamadiya in #789 
 feat(coverage): persist the per-test test-to-code map + one ingestion entry point by @RaghavChamadiya in #790 
 feat(coverage): repowise impacted-tests command by @RaghavChamadiya in #792 
 chore: use full AGPL-3.0 license text so GitHub detects it by @RaghavChamadiya in #794 
 feat(coverage): coverage-backed missing-test signal by @RaghavChamadiya in #793 
 fix(update): persist wiki_symbols on incremental updates by @RaghavChamadiya in #795 
 fix(mcp): verify symbol bounds before serving live slices in get_answer by @RaghavChamadiya in #796 
 fix(search): lead hybrid results with concept pages for prose queries by @RaghavChamadiya in #797 
 feat(docker): lean MCP-only image for MCP hosts and directories by @RaghavChamadiya in #800 
 chore(glama): add glama.json to claim the MCP server listing by @RaghavChamadiya in #802 
 feat(answer): flow-shaped answers via graph path between named endpoints by @RaghavChamadiya in #804 
 fix(update): persist graph_edges on incremental update by @RaghavChamadiya in #806 
 fix(graph): keep max confidence on edge upsert by @RaghavChamadiya in #807 
 feat(mcp): forgive get_symbol(id=) and ground a hedged get_answer on the served body by @RaghavChamadiya in #783 
 Explain the agent-authorship share on the contributors strip by @swati510 in #799 
 feat(health): deduct open performance findings from the performance score by @swati510 in #801 
 feat: agent co-author detection + derived decision scope by @swati510 in #803 
 fix(graph): execution-flow picker on the module overview; hierarchical layout guardrails by @swati510 in #805 
 test(graph): type-complete node fixtures in graph-flow tests by @swati510 in #808 
 test: fix two stale unit tests failing on main CI by @swati510 in #809 
 release: v0.31.0 - coverage test intelligence, decisions from agent sessions, grounded get_answer by @RaghavChamadiya in #810 
 
 Full Changelog : v0.30.0...v0.31.0

</details>