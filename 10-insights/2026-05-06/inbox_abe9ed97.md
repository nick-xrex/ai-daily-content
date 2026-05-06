---
id: inbox_abe9ed97
date: 2026-05-06
source_ref: "[[00-inbox/.../inbox_abe9ed97]]"
title: "Anyone ever notice eerily similar ChatGPT and Claude responses like this?"
url: https://www.reddit.com/r/ClaudeAI/comments/1t4zc3s/anyone_ever_notice_eerily_similar_chatgpt_and/
source: reddit-claudeai
published_at: 2026-05-06T01:55:52+00:00
fetched_at: 2026-05-06T13:31:54.845669+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "一位使用者進行了跨模型對比測試，分別使用 Sonnet 4.6、Opus 4.6、Opus 4.7 和 ChatGPT 5.3 對同一段程式碼進行審查。使用者發現 Opus 4.7 和 ChatGPT 5.3 的初始回應段落措辭「幾乎一字一句相同」，超出合理巧合範圍。Opus 4.7 開頭寫著「Solid little utility. The core idea is right: a fenced code block's fence must be longer than any backtick run inside it」，ChatGPT 5.3 表述幾乎完全一致。使用者無法確定原因，提出三個可能解釋：訓練數據高度重疊、一個提供商在後端調用另一個、或隱藏的架構連結。值得注意的是，兩模型在後續段落差異明顯，只有初始框架相似。"
key_points:
  - "Opus 4.7 與 ChatGPT 5.3 代碼審查的開頭段落措辭高度重合"
  - "相似度超過訓練數據重疊的合理預期，引發跨模型架構的疑問"
  - "後續段落差異明顯，僅初始分析框架一致"
tags: [model-comparison, response-similarity, opus-4.7]
topics: [foundation_models.claude, foundation_models.gpt]
importance: 3
novelty: 4
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Anyone ever notice eerily similar ChatGPT and Claude responses like this?

一位使用者進行了跨模型對比測試，分別使用 Sonnet 4.6、Opus 4.6、Opus 4.7 和 ChatGPT 5.3 對同一段程式碼進行審查。使用者發現 Opus 4.7 和 ChatGPT 5.3 的初始回應段落措辭「幾乎一字一句相同」，超出合理巧合範圍。Opus 4.7 開頭寫著「Solid little utility. The core idea is right: a fenced code block's fence must be longer than any backtick run inside it」，ChatGPT 5.3 表述幾乎完全一致。使用者無法確定原因，提出三個可能解釋：訓練數據高度重疊、一個提供商在後端調用另一個、或隱藏的架構連結。值得注意的是，兩模型在後續段落差異明顯，只有初始框架相似。

### 重點
- Opus 4.7 與 ChatGPT 5.3 代碼審查的開頭段落措辭高度重合
- 相似度超過訓練數據重疊的合理預期，引發跨模型架構的疑問
- 後續段落差異明顯，僅初始分析框架一致

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t4zc3s/anyone_ever_notice_eerily_similar_chatgpt_and/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Anyone ever notice eerily similar ChatGPT and Claude responses like this?

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1t4zc3s/anyone_ever_notice_eerily_similar_chatgpt_and/"> <img alt="Anyone ever notice eerily similar ChatGPT and Claude responses like this?" src="https://preview.redd.it/xv35b1pz9fzg1.png?width=140&amp;height=104&amp;auto=webp&amp;s=19103d6af8521b5d5b1f855e5b977c39f0e57049" title="Anyone ever notice eerily similar ChatGPT and Claude responses like this?" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Today I tested out various models on the same prompt (Sonnet 4.6, Opus 4.6, Opus 4.7, ChatGPT 5.3). I actually just wanted to see which models (if any) would correctly point out what I saw as the biggest issue in the example code.</p> <p>What I wasn't expecting, was GPT 5.3's and Opus 4.7's first paragraphs to be almost word-for-word the same here...</p> <p>Opus 4.7:</p> <blockquote> <p><strong>Solid little utility. The core idea is right:</strong> a fenced code block's <strong>fence must be longer than any backtick run inside it,</strong> so you scan for the longest run and add one. <strong>A few thoughts</strong>, roughly in order of how much I'd actually push on them: ...</p> </blockquote> <p>GPT 5.3:</p> <blockquote> <p><strong>Nice little utility. The core idea is solid:</strong> choose a <strong>fence longer than any backtick run inside the text,</strong> so the content cannot accidentally close the code block. </p> <p><strong>A few things</strong> I’d look at: ...</p> </blockquote> <p>Obviously there are some patterns that are shared across basically all AI models these days (e.g. em dashes) but this really threw me for a loop. Even wondered for a second if one provider was sneakily calling the other under the hood, to save on compute costs. Or if one model was just really heavily trained on the other. These wordings are specific enough that I can't imagine it's simply due to training data overlap, but I guess that's theoretically possible too.</p> <p>FWIW the responses did diverge more after the first paragraph. (I can share them in full in the comments, to keep this post concise.)</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/PigsAreGassedToDeath"> /u/PigsAreGassedToDeath </a> <br /> <span><a href="https://www.reddit.com/gallery/1t4zc3s">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t4zc3s/anyone_ever_notice_eerily_similar_chatgpt_and/">[comments]</a></span> </td></tr></table>

</details>