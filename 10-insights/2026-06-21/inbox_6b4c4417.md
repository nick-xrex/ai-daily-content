---
id: inbox_6b4c4417
date: 2026-06-21
source_ref: "[[00-inbox/.../inbox_6b4c4417]]"
title: "v13.7.1"
url: https://github.com/thedotmack/claude-mem/releases/tag/v13.7.1
source: claude-mem-releases
published_at: 2026-06-21T20:16:23+00:00
fetched_at: 2026-06-22T01:24:07.843812+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "claude-mem v13.7.1 發佈，著重清理和可靠性改進，無新使用者功能。主要修復：Node 版本要求從 >=20.0.0 升至 >=20.12.0，因舊版本中 util.parseEnv 未定義導致靜默憑證加載失敗。內部改動包括 Ponytail 審計移除 10.4k 行死碼、新增 OpenAICompatibleProvider 基類統一 Gemini 和 OpenRouter 會話週期、多項基礎設施去重複化（parseRetryAfterMs 3→1、waitForExit 2→1 等）。此版本著重代碼品質而非功能擴展。"
key_points:
  - "Node 版本要求提升至 >=20.12.0，修復 util.parseEnv 相容性導致的靜默憑證失敗"
  - "Ponytail 審計移除 10.4k 行死碼，新增 OpenAICompatibleProvider 統一多廠商供應商支援"
  - "基礎設施去重複化：parseRetryAfterMs (3→1)、waitForExit (2→1)、request-auth (2→1)、resolveQueue (2→1)"
tags: [claude-mem, maintenance, code-quality, reliability]
topics: [foundation_models.claude]
importance: 3
novelty: 1
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v13.7.1

claude-mem v13.7.1 發佈，著重清理和可靠性改進，無新使用者功能。主要修復：Node 版本要求從 >=20.0.0 升至 >=20.12.0，因舊版本中 util.parseEnv 未定義導致靜默憑證加載失敗。內部改動包括 Ponytail 審計移除 10.4k 行死碼、新增 OpenAICompatibleProvider 基類統一 Gemini 和 OpenRouter 會話週期、多項基礎設施去重複化（parseRetryAfterMs 3→1、waitForExit 2→1 等）。此版本著重代碼品質而非功能擴展。

### 重點
- Node 版本要求提升至 >=20.12.0，修復 util.parseEnv 相容性導致的靜默憑證失敗
- Ponytail 審計移除 10.4k 行死碼，新增 OpenAICompatibleProvider 統一多廠商供應商支援
- 基礎設施去重複化：parseRetryAfterMs (3→1)、waitForExit (2→1)、request-auth (2→1)、resolveQueue (2→1)

**原文：** [claude-mem-releases](https://github.com/thedotmack/claude-mem/releases/tag/v13.7.1)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v13.7.1

Cleanup + reliability release. No new user-facing features. 
 Fixed 
 
 Node version floor corrected. engines.node now requires &gt;=20.12.0 to match the stdlib util.parseEnv adopted during the audit. It previously advertised &gt;=20.0.0 , where util.parseEnv is undefined — causing silent credential-load failures (and a hard throw in saveClaudeMemEnv ) on Node 20.0–20.11. Fixed in both the npm package and the generated plugin manifest. ( #3021 ) 
 
 Changed (internal) 
 
 Ponytail audit — −10.4k lines of dead/redundant code removed across 8 slices (worker HTTP routes, agents, session/rate-limit, search pipeline, providers, storage/shared). 
 Provider refactor. New OpenAICompatibleProvider base class unifies the Gemini and OpenRouter session lifecycle; per-provider behavior preserved via abstract flags ( requireNonEmptyToTruncate , forwardEmptyMessageResponse ). 
 Infra deduplication. Consolidated parseRetryAfterMs (3→1), waitForExit (2→1), request-auth helpers (2→1), and resolveQueue (2→1); a CREDENTIAL_KEYS loop replaces three duplicated copy blocks. 
 Worker-restart hardening via a single-spawn gate. 
 Deterministic dependency closure for the bundled plugin runtime. 
 
 Full Changelog : v13.7.0...v13.7.1

</details>