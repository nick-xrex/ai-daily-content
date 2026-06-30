---
id: inbox_a13da625
date: 2026-06-29
source_ref: "[[00-inbox/2026-06-29/2234-infoq-main-presentation-million-pdfs-building-a-mod-bb36]]"
title: "Presentation: Million PDFs: Building a Modern Document Infrastructure with Rust and Typst"
url: https://www.infoq.com/presentations/document-infrastructure-rust-typst/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global
source: infoq-main
published_at: 2026-06-29T12:35:00+00:00
fetched_at: 2026-06-29T23:12:51.025887+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Erik Steiger 分享了用 Rust + Typst 無伺服器架構替代 Puppeteer / LaTeX 進行大規模 PDF 生成的方案。新架構將 render 延遲降到 2ms 以下，解決了銀行、製造等規範嚴格行業的傳統 PDF 引擎資源消耗與性能瓶頸問題。該方案借鑒 Git 和 Docker 概念管理範本庫，確保合規性並加速除錯流程，直接應對遺留系統的運營痛點。"
key_points:
  - "Rust + Typst serverless 架構相比 Puppeteer/LaTeX，render 延遲 < 2ms"
  - "範本庫採用 Git + Docker 管理模式，確保文檔生成的可追溯性與合規性"
  - "針對銀行、製造等高規範要求行業，減低資源消耗，提升除錯效率"
tags: [pdf-generation, rust, typst, serverless, document-infrastructure]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Presentation: Million PDFs: Building a Modern Document Infrastructure with Rust and Typst

Erik Steiger 分享了用 Rust + Typst 無伺服器架構替代 Puppeteer / LaTeX 進行大規模 PDF 生成的方案。新架構將 render 延遲降到 2ms 以下，解決了銀行、製造等規範嚴格行業的傳統 PDF 引擎資源消耗與性能瓶頸問題。該方案借鑒 Git 和 Docker 概念管理範本庫，確保合規性並加速除錯流程，直接應對遺留系統的運營痛點。

### 重點
- Rust + Typst serverless 架構相比 Puppeteer/LaTeX，render 延遲 < 2ms
- 範本庫採用 Git + Docker 管理模式，確保文檔生成的可追溯性與合規性
- 針對銀行、製造等高規範要求行業，減低資源消耗，提升除錯效率

**原文：** [infoq-main](https://www.infoq.com/presentations/document-infrastructure-rust-typst/?utm_campaign=infoq_content&utm_source=infoq&utm_medium=feed&utm_term=global)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Erik Steiger discusses the operational pain of legacy PDF generation in regulated banking and manufacturing. He explains how transitioning from resource-heavy engines like Puppeteer and LaTeX to a serverless Rust architecture powered by Typst can drop render latencies below 2ms. He shares how applying Git and Docker concepts to template registries ensures ironclad compliance and rapid debugging. By Erik Steiger

</details>