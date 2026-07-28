---
id: inbox_d7a3714d
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_d7a3714d]]"
title: "v3.32.22 — CI-green hotfix: ADR-125 CLI-flag precedence for RUFLO_MEMORY_SCAN_ON_WRITE (#2794)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.22
source: ruflo-releases
published_at: 2026-07-27T14:11:35+00:00
fetched_at: 2026-07-28T01:14:09.829240+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.32.22 修復 v3.32.17 MemPoison 環境變數配置問題，恢復 CI 綠燈狀態（CI 因此問題紅燈約 5 小時，從 2026-07-27 03:04 UTC 開始）。主要修復：RUFLO_MEMORY_SCAN_ON_WRITE 環境變數讀取改用 nullish coalescing（ctx.flags.scanContent ?? process.env.RUFLO_MEMORY_SCAN_ON_WRITE），確保 CLI 旗標優先級符合 ADR-125 §\"CLI flag wins\" 標準。特別移除 --scan-content 選項的 default: false，讓解析器在未設定時保留 undefined 狀態，這樣 ?? 運算子才能正確落回環境變數。明確指定 --no-scan-content 仍優先於環境變數（三層優先級：CLI explicit > env > default）。ADR-125 審計腳本驗證所有 CLAUDE_FLOW_/RUFLO_ env var 讀取遵循此規則，修復後審計通過。"
key_points:
  - "使用 nullish coalescing (ctx.flags ?? process.env.VAR) 而非 || 運算子實現 CLI-env 優先級；|| 會誤判 0 與 false 為假值"
  - "留下 undefined 狀態讓環境變數可被識別：移除 default: false 使解析器對未設旗標返回 undefined，而非預設值"
  - "ADR-125 審計自動化檢查所有環境變數讀取遵循優先級規則，形成 CI 綠燈看門人"
tags: [config-precedence, env-cli-handling, nullish-coalescing, adr-compliance]
topics: []
importance: 2
novelty: 1
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.22 — CI-green hotfix: ADR-125 CLI-flag precedence for RUFLO_MEMORY_SCAN_ON_WRITE (#2794)

ruflo v3.32.22 修復 v3.32.17 MemPoison 環境變數配置問題，恢復 CI 綠燈狀態（CI 因此問題紅燈約 5 小時，從 2026-07-27 03:04 UTC 開始）。主要修復：RUFLO_MEMORY_SCAN_ON_WRITE 環境變數讀取改用 nullish coalescing（ctx.flags.scanContent ?? process.env.RUFLO_MEMORY_SCAN_ON_WRITE），確保 CLI 旗標優先級符合 ADR-125 §"CLI flag wins" 標準。特別移除 --scan-content 選項的 default: false，讓解析器在未設定時保留 undefined 狀態，這樣 ?? 運算子才能正確落回環境變數。明確指定 --no-scan-content 仍優先於環境變數（三層優先級：CLI explicit > env > default）。ADR-125 審計腳本驗證所有 CLAUDE_FLOW_/RUFLO_ env var 讀取遵循此規則，修復後審計通過。

### 重點
- 使用 nullish coalescing (ctx.flags ?? process.env.VAR) 而非 || 運算子實現 CLI-env 優先級；|| 會誤判 0 與 false 為假值
- 留下 undefined 狀態讓環境變數可被識別：移除 default: false 使解析器對未設旗標返回 undefined，而非預設值
- ADR-125 審計自動化檢查所有環境變數讀取遵循優先級規則，形成 CI 綠燈看門人

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.22)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.22 — CI-green hotfix: ADR-125 CLI-flag precedence for RUFLO_MEMORY_SCAN_ON_WRITE (#2794)

Hotfix for the verification agent's #2794 finding — CI on main was red since 03:04 UTC because v3.32.17's #2752 MemPoison env var didn't match the ADR-125 §"CLI flag wins" pattern the audit script requires. 
 Fixed 
 Restructured the RUFLO_MEMORY_SCAN_ON_WRITE read so ctx.flags.scanContent takes precedence via nullish coalescing, with the exact ADR-125 comment format. Removed default: false from the --scan-content option so the parser leaves it undefined when unset (required for ?? env to see the env value). Explicit --no-scan-content still wins over the env var. 
 Verification 
 
 Audit script: ok: all CLAUDE_FLOW_ / RUFLO_ env var reads have documented CLI-flag precedence** 
 Regression tests still green: planflip-mempoison-2752 (6/6) + memory-search-2790 (4/4) 
 
 Closes: #2794 .

</details>