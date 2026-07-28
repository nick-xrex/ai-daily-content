---
id: inbox_40bb3859
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_40bb3859]]"
title: "v3.32.15 — MCP Composition Inspector (#2783 dream — cross-tool prompt-injection scan)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.15
source: ruflo-releases
published_at: 2026-07-27T02:29:25+00:00
fetched_at: 2026-07-28T01:16:18.465872+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.15 推出 `ruflo security composition-scan` 對 MCP 工具描述集合進行確定性掃描，檢測 ShareLock Shamir 分割提示注入模式（arXiv 2606.27027，dream-cycle #2783）。三種攻擊簽名：(1) 注入短語（16 個已知短語）、(2) 共享片段（跨工具的相同子字符串 ≥N 字符，上限 ≤K 工具，基於攻擊碎片通常僅在 2-3 工具中出現的觀察）、(3) 名稱相似（≤2 編輯距離的 typosquat 攻擊）。用法：`ruflo security composition-scan [--tools-json] [--min-fragment 30] [--top 50]`。在 CLI 自有 350 工具註冊表上測試，population cap 優化將誤報從 152,560 降至 1,788，減少 92 倍。通過 6/6 單元測試 + E2E 驗證，E2E 在合成 4 工具惡意註冊表上三種簽名全部正確觸發。"
key_points:
  - "ShareLock 檢測：三種簽名對應 Shamir 秘密分享模式，捕捉跨工具的協同注入攻擊"
  - "population cap 優化：基於攻擊碎片通常僅在 2-3 工具中出現，誤報從 152,560 → 1,788（92 倍改進）"
  - "共用掃描目錄：16 個 injection phrase 與 PlanFlip / MemPoison / channel-scan 共用，單次修改強化多層防護"
tags: [composition-security, mcp-tools, sharelock-detection, false-positive-reduction]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.15 — MCP Composition Inspector (#2783 dream — cross-tool prompt-injection scan)

Ruflo v3.32.15 推出 `ruflo security composition-scan` 對 MCP 工具描述集合進行確定性掃描，檢測 ShareLock Shamir 分割提示注入模式（arXiv 2606.27027，dream-cycle #2783）。三種攻擊簽名：(1) 注入短語（16 個已知短語）、(2) 共享片段（跨工具的相同子字符串 ≥N 字符，上限 ≤K 工具，基於攻擊碎片通常僅在 2-3 工具中出現的觀察）、(3) 名稱相似（≤2 編輯距離的 typosquat 攻擊）。用法：`ruflo security composition-scan [--tools-json] [--min-fragment 30] [--top 50]`。在 CLI 自有 350 工具註冊表上測試，population cap 優化將誤報從 152,560 降至 1,788，減少 92 倍。通過 6/6 單元測試 + E2E 驗證，E2E 在合成 4 工具惡意註冊表上三種簽名全部正確觸發。

### 重點
- ShareLock 檢測：三種簽名對應 Shamir 秘密分享模式，捕捉跨工具的協同注入攻擊
- population cap 優化：基於攻擊碎片通常僅在 2-3 工具中出現，誤報從 152,560 → 1,788（92 倍改進）
- 共用掃描目錄：16 個 injection phrase 與 PlanFlip / MemPoison / channel-scan 共用，單次修改強化多層防護

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.15)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.15 — MCP Composition Inspector (#2783 dream — cross-tool prompt-injection scan)

First dream-cycle backlog item shipped after the parser scoping fix. 
 Added 
 ruflo security composition-scan — deterministic (no LLM) scanner that reads a set of MCP tool descriptors and flags three attack signatures targeting the ShareLock Shamir-split prompt-injection pattern (arXiv 2606.27027, dream-cycle #2783 ): 
 
 Injection-phrase — 16 known prompt-injection phrases inside a single tool. 
 Shared-fragment — identical substrings ≥ N chars across tool descriptions, capped at ≤ K distinct tools per fragment. Attack fragments live in small conspiracies (2-3 tools); template language shows up in dozens. 
 Name-lookalike — tool names ≤ 2 edits from a trusted ruflo prefix (typosquat mitigation). 
 
 Usage: 
 ruflo security composition-scan # scan the CLI's own MCP tools
ruflo security composition-scan --tools-json X.json # scan a third-party MCP registry
ruflo security composition-scan --min-fragment 30 --top 50
 
 Verification 
 
 Unit tests: 6/6 pass (shared-fragment, injection-phrase, name-lookalike, ruflo-benign-baseline, stats accuracy, minFragment tuning). 
 E2E on synthetic malicious 4-tool registry: all 3 signatures flagged correctly. 
 E2E on the CLI's own 350-tool registry: population cap knocks false-positives 92× (152,560 → 1,788). 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.15 
 Refs: dream-cycle #2783 (2026-07-26).

</details>