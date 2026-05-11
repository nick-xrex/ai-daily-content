---
id: inbox_3ddd6446
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_3ddd6446]]"
title: "Built HTML Drive - Google Drive for Claude generated HTML files"
url: https://www.reddit.com/r/ClaudeAI/comments/1t9e2xw/built_html_drive_google_drive_for_claude/
source: reddit-claudeai
published_at: 2026-05-10T18:02:28+00:00
fetched_at: 2026-05-11T02:29:32.565971+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者 invocation02 構建 HTML Drive——讓 Claude 儲存 HTML 檔案的個人雲端平台。核心洞見來自 Anthropic 工程師 Thariq Shihipar：Claude 在互動式 HTML（色彩、排版、交互、圖表）的表現遠優於 markdown，但 HTML 檔案缺乏預設儲存位置。HTML Drive 提供版本控制、分享（私有/邀請/公開）、文件夾組織、即時預覽。設置單純：點擊「Connect agent」獲得 URL，貼入 Claude Code 即可。後端自動生成憑證，無環保變數、無分步配置。已公開示範：用互動式 HTML 呈現 Thariq 的文章、Claude 自編的 devlog。"
key_points:
  - "Markdown 是表現力上限，Claude 的最佳輸出是互動式 HTML（顏色、排版、交互圖表）；傳統檔案系統或 S3 無法長期管理 HTML 成品"
  - "單 URL 設置模式：無環保變數、無配置檔案，後端動態生成憑證，大幅降低 agent 整合複雜度"
  - "完整生命週期：版本控制保留歷史、分享機制支持私有/邀請/公開、圖標預覽提升檔案瀏覽體驗"
tags: [html-generation, claude-code, content-management, interactive-ui]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 5
insight_type: framework
deep_dive_candidate: false
deep_dive_approved: false
---

## Built HTML Drive - Google Drive for Claude generated HTML files

開發者 invocation02 構建 HTML Drive——讓 Claude 儲存 HTML 檔案的個人雲端平台。核心洞見來自 Anthropic 工程師 Thariq Shihipar：Claude 在互動式 HTML（色彩、排版、交互、圖表）的表現遠優於 markdown，但 HTML 檔案缺乏預設儲存位置。HTML Drive 提供版本控制、分享（私有/邀請/公開）、文件夾組織、即時預覽。設置單純：點擊「Connect agent」獲得 URL，貼入 Claude Code 即可。後端自動生成憑證，無環保變數、無分步配置。已公開示範：用互動式 HTML 呈現 Thariq 的文章、Claude 自編的 devlog。

### 重點
- Markdown 是表現力上限，Claude 的最佳輸出是互動式 HTML（顏色、排版、交互圖表）；傳統檔案系統或 S3 無法長期管理 HTML 成品
- 單 URL 設置模式：無環保變數、無配置檔案，後端動態生成憑證，大幅降低 agent 整合複雜度
- 完整生命週期：版本控制保留歷史、分享機制支持私有/邀請/公開、圖標預覽提升檔案瀏覽體驗

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t9e2xw/built_html_drive_google_drive_for_claude/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Built HTML Drive - Google Drive for Claude generated HTML files

I built HTML Drive this weekend: a personal Drive Claude can save to. Sign in with Google, then ask Claude to make HTML and it lands in your account, versioned, shareable, and with its own URL. The reason I built it is Thariq Shihipar's (Anthropic engineer) argument that markdown is restricting. Anyone who's watched Claude produce a 500-line markdown plan knows nobody actually reads it. HTML is what Claude does its best work in — colors, layout, interactivity, illustrations — but HTML files don't have a default home the way markdown does. They are somewhere in your filesys, or you upload them to S3 and lose track, or you screenshot the rendered version and lose all the interactivity. I wanted somewhere I could just point Claude at and say &quot;save it there.&quot; Connecting your agent is dead simple. You click &quot;Connect agent&quot; in the toolbar and get a single URL. You paste that URL into Claude Code. That's the entire setup. Behind the scenes the URL points to instructions the server generates on the fly with your credentials baked in, so the agent fetches it once and immediately knows how to save HTML to your account. No environment variables, no separate config files, no two-step paste. Just one URL. Every save is versioned automatically, so older versions stay reachable while the latest is what loads when someone visits the share link. Sharing works like Google Docs: private by default, invite specific people by email, or flip the whole thing public. There are folders for organizing, and the file browser has both an icon view (with little live previews of each file) and a list view. For demos, I had Claude render Thariq's essay as the kind of HTML it argues for: a living document with interactive figures sprinkled through, instead of a flat markdown blob. I also asked Claude to write a devlog while it was building the Drive, and we saved it into the Drive it was building. Both are public on the homepage. Try it: https://html.app.teenyapp.com &#32; submitted by &#32; /u/invocation02 [link] &#32; [comments]

</details>