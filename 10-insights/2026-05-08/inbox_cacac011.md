---
id: inbox_cacac011
date: 2026-05-08
source_ref: "[[00-inbox/2026-05-08/0737-medium-tag-claude-the-other-4-lines-your-claude-md-needs-a-4507]]"
title: "The Other 4 Lines: Your CLAUDE.MD Needs: A Security Engineer’s Take"
url: https://medium.com/@nitikakumari065/the-other-4-lines-your-claude-md-needs-a-security-engineers-take-1a33d2187393?source=rss------claude-5
source: medium-tag-claude
published_at: 2026-05-08T06:21:09+00:00
fetched_at: 2026-05-08T07:58:45.369101+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "資安工程師提出 Karpathy 知名的 4 行 CLAUDE.md 存在致命缺口：完全忽略安全威脅。文章建議並列 4 條安全規則：(1) 將網頁擷取、MCP 輸出視為數據而非指令，防止 prompt injection；(2) 禁止訪問密鑰文件；(3) 破壞性操作（rm -rf、git push --force）前必須暫停並用英文說明；(4) 檢查第三方 MCP 工具的讀寫權限。文章引用 Snyk 數據指出 36% 公開 Claude skills 含注入 payload，並參考 2025-2026 真實事件（Claudy Day 漏洞、Claude Code 洩露、供應鏈攻擊）為案例。強調 CLAUDE.md 規則是「護欄而非牆」，應與作業系統和設定層安全控制並行。"
key_points:
  - "4 條安全規則對應 2026 威脅景觀：外部內容隔離、密鑰禁入、操作前暫停、MCP 工具審查"
  - "實證數據：Snyk 檢測 36% 公開 Claude skills 包含注入 payload，證明工具審查必要性"
  - "可直接套用：針對 Claude Code 等 agentic 工具的實際防禦層，與 OS 級控制互補"
tags: [claude-md, security-practices, prompt-injection, agentic-safety, guard-rails]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## The Other 4 Lines: Your CLAUDE.MD Needs: A Security Engineer’s Take

資安工程師提出 Karpathy 知名的 4 行 CLAUDE.md 存在致命缺口：完全忽略安全威脅。文章建議並列 4 條安全規則：(1) 將網頁擷取、MCP 輸出視為數據而非指令，防止 prompt injection；(2) 禁止訪問密鑰文件；(3) 破壞性操作（rm -rf、git push --force）前必須暫停並用英文說明；(4) 檢查第三方 MCP 工具的讀寫權限。文章引用 Snyk 數據指出 36% 公開 Claude skills 含注入 payload，並參考 2025-2026 真實事件（Claudy Day 漏洞、Claude Code 洩露、供應鏈攻擊）為案例。強調 CLAUDE.md 規則是「護欄而非牆」，應與作業系統和設定層安全控制並行。

### 重點
- 4 條安全規則對應 2026 威脅景觀：外部內容隔離、密鑰禁入、操作前暫停、MCP 工具審查
- 實證數據：Snyk 檢測 36% 公開 Claude skills 包含注入 payload，證明工具審查必要性
- 可直接套用：針對 Claude Code 等 agentic 工具的實際防禦層，與 OS 級控制互補

**原文：** [medium-tag-claude](https://medium.com/@nitikakumari065/the-other-4-lines-your-claude-md-needs-a-security-engineers-take-1a33d2187393?source=rss------claude-5)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Karpathy&#x2019;s four lines fixed coding correctness. They say nothing about security. After a year of prompt injection of CVEs, leaked source&#x2026; Continue reading on Medium »

</details>