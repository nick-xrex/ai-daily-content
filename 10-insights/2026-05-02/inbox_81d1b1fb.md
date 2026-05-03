---
id: inbox_81d1b1fb
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-claudeai-i-thought-cowork-was-gaslighting-me-abou-4869]]"
title: "I thought Cowork was gaslighting me about browser use"
url: https://www.reddit.com/r/ClaudeAI/comments/1t1t9f5/i_thought_cowork_was_gaslighting_me_about_browser/
source: reddit-claudeai
published_at: 2026-05-02T15:39:41+00:00
fetched_at: 2026-05-03T02:05:03.129048+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "用戶在 Linux 機器上測試 Claude Cowork 時要求搜索 booking.com 酒店，Claude 要求 Chrome 使用權限儘管該裝置未開啟 Chrome。經詢問，Claude 坦承初始敘述有誤，該瀏覽器實例實際位於另一台 Windows 設備（可能是用戶另一台電腦或遠程機器），透過 Claude in Chrome 擴展程序連接至用戶的 Anthropic 帳戶。用戶後續在 Windows 桌面確認了打開的 booking.com 標籤。此發現揭示了 Cowork 的跨設備瀏覽器同步能力，但官方文檔中未清楚記載該功能。"
key_points:
  - "Claude Cowork 支援跨設備瀏覽器連接 (isLocal: false 標記遠程實例)"
  - "透過 Claude in Chrome 擴展程式連結其他裝置上的瀏覽器，實現跨機搜索執行"
  - "該多裝置同步功能在官方文檔中未清楚說明，需補充文檔"
tags: [cowork, cross-device-browser, claude-in-chrome, undocumented-feature]
topics: [foundation_models.claude]
importance: 3
novelty: 2
insight_quality: 3
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## I thought Cowork was gaslighting me about browser use

用戶在 Linux 機器上測試 Claude Cowork 時要求搜索 booking.com 酒店，Claude 要求 Chrome 使用權限儘管該裝置未開啟 Chrome。經詢問，Claude 坦承初始敘述有誤，該瀏覽器實例實際位於另一台 Windows 設備（可能是用戶另一台電腦或遠程機器），透過 Claude in Chrome 擴展程序連接至用戶的 Anthropic 帳戶。用戶後續在 Windows 桌面確認了打開的 booking.com 標籤。此發現揭示了 Cowork 的跨設備瀏覽器同步能力，但官方文檔中未清楚記載該功能。

### 重點
- Claude Cowork 支援跨設備瀏覽器連接 (isLocal: false 標記遠程實例)
- 透過 Claude in Chrome 擴展程式連結其他裝置上的瀏覽器，實現跨機搜索執行
- 該多裝置同步功能在官方文檔中未清楚說明，需補充文檔

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t1t9f5/i_thought_cowork_was_gaslighting_me_about_browser/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>I was testing out Cowork on my Linux machine and asked it to search for a hotel ok booking.com. So off it goes, asks for my permission to use Chrome etc..</p> <p>However, Chrome wasn't open. In fact, I'd never opened Chrome on that machine. So I asked Claude if it was running headless Chrome to compete its work. It assured me that it wasn't and that it definitely was running a real browser on my local machine.</p> <p>But, it definitely wasn't. So of course I did the natural thing and called out Claude for being a liar (because I like burning tokens) and here's what it told me:</p> <p>&quot;You're right, I got that wrong — apologies. Looking back at what the tool actually returned: the connected browser is flagged as <strong>isLocal: false</strong>, meaning it's not on the machine you're chatting from. It's a Chrome instance with the Claude in Chrome extension installed and signed into your Anthropic account on a Windows device somewhere — possibly another computer of yours, or one where you previously set it up and left it running.</p> <p>I shouldn't have claimed the tab would be visible to you here. If you want to actually see the search, you'd need to be on whichever Windows machine has that extension paired. Do you want me to list the connected browser details so you can work out which one it is, or just leave it and I can pull the results some other way?&quot;</p> <p>I didn't realise this was a thing. I asked Claude if it was documented, and it told me it couldn't find it in the docs. I'm gonna take its word for it bc I'm lazy and it makes a good reddit post *if true.</p> <p>EDIT: I forgot to mention that I checked my Windows desktop where I'm also running Cowork and there was the open browser tab with the booking.com search.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/mashedtaz1"> /u/mashedtaz1 </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t1t9f5/i_thought_cowork_was_gaslighting_me_about_browser/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t1t9f5/i_thought_cowork_was_gaslighting_me_about_browser/">[comments]</a></span>

</details>