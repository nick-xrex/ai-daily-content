---
id: inbox_a9f9cac5
date: 2026-07-27
source_ref: "[[00-inbox/.../inbox_a9f9cac5]]"
title: "v3.32.16 — ChannelGuard companion (#2783 dream-cycle pair complete)"
url: https://github.com/ruvnet/ruflo/releases/tag/v3.32.16
source: ruflo-releases
published_at: 2026-07-27T02:36:33+00:00
fetched_at: 2026-07-28T01:16:18.464366+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Ruflo v3.32.16 ChannelGuard 完成 dream-cycle #2783 ADR-320 建議（Composition Inspector v3.32.15 + 本版本）。推出 `ruflo security channel-scan` 對代理間訊息進行確定性掃描（無 LLM），基於 arXiv 2607.19430 研究（individually-safe 代理仍可通過訊息通道傳播注入）。檢測四種攻擊簽名：(1) 注入短語（16 個已知短語與 composition-scan 共用）、(2) 角色轉換（system: / assistant: / user: 標記在訊息體內）、(3) 編碼負載（長 base64 / hex 序列）、(4) 零寬與雙向 unicode（U+200B、U+200C、U+200D、U+FEFF、U+202A-E、U+2066-9）。支援 `ruflo security channel-scan -m \"...\"` 與 `--message-file` 用法，exit 0 = 安全、2 = 檢出。通過 ChannelGuard 9/9 + Composition Inspector 6/6，共 15/15 測試。"
key_points:
  - "確定性掃描四種攻擊簽名：注入短語、角色轉換、編碼負載、零寬 unicode，無 LLM 依賴確保可靠性"
  - "基於 arXiv 2607.19430 研究：inter-agent 訊息邊界是注入風險點，每跳都需防護"
  - "CLI 友善設計：exit 0/2 信號機制適合 shell 集成（channel-scan && forward 模式）"
tags: [channel-security, inter-agent-safety, prompt-injection]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## v3.32.16 — ChannelGuard companion (#2783 dream-cycle pair complete)

Ruflo v3.32.16 ChannelGuard 完成 dream-cycle #2783 ADR-320 建議（Composition Inspector v3.32.15 + 本版本）。推出 `ruflo security channel-scan` 對代理間訊息進行確定性掃描（無 LLM），基於 arXiv 2607.19430 研究（individually-safe 代理仍可通過訊息通道傳播注入）。檢測四種攻擊簽名：(1) 注入短語（16 個已知短語與 composition-scan 共用）、(2) 角色轉換（system: / assistant: / user: 標記在訊息體內）、(3) 編碼負載（長 base64 / hex 序列）、(4) 零寬與雙向 unicode（U+200B、U+200C、U+200D、U+FEFF、U+202A-E、U+2066-9）。支援 `ruflo security channel-scan -m "..."` 與 `--message-file` 用法，exit 0 = 安全、2 = 檢出。通過 ChannelGuard 9/9 + Composition Inspector 6/6，共 15/15 測試。

### 重點
- 確定性掃描四種攻擊簽名：注入短語、角色轉換、編碼負載、零寬 unicode，無 LLM 依賴確保可靠性
- 基於 arXiv 2607.19430 研究：inter-agent 訊息邊界是注入風險點，每跳都需防護
- CLI 友善設計：exit 0/2 信號機制適合 shell 集成（channel-scan && forward 模式）

**原文：** [ruflo-releases](https://github.com/ruvnet/ruflo/releases/tag/v3.32.16)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# v3.32.16 — ChannelGuard companion (#2783 dream-cycle pair complete)

Completes the dream-cycle #2783 ADR-320 recommendation: Composition Inspector (v3.32.15) + ChannelGuard (this release). 
 Added 
 ruflo security channel-scan — deterministic (no LLM) inter-agent message scanner. arXiv 2607.19430: individually-safe LLM agents propagate injection payloads through inter-agent message channels; per-message safety checks pass at each hop. ChannelGuard closes the gap by scanning content at the routing boundary. 
 Four attack signatures: 
 
 Injection-phrase — shared 16-phrase catalog with composition-scan (new src/security/injection-catalog.ts ; a phrase added there strengthens both surfaces). 
 Role-shift — system: / assistant: / user: markers appearing INSIDE the message body (start-of-message preambles allowed). 
 Encoded-payload — long base64/hex runs that could hide obfuscated instructions. 
 Zero-width/bidi unicode — U+200B, U+200C, U+200D, U+FEFF, U+202A-E, U+2066-9 — zero legitimate use in agent messages. 
 
 Usage: 
 ruflo security channel-scan -m "...message text..."
ruflo security channel-scan --message-file ./inbox/msg-1234.txt
 
 Exit codes: 0 safe, 2 flagged — shell-integration friendly ( channel-scan &amp;&amp; forward skips flagged messages). 
 Verification 
 
 Regression tests: 9/9 for ChannelGuard, 6/6 for Composition Inspector, 15/15 total . 
 E2E on malicious message → 5 findings across 3 signature categories. 
 E2E on benign handoff → SAFE, 0 findings. 
 
 Upgrade 
 npx ruflo@latest --version # → 3.32.16 
 Refs: dream-cycle #2783 .

</details>