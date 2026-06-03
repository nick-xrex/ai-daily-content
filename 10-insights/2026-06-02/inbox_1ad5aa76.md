---
id: inbox_1ad5aa76
date: 2026-06-02
source_ref: "[[00-inbox/2026-06-02/0030-ruflo-releases-v3-10-34-security-adr-p1-adr-144-adr-145-8b83]]"
title: "v3.10.34 — Security ADR P1 (ADR-144 / ADR-145 / ADR-146)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.10.34
source: ruflo-releases
published_at: 2026-06-02T09:53:49+00:00
fetched_at: 2026-06-03T00:36:32.140836+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.10.34 發布，實現三項安全相關 ADR 的 P1 階段。ADR-144 引入 AgentAuthorizationPropagator（行動層），實施權限範圍檢查，工具集合單調遞減、委派深度遞減、過期檢查，18 個單元測試。ADR-145 實現 PluginIntegrityVerifier（安裝層），透過 Canonical JSON + SHA-256 hash + Ed25519 簽名驗證確保外掛完整性，信任錨點允許列表支持精確與萬用符匹配，13 個單元測試。ADR-146 在 MCP dispatch 單點植入 ToolOutputGuardrail（內容層），防止注入攻擊，被拒絕欄位標記為 `<rejected-by-guardrail>` 供上層處理，4 個接線測試。三個 ADR 預設均為 OFF（環境變數 `CLAUDE_FLOW_STRICT_GUARDRAIL=true` 控制），將在 v4.0 成為預設啟用。--version 冷啟動時間保持 33ms。"
key_points:
  - "AuthScope envelope：工具集合單調遞減、委派深度檢查、過期驗證，防止權限提升與逃逸"
  - "PluginIntegrityVerifier：Canonical JSON 序列化 + Ed25519 簽名 + 信任錨點機制，確保外掛程式碼來源可信，防止供應鏈攻擊"
  - "多層防護架構：install boundary（程式碼可信）→ action boundary（主體許可）→ content boundary（數據安全），分層降低攻擊面"
tags: [ruflo, security, authorization, plugin-integrity, content-guardrail]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## v3.10.34 — Security ADR P1 (ADR-144 / ADR-145 / ADR-146)

Ruflo v3.10.34 發布，實現三項安全相關 ADR 的 P1 階段。ADR-144 引入 AgentAuthorizationPropagator（行動層），實施權限範圍檢查，工具集合單調遞減、委派深度遞減、過期檢查，18 個單元測試。ADR-145 實現 PluginIntegrityVerifier（安裝層），透過 Canonical JSON + SHA-256 hash + Ed25519 簽名驗證確保外掛完整性，信任錨點允許列表支持精確與萬用符匹配，13 個單元測試。ADR-146 在 MCP dispatch 單點植入 ToolOutputGuardrail（內容層），防止注入攻擊，被拒絕欄位標記為 `<rejected-by-guardrail>` 供上層處理，4 個接線測試。三個 ADR 預設均為 OFF（環境變數 `CLAUDE_FLOW_STRICT_GUARDRAIL=true` 控制），將在 v4.0 成為預設啟用。--version 冷啟動時間保持 33ms。

### 重點
- AuthScope envelope：工具集合單調遞減、委派深度檢查、過期驗證，防止權限提升與逃逸
- PluginIntegrityVerifier：Canonical JSON 序列化 + Ed25519 簽名 + 信任錨點機制，確保外掛程式碼來源可信，防止供應鏈攻擊
- 多層防護架構：install boundary（程式碼可信）→ action boundary（主體許可）→ content boundary（數據安全），分層降低攻擊面

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.10.34)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

v3.10.34 — Security ADR P1 implementations (ADR-144, ADR-145, ADR-146) 
 Three independent P1 components landing the first concrete code from the three security ADRs filed earlier today (ADR-144 / ADR-145 / ADR-146). Each is OFF by default — strict mode becomes default in v4.0 — so existing pipelines keep their exact behaviour. 
 ADR-144 P1 — AgentAuthorizationPropagator (closes #2248 P1) 
 Action-layer security. New module: @claude-flow/security/authorization/propagator . 
 
 AuthScope envelope (principal, granted tools/servers, delegation depth, expiry) 
 wrapOutbound : monotonically-reducing scope — newly granted tools must be a subset of the holder's; depth decrements by ≥1; expiry checked 
 checkToolCall : typed decisions ( tool-not-in-scope / server-not-in-scope / scope-expired / delegation-depth-exhausted ) — never throws, telemetry-friendly 
 verifyServerAuth : fail-closed on missing / empty credentials (P1 permissive accept for non-empty; P4 wires the real validator) 
 Provenance buffer ring-bounded, ready for the P5 telemetry sink 
 makeLegacyPermissiveScope migration shim for legacy callers 
 
 18 unit tests covering every invariant. Verified against published 3.10.34: 
 granted reduced from 3 to 1 — depth 2
escalation refused: scope-cannot-grow
 
 ADR-145 P1 — PluginIntegrityVerifier (closes #2254 P1) 
 Install-layer security. New module: @claude-flow/security/plugins/integrity-verifier . Plus a placeholder v3/@claude-flow/cli/src/plugins/trust/trust-anchors.json for the official-plugin signing key (to be filled in P1.1 when the publish flow is wired). 
 
 Canonical JSON serialisation (deterministic key order) + SHA-256 manifest hash 
 Ed25519 detached signature verification via @noble/ed25519 (probe-and-fall-back — mirrors verify.mjs #1880 pattern so untrusted environments skip rather than throw) 
 Trust-anchor allowlist with exact + wildcard scope matching + expiry 
 Structured VerificationStatus : pass / signature-missing / signature-invalid / manifest-hash-mismatch / unknown-signer / signer-expired 
 Stage-2 semantic-intent scan (SCH defence) lands in P2 
 
 13 unit tests including the round-trip sign→verify and tamper-flip cases. Verified end-to-end: 
 canonicalize a-then-b == b-then-a: true
hashManifest deterministic: true
unsigned manifest → signature-missing
 
 ADR-146 P2 — Guardrail call site in MCP dispatch (closes #2149 follow-up P2) 
 Content-layer security. Wires the ADR-131 ToolOutputGuardrail class into the single MCP dispatch chokepoint at mcp-client.ts::callMCPTool . 
 
 Lazy-resolves @claude-flow/security so the cold-import cost doesn't hit every CLI invocation; falls back to no-op if the module isn't installed (third-party consumers of @claude-flow/cli ) 
 Walks the result object one level deep — matches the flat-record shape of every existing tool. Deeper traversal would change the p99 latency contract. 
 Rejected fields replaced with a typed marker: &lt;rejected-by-guardrail tool="X" category=Y&gt; so callers can surface the rejection rather than silently dropping content 
 Off by default. CLAUDE_FLOW_STRICT_GUARDRAIL=true turns it on; precedence is documented inline so the env-var audit passes without an escape-hatch entry. 
 
 4 wiring tests (legacy passthrough, strict-mode reject of known injection, strict-mode passthrough on safe content, non-object results pass through). Verified end-to-end: 
 $ CLAUDE_FLOW_STRICT_GUARDRAIL=true npx ruflo ...
action: reject (on known indirect-injection payload)
 
 Layering — three orthogonal boundaries 
 Install boundary ADR-145 → Is the code trustworthy enough to load?
Memory-write ADR-145 → Is this agent allowed to write here? (P3+)
Action boundary ADR-144 → Is this agent allowed to act, on this server, now?
Content boundary ADR-131 / ADR-146 → Does this content contain hijack instructions?
 
 Each ADR has its own phased rollout (P1 here; P2-P5 follow). All three flip to default-on in v4.0. 
 Install 
 npx ruflo@latest --version # → ruflo v3.10.34 (33 ms — #2256 fast path intact) 
 All 9 dist-tag pointers ( latest / alpha / v3alpha across @claude-flow/cli , claude-flow , ruflo ) at 3.10.34. @claude-flow/security published as 3.0.0-alpha.9 with all three dist-tags repointed. 
 What didn't change 
 
 --version cold-start: still 33 ms (the #2256 fast path in bin/cli.js and ruflo/bin/ruflo.js is unaffected) 
 MCP stdio cleanliness: still pure JSON-RPC on stdout (ADR-146 P2 deliberately doesn't touch stderr routing) 
 All 4 audits + 2 regression smokes still pass locally — guards added in 3.10.33 (YAML lint + router regex) continue to cover their cases

</details>