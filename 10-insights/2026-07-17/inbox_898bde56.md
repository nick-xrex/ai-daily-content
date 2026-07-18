---
id: inbox_898bde56
date: 2026-07-17
source_ref: "[[00-inbox/.../inbox_898bde56]]"
title: "Presentation: From OTEL to SLMs: Distilling Frontier Model Behaviour from Production Telemetry"
url: https://www.infoq.com/presentations/otel-slm-ai/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-07-17T13:17:00+00:00
fetched_at: 2026-07-18T01:48:33.997789+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "InfoQ 收錄 Ben O'Mahony 的演講，介紹如何超越規則型檢查器，使用 OpenTelemetry 對 AI 驅動的語言伺服器協議（LSP）進行原生代碼檢測，追蹤使用者對程式碼修復的具體行動（接受、拒絕或重新生成）作為隱性訓練標籤。這些行動形成持續的數據飛輪，最終用於將前沿模型能力蒸餾到更便宜的本地小型語言模型（SLM）。該方法將產品遙測與模型優化結合，為代碼編輯工具提供了自動化改進的系統性路徑。"
key_points:
  - "方法：用 OpenTelemetry 追蹤用戶對 AI 程式碼修復的隱性反饋（接受、拒絕、重新生成）"
  - "流程：遙測數據 → 訓練飛輪 → 蒸餾前沿模型能力到本地廉價 SLM"
  - "應用：構建 AI 驅動的 LSP，超越規則型檢查，實現持續自動化改進"
tags: [opentelemetry, slm-distillation, lsp, ai-observability]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: From OTEL to SLMs: Distilling Frontier Model Behaviour from Production Telemetry

InfoQ 收錄 Ben O'Mahony 的演講，介紹如何超越規則型檢查器，使用 OpenTelemetry 對 AI 驅動的語言伺服器協議（LSP）進行原生代碼檢測，追蹤使用者對程式碼修復的具體行動（接受、拒絕或重新生成）作為隱性訓練標籤。這些行動形成持續的數據飛輪，最終用於將前沿模型能力蒸餾到更便宜的本地小型語言模型（SLM）。該方法將產品遙測與模型優化結合，為代碼編輯工具提供了自動化改進的系統性路徑。

### 重點
- 方法：用 OpenTelemetry 追蹤用戶對 AI 程式碼修復的隱性反饋（接受、拒絕、重新生成）
- 流程：遙測數據 → 訓練飛輪 → 蒸餾前沿模型能力到本地廉價 SLM
- 應用：構建 AI 驅動的 LSP，超越規則型檢查，實現持續自動化改進

**原文：** [infoq-main](https://www.infoq.com/presentations/otel-slm-ai/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Presentation: From OTEL to SLMs: Distilling Frontier Model Behaviour from Production Telemetry

Ben O'Mahony discusses building custom AI-powered Language Server Protocols (LSPs) that go beyond standard rule-based checkers. He explains how to instrument AI agents natively with OpenTelemetry to track concrete user actions (accepting, dismissing, or regenerating code fixes) as implicit labels, creating a continuous data flywheel to distill frontier capabilities into cheaper, local SLMs. By Ben O'Mahony

</details>