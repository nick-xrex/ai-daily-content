---
id: inbox_2b3b37b6
date: 2026-04-30
source_ref: "[[00-inbox/.../inbox_2b3b37b6]]"
title: "Claude Code Read tool silently downscales images"
url: https://www.reddit.com/r/ClaudeAI/comments/1t08qow/claude_code_read_tool_silently_downscales_images/
source: reddit-claudeai
published_at: 2026-04-30T20:55:01+00:00
fetched_at: 2026-05-01T14:06:33.035555+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者發現 Claude Code Read 工具存在隱藏行為：輸入高解析度視網膜螢幕截圖時，工具自動縮小圖像尺寸後才送入模型，但無任何警告。模型返回看似自信的答案，卻基於降尺度的劣化圖像，導致文字識別失敗。使用者質疑過往提供的所有截圖是否都被無聲縮小，影響長期準確度。"
key_points:
  - "Claude Code Read 工具自動縮小輸入圖像，無使用者警告或透明度揭示"
  - "高解析度視網膜截圖被降尺度後細節遺失，文字識別準確度大幅下降"
  - "使用者無法區分結果是源自原圖還是降尺度版本，埋藏可靠性風險"
tags: [claude-code-bug, image-downscaling, read-tool, transparency-gap]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Claude Code Read tool silently downscales images

使用者發現 Claude Code Read 工具存在隱藏行為：輸入高解析度視網膜螢幕截圖時，工具自動縮小圖像尺寸後才送入模型，但無任何警告。模型返回看似自信的答案，卻基於降尺度的劣化圖像，導致文字識別失敗。使用者質疑過往提供的所有截圖是否都被無聲縮小，影響長期準確度。

### 重點
- Claude Code Read 工具自動縮小輸入圖像，無使用者警告或透明度揭示
- 高解析度視網膜截圖被降尺度後細節遺失，文字識別準確度大幅下降
- 使用者無法區分結果是源自原圖還是降尺度版本，埋藏可靠性風險

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t08qow/claude_code_read_tool_silently_downscales_images/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Claude Code Read tool silently downscales images

<!-- SC_OFF --><div class="md"><p>Sent Claude Opus 4.7 a set of 10 retina screenshots (in Claude Code). Asked it to extract some text from them. Text was normal size clearly readable on my screen.</p> <p>Got back a confidence structural summary and a vague “couldn’t fully read every value” answer.</p> <p>Pushed on it. Turns out the ‘read’ tool down scales images before the model sees them. The thing I was looking at on my monitor and the thing the model was looking at were not the same image.</p> <p>No warning anywhere. The tool result is indistinguishable from reading a text file. You hand it a screenshot, get back a confident answer, and have no signal that the model is working off of degraded copy.</p> <p>So all this time whenever I gave Claude a screenshot to look at it’s been hallucinating most of the answers that I’ve been looking for?</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/IsaacKatahdin"> /u/IsaacKatahdin </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t08qow/claude_code_read_tool_silently_downscales_images/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t08qow/claude_code_read_tool_silently_downscales_images/">[comments]</a></span>

</details>