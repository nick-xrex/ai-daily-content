---
id: inbox_6688ae36
date: 2026-04-30
source_ref: "[[00-inbox/.../inbox_6688ae36]]"
title: "I gave the Claude desktop app a built-in mobile device"
url: https://www.reddit.com/r/ClaudeAI/comments/1t09ff4/i_gave_the_claude_desktop_app_a_builtin_mobile/
source: reddit-claudeai
published_at: 2026-04-30T21:21:05+00:00
fetched_at: 2026-05-01T14:06:33.034229+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者展示第三方工具 MobAI 與 Claude Desktop 的整合方案，使 Claude 能控制 iOS 模擬器並與行動應用互動。核心創新在於使用者可在行動螢幕選定特定元素，MobAI 傳遞該元素的結構化上下文予 Claude（非單純截圖），使 Claude 精確理解元素功能與位置。支援原生應用、跨平台應用、實體 iOS/Android 裝置及模擬器。"
key_points:
  - "MobAI 與 Claude Desktop 整合，支援控制 iOS 模擬器並執行應用操作"
  - "選擇行動螢幕元素後，傳遞結構化上下文而非單純圖像，提升 Claude 理解精度"
  - "相容原生、跨平台應用及實體 iOS/Android 裝置、Android 模擬器、iOS 模擬器"
tags: [claude-desktop, mobai, mobile-testing, ui-automation]
topics: [foundation_models.claude]
importance: 3
novelty: 4
insight_quality: 3
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## I gave the Claude desktop app a built-in mobile device

使用者展示第三方工具 MobAI 與 Claude Desktop 的整合方案，使 Claude 能控制 iOS 模擬器並與行動應用互動。核心創新在於使用者可在行動螢幕選定特定元素，MobAI 傳遞該元素的結構化上下文予 Claude（非單純截圖），使 Claude 精確理解元素功能與位置。支援原生應用、跨平台應用、實體 iOS/Android 裝置及模擬器。

### 重點
- MobAI 與 Claude Desktop 整合，支援控制 iOS 模擬器並執行應用操作
- 選擇行動螢幕元素後，傳遞結構化上下文而非單純圖像，提升 Claude 理解精度
- 相容原生、跨平台應用及實體 iOS/Android 裝置、Android 模擬器、iOS 模擬器

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t09ff4/i_gave_the_claude_desktop_app_a_builtin_mobile/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I gave the Claude desktop app a built-in mobile device

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t09ff4/i_gave_the_claude_desktop_app_a_builtin_mobile/"> <img alt="I gave the Claude desktop app a built-in mobile device" src="https://external-preview.redd.it/ZjZybWNwZXQ4ZXlnMQHxID73vFjsp01LJkF9ltZUUJGbtuCkvExHvrHlLvsF.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=2e8c773c05541a2d39d46406a08ca82c8fb2d7ca" title="I gave the Claude desktop app a built-in mobile device" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Hey everyone!</p> <p>I’ve been experimenting with a setup where Claude Desktop can work against a live mobile app through Preview.</p> <p>In the demo, I use <a href="https://mobai.run">MobAI</a> to control an iOS simulator, perform a few actions inside the app, then select a specific element on the mobile screen and ask Claude what it is.</p> <p>What I like here is that Claude is not guessing from a screenshot alone. MobAI sends context about the selected element, so Claude can understand what it is, where it is, and how it relates to the current screen.</p> <p>So the loop is basically: control the app, select an element, send it to Claude, and ask it to make changes to that UI.</p> <p>It works with native and cross-platform apps on physical iOS and Android devices, Android emulators, and iOS simulators.</p> <p>For context, I’m the author of MobAI.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/interlap"> /u/interlap </a> <br /> <span><a href="https://v.redd.it/k3k6zpet8eyg1">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t09ff4/i_gave_the_claude_desktop_app_a_builtin_mobile/">[comments]</a></span> </td></tr></table>

</details>