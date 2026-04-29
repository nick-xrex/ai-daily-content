---
id: inbox_a1f3132c
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0658-reddit-claudeai-toothcomb-is-an-open-source-tool-for-ana-a0eb]]"
title: "Toothcomb is an open-source tool for analysing and fact-checking speech in real time."
url: https://www.reddit.com/r/ClaudeAI/comments/1sy1vcw/toothcomb_is_an_opensource_tool_for_analysing_and/
source: reddit-claudeai
published_at: 2026-04-28T13:44:16+00:00
fetched_at: 2026-04-29T07:28:48.557822+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Toothcomb 是開源語音分析與事實查證工具，支援逐字稿輸入、MP3 上傳、即時麥克風串流等多種音訊來源。分析採三階段管線：首先將文本拆分為數句至數十句片段，逐一發送至 Claude Opus API 搭配詳細提示詞查找主張、邏輯謬誤、欺騙性措辭；其次 Opus 判定需事實檢驗的陳述，利用內部知識或透過 Sonnet API 網路搜尋取得最新資訊；最後執行全局最終檢閱捕捉跨段矛盾、承諾未兌現等整體問題。開發者強調細緻管理 Claude 代碼生成過程（細緻到人類開發者會辭職的程度）反而實現真誠人-AI 協作，代碼品質與手工撰寫不相上下但開發時間大幅縮短。"
key_points:
  - "三階段管線架構：句段拆分 → Opus 並行分析（主張、謬誤、欺騙）→ 網路搜尋 → 全文一致性檢閱，能捕捉單段無法發現的跨段矛盾"
  - "人-AI 協作洞察：細緻的「微管理」Claude 代碼反而產出高品質成果，加速交付，體現積極干預反而優化的協作模式"
  - "多源音訊支援：逐字稿、MP3、麥克風串流，實時視覺化展示分析與事實檢驗進度，適用於即時講座監控或錄音事後審查"
tags: [toothcomb, fact-checking, speech-analysis, opus, prompt-engineering, claude-code]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Toothcomb is an open-source tool for analysing and fact-checking speech in real time.

Toothcomb 是開源語音分析與事實查證工具，支援逐字稿輸入、MP3 上傳、即時麥克風串流等多種音訊來源。分析採三階段管線：首先將文本拆分為數句至數十句片段，逐一發送至 Claude Opus API 搭配詳細提示詞查找主張、邏輯謬誤、欺騙性措辭；其次 Opus 判定需事實檢驗的陳述，利用內部知識或透過 Sonnet API 網路搜尋取得最新資訊；最後執行全局最終檢閱捕捉跨段矛盾、承諾未兌現等整體問題。開發者強調細緻管理 Claude 代碼生成過程（細緻到人類開發者會辭職的程度）反而實現真誠人-AI 協作，代碼品質與手工撰寫不相上下但開發時間大幅縮短。

### 重點
- 三階段管線架構：句段拆分 → Opus 並行分析（主張、謬誤、欺騙）→ 網路搜尋 → 全文一致性檢閱，能捕捉單段無法發現的跨段矛盾
- 人-AI 協作洞察：細緻的「微管理」Claude 代碼反而產出高品質成果，加速交付，體現積極干預反而優化的協作模式
- 多源音訊支援：逐字稿、MP3、麥克風串流，實時視覺化展示分析與事實檢驗進度，適用於即時講座監控或錄音事後審查

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1sy1vcw/toothcomb_is_an_opensource_tool_for_analysing_and/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/ClaudeAI/comments/1sy1vcw/toothcomb_is_an_opensource_tool_for_analysing_and/"> <img alt="Toothcomb is an open-source tool for analysing and fact-checking speech in real time." src="https://external-preview.redd.it/MzV3MTRiOW1teHhnMQmR34WQo1CyaZrG1uVL7JYGcqnnmHwESgxw7etFGugr.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=883aa39e2cccfe4f989c261964052b7ca3a14ce4" title="Toothcomb is an open-source tool for analysing and fact-checking speech in real time." /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Give Toothcomb a speech transcript and it will fact-check and analyse it. If you have an MP3 file of someone speaking, it can generate the transcript for you. You can also stream audio in real time from your device's microphone. You can see a <a href="https://toothcomb.codebox.net/">demo running here</a> and read more about the project on the <a href="https://codebox.net/pages/toothcomb-ai-fact-checker">home page</a>. </p> <p>Analysis is performed in three stages:</p> <ol> <li><p>The text is broken up into small parts, each usually a few sentences in length. These parts are sent, one at a time, to the Claude Opus API with <a href="https://github.com/codebox/toothcomb/blob/main/resources/prompts/utterance_analysis.txt">detailed instructions about what to look for</a>. The API will respond with a list of what it found - this may include claims, promises or predictions made by the speaker, logical fallacies, and deceptive or manipulative language.</p></li> <li><p>Claude may decide that some of the speaker's statements require fact-checking. It may be able to perform these checks using what it already knows, or it may need to search the web to get up-to-date information, this is done using the APIs web search tool in conjunction with the Sonnet API.</p></li> <li><p>Once each part of the speech has been checked separately, a <a href="https://github.com/codebox/toothcomb/blob/main/resources/prompts/transcript_review.txt">final review of the entire speech</a> is performed. The final review can pick up things that aren't apparent from looking at small parts in isolation. For example, it will check if the speaker contradicts themselves, or promises to address some issue and then fails to do so.</p></li> </ol> <p>The architecture and high-level design of both the code and the user interface were created by me; most of the actual code was written by Claude Code/Opus 4.6. During development I micro-managed Claude to the point where any human developer would have resigned, and been right to do so. This felt like a genuine collaboration, and the resulting code is probably as good as if I'd written it by hand myself, but it took a lot less time to finish.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/bluebox72"> /u/bluebox72 </a> <br /> <span><a href="https://v.redd.it/c5he4vzgmxxg1">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1sy1vcw/toothcomb_is_an_opensource_tool_for_analysing_and/">[comments]</a></span> </td></tr></table>

</details>