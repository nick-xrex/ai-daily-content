---
id: inbox_ffc26275
date: 2026-07-28
source_ref: "[[00-inbox/.../inbox_ffc26275]]"
title: "Ruflo v3.32.26 — Safer Self-Improvement"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.26
source: ruflo-releases
published_at: 2026-07-28T20:29:19+00:00
fetched_at: 2026-07-29T03:36:50.913521+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.26 發布，引入自我改進控制飛輪機制。新版本讓 Ruflo 能在不改變現有配置的前提下測試檢索策略改進。採用 evaluate → review → promote 三階段流程，候選項目必須通過簽署的收據和明確 --confirm 命令才能推廣，絕不自動推廣。支持對比品質、延遲、token 使用、失敗率與成本限制，並通過收據和推廣歷史進行完整審計。框架核心是將自我改進決策權保留在人類手中，避免優化器完全接管；Darwin 可探索和提議，但 Ruflo 負責判斷安全性。目前僅應用於 bounded retrieval-policy tuning，tool-policy 和 model-policy 演進、以及 unattended autopilot 仍待安全和成本控制就位。"
key_points:
  - "Evaluate-Review-Promote 三階段飛輪框架：評估不改變活躍策略，推廣需簽署收據 + --confirm，拒絕過期/已改變/不受信任/已使用的收據"
  - "簽署的收據能偵測評估證據篡改，支持一次性原子推廣與一致性崩潰恢復，資源限制在候選評估前執行"
  - "當前僅限 bounded retrieval-policy 調優；tool-policy、model-policy 演進和無人值守自動推廣尚在資安與支出控制完善階段"
tags: [ruflo, self-improvement, safety, human-in-the-loop, retrieval-policy]
topics: []
importance: 5
novelty: 5
insight_quality: 5
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## Ruflo v3.32.26 — Safer Self-Improvement

Ruflo v3.32.26 發布，引入自我改進控制飛輪機制。新版本讓 Ruflo 能在不改變現有配置的前提下測試檢索策略改進。採用 evaluate → review → promote 三階段流程，候選項目必須通過簽署的收據和明確 --confirm 命令才能推廣，絕不自動推廣。支持對比品質、延遲、token 使用、失敗率與成本限制，並通過收據和推廣歷史進行完整審計。框架核心是將自我改進決策權保留在人類手中，避免優化器完全接管；Darwin 可探索和提議，但 Ruflo 負責判斷安全性。目前僅應用於 bounded retrieval-policy tuning，tool-policy 和 model-policy 演進、以及 unattended autopilot 仍待安全和成本控制就位。

### 重點
- Evaluate-Review-Promote 三階段飛輪框架：評估不改變活躍策略，推廣需簽署收據 + --confirm，拒絕過期/已改變/不受信任/已使用的收據
- 簽署的收據能偵測評估證據篡改，支持一次性原子推廣與一致性崩潰恢復，資源限制在候選評估前執行
- 當前僅限 bounded retrieval-policy 調優；tool-policy、model-policy 演進和無人值守自動推廣尚在資安與支出控制完善階段

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.26)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Ruflo v3.32.26 — Safer Self-Improvement

Ruflo v3.32.26 — Safer Self-Improvement 
 Ruflo can now test improvements to its retrieval behavior without changing the configuration you are currently using. 
 This release introduces a controlled flywheel: 
 evaluate → review → promote
 
 Ruflo evaluates candidate settings, records the results in a verifiable receipt, and waits for you to approve an accepted candidate. Nothing is promoted automatically. 
 Why this matters 
 Self-improvement should not mean handing control to an optimizer. 
 With v3.32.26, you can: 
 
 test retrieval-policy improvements against held-out tasks; 
 compare quality, latency, token use, failures, and cost limits; 
 inspect the evidence before making a change; 
 activate an accepted candidate with an explicit command; 
 audit what changed through receipts and promotion history. 
 
 Darwin can explore and propose candidates, but Ruflo remains responsible for deciding whether a candidate is safe to promote. 
 Install or upgrade 
 npm install --global ruflo@3.32.26
ruflo --version 
 You can also try this release without a global installation: 
 npx ruflo@3.32.26 metaharness flywheel status --project-root . 
 Try the flywheel 
 Check the current state: 
 ruflo metaharness flywheel status --project-root . 
 Run a local evaluation: 
 ruflo metaharness flywheel run \
 --project-root . \
 --proposer local \
 --sample 40 \
 --private-key /path/to/flywheel-private.pem \
 --public-key /path/to/flywheel-public.pem 
 Review the results: 
 ruflo metaharness flywheel receipts --project-root . 
ruflo metaharness flywheel history --project-root . 
 Promote an accepted result: 
 ruflo metaharness flywheel promote &lt; receipt-id &gt; \
 --project-root . \
 --public-key /path/to/flywheel-public.pem \
 --confirm 
 The end-user quick start includes signing-key setup and a complete walkthrough. 
 Also new 
 
 First-class metaharness flywheel commands in the CLI and MCP. 
 Darwin candidate evolution through metaharness evolve . 
 Stable benchmark creation and verification through metaharness bench . 
 Signed receipts that detect altered evaluation evidence. 
 Atomic, one-time promotion with consistent crash recovery. 
 Safe local operation when the optional Darwin or Flywheel packages are not installed. 
 
 Safe by default 
 
 Evaluation never changes the active policy. 
 Promotion requires an accepted receipt and explicit --confirm . 
 Stale, changed, untrusted, or already-used receipts are rejected. 
 Candidate resource limits are enforced before candidates are considered. 
 Darwin failures do not silently become Darwin-authorized promotions. 
 Automatic unattended promotion is not enabled in this release. 
 
 v3.32.26 currently applies the new loop to bounded retrieval-policy tuning. Tool-policy evolution, model-policy evolution, and unattended autopilot remain disabled until their separate security and spending controls are ready. 
 Compatibility 
 This is a backward-compatible patch release. Existing Ruflo workflows continue to work, and the new flywheel remains opt-in. 
 Published packages: 
 ruflo@3.32.26
claude-flow@3.32.26
@claude-flow/cli@3.32.26
 
 Validation 
 The release passed the focused flywheel suite, signed-receipt and tamper checks, stale-state and crash-recovery tests, resource-limit tests, and a 100-way concurrent promotion test that produced exactly one successful promotion. 
 Learn more 
 
 End-user quick start 
 ADR-322 architecture and safety model 
 Implementation PR #2817 
 Full changelog

</details>