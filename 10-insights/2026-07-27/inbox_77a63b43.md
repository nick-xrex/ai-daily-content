---
id: inbox_77a63b43
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_77a63b43]]"
title: "v3.32.17 — PlanFlip + MemPoison gates (#2752 dream-cycle)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.17
source: ruflo-releases
published_at: 2026-07-27T02:45:24+00:00
fetched_at: 2026-07-28T01:16:18.463046+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.17 實裝 PlanFlip 與 MemPoison 兩個安全防護閘門（dream-cycle #2752）。PlanFlip gate 透過 `ruflo security scan-plan` 掃描計劃中被注入會改變權限的步驟，支援 --strict 模式；MemPoison gate 透過 `ruflo memory store --scan-content` 在持久化前拒絕有害值，並可全局啟用 RUFLO_MEMORY_SCAN_ON_WRITE=1。兩個 gate 都復用 ChannelGuard 的共用掃描目錄（injection-catalog），新增短語一次增強四個防護面（composition-scan、channel-scan、scan-plan、memory-store）。驗證通過 6/6 回歸測試 + 3 個 CLI E2E，與 #2783 共計 21/21 安全測試；exit 2 信號機制適合 shell 集成。"
key_points:
  - "PlanFlip gate：`ruflo security scan-plan` 偵測計劃步驟注入攻擊，exit 2 信號阻止不安全計劃分發"
  - "MemPoison gate：`ruflo memory store --scan-content` 拒寫有害記憶值，RUFLO_MEMORY_SCAN_ON_WRITE=1 全局激活"
  - "掃描目錄共用設計：16 個 injection phrase + ChannelGuard scanner 修改一處同步強化四個防護面，提高代碼複用性"
tags: [security-gate, plan-injection, memory-poisoning, shared-scanner]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.17 — PlanFlip + MemPoison gates (#2752 dream-cycle)

Ruflo v3.32.17 實裝 PlanFlip 與 MemPoison 兩個安全防護閘門（dream-cycle #2752）。PlanFlip gate 透過 `ruflo security scan-plan` 掃描計劃中被注入會改變權限的步驟，支援 --strict 模式；MemPoison gate 透過 `ruflo memory store --scan-content` 在持久化前拒絕有害值，並可全局啟用 RUFLO_MEMORY_SCAN_ON_WRITE=1。兩個 gate 都復用 ChannelGuard 的共用掃描目錄（injection-catalog），新增短語一次增強四個防護面（composition-scan、channel-scan、scan-plan、memory-store）。驗證通過 6/6 回歸測試 + 3 個 CLI E2E，與 #2783 共計 21/21 安全測試；exit 2 信號機制適合 shell 集成。

### 重點
- PlanFlip gate：`ruflo security scan-plan` 偵測計劃步驟注入攻擊，exit 2 信號阻止不安全計劃分發
- MemPoison gate：`ruflo memory store --scan-content` 拒寫有害記憶值，RUFLO_MEMORY_SCAN_ON_WRITE=1 全局激活
- 掃描目錄共用設計：16 個 injection phrase + ChannelGuard scanner 修改一處同步強化四個防護面，提高代碼複用性

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.17)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.17 — PlanFlip + MemPoison gates (#2752 dream-cycle)

Two more dream-cycle security gates, reusing ChannelGuard's detector. 
 Added 
 PlanFlip gate — ruflo security scan-plan 
Scans agent-emitted plans (inline -p or --plan-file &lt;path&gt; ) for injected steps that would shift the plan's authority. Gate FIRES on high-severity findings (default) or ANY finding ( --strict ). Exit 2 signals fire so callers can gate distribution. 
 MemPoison gate — ruflo memory store --scan-content 
Runs the scanner on the value BEFORE persistence and refuses the write with exit 2 on any finding. Also activates globally via RUFLO_MEMORY_SCAN_ON_WRITE=1 for safety-critical flows. Refusal is authoritative — does not fall through to the sql.js path. 
 Both gates reuse ChannelGuard's scanChannelMessage from the shared security/injection-catalog + channel-guard modules — adding a phrase to the catalog now strengthens all four surfaces at once (composition-scan, channel-scan, scan-plan, memory-store). 
 Verification 
 
 Regression tests: 6/6 for #2752 (detector + 3 CLI wire E2E via real execFileSync ) 
 Total security tests ( #2752 + #2783 ): 21/21 
 E2E on shipped CLI: memory store with injected value → exit 2, plan file with injected step → exit 2 with FIRE verdict 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.17 
 Refs: dream-cycle #2752 (2026-07-21).

</details>