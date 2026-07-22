---
id: inbox_547e02ca
date: 2026-06-08
source_ref: "[[00-inbox/.../inbox_547e02ca]]"
title: "v0.18.0"
url: https://github.com/repowise-dev/repowise/releases/tag/v0.18.0
source: repowise-releases
published_at: 2026-06-08T15:13:14+00:00
fetched_at: 2026-07-22T01:05:31.855016+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Repowise v0.18.0（2026年6月8日發布）標誌著產品價值主張從原始API成本轉向代幣效率指標。核心更新包括：(1) 實現每個MCP工具的計數對照代幣節省追蹤（per-tool savings ledger），量化智能體工作流的優化收益；(2) 引入Model-aware節省定價與視覺化，在成本頁面與代理資訊卡上展示節省成果（Hero results card）；(3) 部署速率限制感知的429退避與慷慨預設值，增強提供商可靠性；(4) 提供共享UI/server構建塊供網頁界面複用。版本聚焦於幫助開發者量化與理解多智能體系統中的代幣效率收益，以計數對照概念區分潛在節省與實際節省。"
key_points:
  - "每個MCP工具計數對照代幣節省追蹤與統一帳簿記錄（#421）：新指標量化智能體優化效果"
  - "Model-aware節省定價 + Hero結果卡在成本頁面展示（#419、#422）：從API成本轉向代幣效率視覺化"
  - "Retry-after感知的429退避 + 慷慨速率限制預設值（#417）：提升提供商可靠性與減少失敗重試"
tags: [repowise, mcp-integration, cost-tracking, efficiency-measurement, token-savings]
topics: [agents.mcp]
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v0.18.0

Repowise v0.18.0（2026年6月8日發布）標誌著產品價值主張從原始API成本轉向代幣效率指標。核心更新包括：(1) 實現每個MCP工具的計數對照代幣節省追蹤（per-tool savings ledger），量化智能體工作流的優化收益；(2) 引入Model-aware節省定價與視覺化，在成本頁面與代理資訊卡上展示節省成果（Hero results card）；(3) 部署速率限制感知的429退避與慷慨預設值，增強提供商可靠性；(4) 提供共享UI/server構建塊供網頁界面複用。版本聚焦於幫助開發者量化與理解多智能體系統中的代幣效率收益，以計數對照概念區分潛在節省與實際節省。

### 重點
- 每個MCP工具計數對照代幣節省追蹤與統一帳簿記錄（#421）：新指標量化智能體優化效果
- Model-aware節省定價 + Hero結果卡在成本頁面展示（#419、#422）：從API成本轉向代幣效率視覺化
- Retry-after感知的429退避 + 慷慨速率限制預設值（#417）：提升提供商可靠性與減少失敗重試

**原文：** [repowise-releases](https://github.com/repowise-dev/repowise/releases/tag/v0.18.0)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v0.18.0

What's Changed 
 
 perf(providers): generous rate-limit defaults + retry-after-aware 429 backoff by @RaghavChamadiya in #417 
 fix(mcp,claude-md): serve curated entry points, cap tour barrels by @RaghavChamadiya in #418 
 feat(costs): model-aware savings pricing + surface MCP savings + hero results card by @RaghavChamadiya in #419 
 feat(overview): surface agent savings card on the repo overview by @RaghavChamadiya in #420 
 feat(mcp): record counterfactual token savings per tool into the unified ledger by @RaghavChamadiya in #421 
 fix(costs): nano-model pricing + lead the Costs page with agent savings by @RaghavChamadiya in #422 
 docs(readme): lead the agent-efficiency benchmark with token reduction, not cost by @RaghavChamadiya in #424 
 feat: shared UI/server building blocks for both web surfaces by @swati510 in #423 
 release: v0.18.0 — curated KG serving blocks, MCP savings, compact init banner by @swati510 in #425 
 
 Full Changelog : v0.17.1...v0.18.0

</details>