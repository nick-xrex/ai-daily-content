---
id: inbox_b340a666
date: 2026-06-22
source_ref: "[[00-inbox/2026-06-22/2203-ruflo-releases-v3-14-0-testgen-test-driven-repair-via-h-ad69]]"
title: "v3.14.0 — testgen Test-Driven Repair via headless `claude -p`"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.14.0
source: ruflo-releases
published_at: 2026-06-22T21:16:30+00:00
fetched_at: 2026-06-23T00:25:15.501899+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "ruflo v3.14.0 推出 Test-Driven Repair 功能，透過 headless `claude -p` 自動修復失敗的測試。工作流程：執行失敗測試 → 以受限工具集（Read、Edit、Bash）和硬性預算上限（預設 $5）生成修復建議 → 驗證測試通過。成本分層：Haiku $0.02–$0.20、Sonnet $0.30–$2.00、Opus $1.50–$8.00 每次嘗試。安全機制包括 --confirm 必填、15 分鐘硬逾時、禁止修改測試或新增相依。實驗驗證：add(a,b) 漏洞的測試集從 2/2 失敗修復至 2/2 通過。CLI 用法：`npx ruflo hooks testgen tdd-repair --repo . --test tests/failing.test.ts --confirm`。"
key_points:
  - "退出碼作為適應度函數：測試通過/失敗是唯一的評定標準，無需 LLM 判斷官"
  - "硬性預算上限防止成本失控：--max-budget-usd 強制執行，預設 $5 上限在大多數 Haiku 修復內完成"
  - "受限工具集 (Read/Edit/Bash only) 隔離風險：無網路、無 MCP、禁止任意寫入，只讀取測試→編輯原始碼→驗證"
tags: [test-driven-repair, claude-code, automation, budget-controlled-agents, fitness-function-pattern]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.14.0 — testgen Test-Driven Repair via headless `claude -p`

ruflo v3.14.0 推出 Test-Driven Repair 功能，透過 headless `claude -p` 自動修復失敗的測試。工作流程：執行失敗測試 → 以受限工具集（Read、Edit、Bash）和硬性預算上限（預設 $5）生成修復建議 → 驗證測試通過。成本分層：Haiku $0.02–$0.20、Sonnet $0.30–$2.00、Opus $1.50–$8.00 每次嘗試。安全機制包括 --confirm 必填、15 分鐘硬逾時、禁止修改測試或新增相依。實驗驗證：add(a,b) 漏洞的測試集從 2/2 失敗修復至 2/2 通過。CLI 用法：`npx ruflo hooks testgen tdd-repair --repo . --test tests/failing.test.ts --confirm`。

### 重點
- 退出碼作為適應度函數：測試通過/失敗是唯一的評定標準，無需 LLM 判斷官
- 硬性預算上限防止成本失控：--max-budget-usd 強制執行，預設 $5 上限在大多數 Haiku 修復內完成
- 受限工具集 (Read/Edit/Bash only) 隔離風險：無網路、無 MCP、禁止任意寫入，只讀取測試→編輯原始碼→驗證

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.14.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

✨ New feature — Test-Driven Repair 
 Closes the loop the existing TDD plugins didn't: we generate tests; now we also fix the code to satisfy them. Inspired by agent-harness-generator ADR-175 ; implemented via headless `claude -p` for tighter integration with our stack. 
 What you can do now 
 ```bash 
 Failing CI test → verified fix PR for pennies 
 npx ruflo@latest hooks testgen tdd-repair 
--repo . 
--test tests/failing.test.ts 
--test-command "npx vitest run tests/failing.test.ts" 
--confirm 
``` 
 Or call `mcp__claude-flow__testgen_tdd_repair` from any agent. 
 How it works 
 
 Pre-flight: run the test command. Refuse if it already passes (catches `--test-command` typos). 
 Spawn `claude -p` with capability-restricted toolset (`--allowedTools Read,Edit,Bash`) and hard-capped budget (`--max-budget-usd`). 
 Focused prompt: read the failing test, fix the source, do NOT modify the test, verify by running it. 
 Re-run the test. The exit code IS the fitness function — no LLM-as-judge. 
 If green: emit success + per-attempt usage (`cost_usd`). If red after `--max-attempts`: emit failure receipts; workspace left as-is for review. 
 
 Safety posture 
 
 `--confirm` REQUIRED (dry-run otherwise) 
 Hard `--max-budget-usd` cap (default $5) 
 `--allowedTools Read,Edit,Bash` (no MCP, no network, no arbitrary writes) 
 Prompt forbids modifying the test or adding dependencies 
 15 min hard timeout 
 
 Smoke proof 
 `docs/benchmarks/tdd-repair/SMOKE-2026-06-22.md` — built fixture with `add(a,b) → a-b` bug; pre-repair 2/2 fail, post-repair 2/2 pass. 
 Cost ladder 
 
 
 
 Tier 
 Model 
 Per-attempt typical 
 
 
 
 
 1 
 Haiku (default) 
 $0.02 – $0.20 
 
 
 2 
 Sonnet 
 $0.30 – $2.00 
 
 
 3 
 Opus 
 $1.50 – $8.00 
 
 
 
 Conformant mode (`--no-test-oracle`) 
 Scoped for a follow-up ADR. Today `--no-test-oracle` returns a clear config error. 
 Distribution 
 
 
 
 Package 
 latest 
 alpha 
 v3alpha 
 
 
 
 
 `@claude-flow/cli` 
 3.14.0 
 3.14.0 
 3.14.0 
 
 
 `claude-flow` 
 3.14.0 
 3.14.0 
 3.14.0 
 
 
 `ruflo` 
 3.14.0 
 3.14.0 
 3.14.0 
 
 
 
 Cross-references 
 
 🔗 Inspired by: agent-harness-generator/packages/darwin-mode ADR-175 
 🔗 Smoke receipts: docs/benchmarks/tdd-repair/SMOKE-2026-06-22.md 
 🔗 Companion: testgen `test-gaps` skill (gap → fix loop scoped for next iteration) 
 
 
 🤖 Generated with RuFlo

</details>