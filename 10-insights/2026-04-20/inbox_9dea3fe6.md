---
id: inbox_9dea3fe6
date: 2026-04-20
source_ref: "[[00-inbox/.../inbox_9dea3fe6]]"
title: "llm-openrouter 0.6"
url: https://simonwillison.net/2026/Apr/20/llm-openrouter/#atom-everything
source: simon-willison
published_at: 2026-04-20T18:00:26+00:00
fetched_at: 2026-04-22T00:38:32.280916+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 發佈 llm-openrouter v0.6，新增 `llm openrouter refresh` 指令實現快速刷新可用模型清單（毋須等待快取過期）。該機制讓開發者能即時嘗試新上線的模型；以 Kimi K2.6 為例，其成功生成了帶動畫控制的 HTML 互動頁面。"
key_points:
  - "工具版本：llm-openrouter v0.6"
  - "新功能：refresh 指令加速模型列表更新，毋須等待快取失效"
  - "實際應用場景：Kimi K2.6 上線至 OpenRouter 時立即試驗"
tags: [llm-cli-tools, openrouter, model-discovery]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-openrouter 0.6

Simon Willison 發佈 llm-openrouter v0.6，新增 `llm openrouter refresh` 指令實現快速刷新可用模型清單（毋須等待快取過期）。該機制讓開發者能即時嘗試新上線的模型；以 Kimi K2.6 為例，其成功生成了帶動畫控制的 HTML 互動頁面。

### 重點
- 工具版本：llm-openrouter v0.6
- 新功能：refresh 指令加速模型列表更新，毋須等待快取失效
- 實際應用場景：Kimi K2.6 上線至 OpenRouter 時立即試驗

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/20/llm-openrouter/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# llm-openrouter 0.6

<p><strong>Release:</strong> <a href="https://github.com/simonw/llm-openrouter/releases/tag/0.6">llm-openrouter 0.6</a></p>
    <blockquote>
<ul>
<li><code>llm openrouter refresh</code> command for refreshing the list of available models without waiting for the cache to expire.</li>
</ul>
</blockquote>
<p>I added this feature so I could try <a href="https://www.kimi.com/blog/kimi-k2-6">Kimi 2.6</a> on OpenRouter as soon as it <a href="https://openrouter.ai/moonshotai/kimi-k2.6">became available there</a>.</p>
<p>Here's <a href="https://gisthost.github.io/?ecaad98efe0f747e27bc0e0ebc669e94/pelican.html">its pelican</a> - this time as an HTML page because Kimi chose to include an HTML and JavaScript UI to control the animation. <a href="https://gist.github.com/simonw/ecaad98efe0f747e27bc0e0ebc669e94#2026-04-20t164936----conversation-01kpnwt8d2bt5qwkm60j9sbkbs-id-01kpnwra0prz6v822cct5b08kq">Transcript here</a>.</p>
<p><img alt="The bicycle is about right. The pelican is OK. It is pedaling furiously and flapping its wings a bit. Controls below the animation provide a pause button and sliders for controlling the speed and the wing flap." src="https://static.simonwillison.net/static/2026/kimi-k2-pelican-64-colors.gif" /></p>
    
        <p>Tags: <a href="https://simonwillison.net/tags/openrouter">openrouter</a>, <a href="https://simonwillison.net/tags/llm">llm</a>, <a href="https://simonwillison.net/tags/llm-release">llm-release</a>, <a href="https://simonwillison.net/tags/pelican-riding-a-bicycle">pelican-riding-a-bicycle</a>, <a href="https://simonwillison.net/tags/kimi">kimi</a>, <a href="https://simonwillison.net/tags/ai-in-china">ai-in-china</a>, <a href="https://simonwillison.net/tags/llms">llms</a>, <a href="https://simonwillison.net/tags/ai">ai</a>, <a href="https://simonwillison.net/tags/generative-ai">generative-ai</a></p>

</details>