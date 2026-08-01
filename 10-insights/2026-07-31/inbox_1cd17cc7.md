---
id: inbox_1cd17cc7
date: 2026-07-31
source_ref: "[[00-inbox/2026-07-31/0614-ruflo-releases-adr-378-379-380-npm-trusted-publishing-s-a19c]]"
title: "ADR-378/379/380 — npm Trusted Publishing, statusline segments, AGNTCY/Outshift integration"
url: https://github.com/ruvnet/ruflo/releases/tag/adr-378-380-agntcy-outshift-integration
source: ruflo-releases
published_at: 2026-07-31T15:30:07+00:00
fetched_at: 2026-08-01T06:19:57.016871+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo ADR-378/379/380 合併完成（PR #2879），npm 版本保持在 3.33.0（非版本發布）。合併三個 ADR：npm Trusted Publishing 工作流（ADR-378）、可選 statusline 使用段落（ADR-379）、AGNTCY/Outshift 運行時整合（ADR-380），涉及 CASA 執行門、CLI 支架、伴生 Rust crate 與 @metaharness/agntcy 套件。重要的是對 CASA 執行門進行了對抗性安全審查，在合併前發現並修復了兩個真實漏洞，確保授權邏輯安全性。後續 PR #2888 進一步確認 @agntcy/slim-bindings 2.0.0-alpha.5 在純 Node 環境下兼容，已驗證 SLIM 伺服器/客戶端啟動無誤。"
key_points:
  - "對抗性安全審查在合併前發現並修復 CASA 執行門的兩個真實漏洞，安全關鍵組件通過獨立審查驗證"
  - "@agntcy/slim-bindings 2.0.0-alpha.5 經驗證兼容純 Node 環境，uniffi-bindgen-react-native 已遷移至 @ubjs/core 與 @ubjs/node"
  - "三個 ADR 統籌發行工作流（npm Trusted Publishing）、UI 可選功能（statusline segments）、運行時授權系統（CASA 編譯與 CLI）"
tags: [adr, security-audit, casa, npm-trusted-publishing, agntcy]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## ADR-378/379/380 — npm Trusted Publishing, statusline segments, AGNTCY/Outshift integration

Ruflo ADR-378/379/380 合併完成（PR #2879），npm 版本保持在 3.33.0（非版本發布）。合併三個 ADR：npm Trusted Publishing 工作流（ADR-378）、可選 statusline 使用段落（ADR-379）、AGNTCY/Outshift 運行時整合（ADR-380），涉及 CASA 執行門、CLI 支架、伴生 Rust crate 與 @metaharness/agntcy 套件。重要的是對 CASA 執行門進行了對抗性安全審查，在合併前發現並修復了兩個真實漏洞，確保授權邏輯安全性。後續 PR #2888 進一步確認 @agntcy/slim-bindings 2.0.0-alpha.5 在純 Node 環境下兼容，已驗證 SLIM 伺服器/客戶端啟動無誤。

### 重點
- 對抗性安全審查在合併前發現並修復 CASA 執行門的兩個真實漏洞，安全關鍵組件通過獨立審查驗證
- @agntcy/slim-bindings 2.0.0-alpha.5 經驗證兼容純 Node 環境，uniffi-bindgen-react-native 已遷移至 @ubjs/core 與 @ubjs/node
- 三個 ADR 統籌發行工作流（npm Trusted Publishing）、UI 可選功能（statusline segments）、運行時授權系統（CASA 編譯與 CLI）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/adr-378-380-agntcy-outshift-integration)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Merge marker for PR #2879 — not an npm version release ( @claude-flow/cli / claude-flow / ruflo remain at 3.33.0 on npm). 
 Full consolidated release notes: https://gist.github.com/ruvnet/d6fc9bea2758049fd87424a2718dec1e 
 See it illustrated: ruflo × AGNTCY — an animated walkthrough 
 Three ADRs merged: npm Trusted Publishing proposal (ADR-378), optional statusline usage segments (ADR-379), and AGNTCY/Outshift runtime integration with real, tested CASA envelope enforcement + CLI scaffolding (ADR-380). Companion: ruvnet/metaharness PR #155 (ADR-240). 
 An adversarial security review found and PR #2879 fixed two real bugs in the CASA enforcement gate before merge — see the gist for details. 
 Update: PR #2888 pins @agntcy/slim-bindings to the confirmed-working pre-release build ( 2.0.0-alpha.5 ) — verified live, a real SLIM server/client bring-up now succeeds under plain Node with zero errors. Not yet in an npx ruflo@latest release; build from main to try it today.

</details>