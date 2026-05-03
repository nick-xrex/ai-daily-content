---
id: inbox_82cf47ce
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-localllama-qwen-3-6-wins-the-benchmarks-but-gemma-4-29d7]]"
title: "Qwen 3.6 wins the benchmarks, but Gemma 4 wins reality. 7 things I learned testing 27B/31B Vision models locally (vLLM / FP8) side by side. Benchmaxing seems real."
url: https://www.reddit.com/r/LocalLLaMA/comments/1t1te8y/qwen_36_wins_the_benchmarks_but_gemma_4_wins/
source: reddit-localllama
published_at: 2026-05-02T15:44:53+00:00
fetched_at: 2026-05-03T01:59:12.944778+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "資深玩家針對 Qwen3.6-27B 與 Gemma4-31B 視覺語言模型進行長期並行本地測試（vLLM FP8），揭示官方基準測試與實務使用存在重大落差。儘管基準榜單 Qwen 領先，實務中 Gemma 4 在多數視覺任務、穩定性、指令遵循方面勝出。Qwen 傾向高 token 消耗與長推理循環（8000+ tokens on obscure tasks），Gemma 則高效簡潔。特定優勢：Qwen 在視頻追蹤與亞洲文化內容優異；Gemma 在歐美任務與細粒度視覺提取更精準。運維 gotcha：vLLM Gemma 視覺 token 預設值過低（280 vs 推薦 1120+），Qwen 需 2 FPS 預處理。"
key_points:
  - "基準遊戲化明顯：官方評分 Qwen > Gemma，實務測試相反；Qwen 基準優勢來自高 token 消耗與長推理循環，實際使用效率差"
  - "域特異性優勢遠勝單一評分：Qwen 視頻追蹤（運動計數、負重估計）優異；Gemma 細粒度視覺（OCR、坐標生成）與指令遵循更佳；區域偏差明顯（Gemma 歐美、Qwen 亞洲）"
  - "運維細節直接影響功能表現：Gemma 視覺 token budget 設置不足（1120+ vs 預設 280）導致誤判為性能差；Qwen 視頻輸入需 2 FPS 預處理；AI 視頻偵測兩者均不可靠"
tags: [vision-models, benchmark-gaming, real-world-evaluation, qwen3.6, gemma4]
topics: []
importance: 4
novelty: 4
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## Qwen 3.6 wins the benchmarks, but Gemma 4 wins reality. 7 things I learned testing 27B/31B Vision models locally (vLLM / FP8) side by side. Benchmaxing seems real.

資深玩家針對 Qwen3.6-27B 與 Gemma4-31B 視覺語言模型進行長期並行本地測試（vLLM FP8），揭示官方基準測試與實務使用存在重大落差。儘管基準榜單 Qwen 領先，實務中 Gemma 4 在多數視覺任務、穩定性、指令遵循方面勝出。Qwen 傾向高 token 消耗與長推理循環（8000+ tokens on obscure tasks），Gemma 則高效簡潔。特定優勢：Qwen 在視頻追蹤與亞洲文化內容優異；Gemma 在歐美任務與細粒度視覺提取更精準。運維 gotcha：vLLM Gemma 視覺 token 預設值過低（280 vs 推薦 1120+），Qwen 需 2 FPS 預處理。

### 重點
- 基準遊戲化明顯：官方評分 Qwen > Gemma，實務測試相反；Qwen 基準優勢來自高 token 消耗與長推理循環，實際使用效率差
- 域特異性優勢遠勝單一評分：Qwen 視頻追蹤（運動計數、負重估計）優異；Gemma 細粒度視覺（OCR、坐標生成）與指令遵循更佳；區域偏差明顯（Gemma 歐美、Qwen 亞洲）
- 運維細節直接影響功能表現：Gemma 視覺 token budget 設置不足（1120+ vs 預設 280）導致誤判為性能差；Qwen 視頻輸入需 2 FPS 預處理；AI 視頻偵測兩者均不可靠

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t1te8y/qwen_36_wins_the_benchmarks_but_gemma_4_wins/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1te8y/qwen_36_wins_the_benchmarks_but_gemma_4_wins/"> <img alt="Qwen 3.6 wins the benchmarks, but Gemma 4 wins reality. 7 things I learned testing 27B/31B Vision models locally (vLLM / FP8) side by side. Benchmaxing seems real." src="https://external-preview.redd.it/8OQk6xmHfnloaxXhcGN3Gif7S0jkDM9uwxv0g3JmzUI.png?width=140&amp;height=70&amp;auto=webp&amp;s=5db3a64285e240acef18dd1e17112bc2ac1244d6" title="Qwen 3.6 wins the benchmarks, but Gemma 4 wins reality. 7 things I learned testing 27B/31B Vision models locally (vLLM / FP8) side by side. Benchmaxing seems real." /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Hey guys,</p> <p>A couple of weeks ago, I asked this sub for the hardest Vision use cases you were dealing with to test the newly dropped Qwen 3.6 against Gemma 4. I finally finished running the gauntlet side-by-side locally on vLLM (FP8 quants) using my custom GUI.</p> <p>If you look at the Benchmarks then Qwen should win but from testing it seems really opposite. Looks like Benchmaxing. I attached comparison of scores below</p> <p>Since official benchmarks are pretty much gamed at this point, I threw real-world, unoptimized junk at them: weird memes, complex GeoGuessr spots, ugly handwritten notes, shopping lists, bounding box requests, and dynamic gym videos.</p> <p>Here are the 5 biggest behavioral differences and quirks I found:</p> <p><strong>- Did Qwen 3.6 fix the &quot;Overthinking&quot; token burn?</strong><br /> Yes and no. In Qwen 3.5, the model would burn 10k tokens overthinking simple tasks. In 3.6, the thinking preservation is noticeably better on simple prompts—it stops earlier. However, if you give it an obscure GeoGuessr location or a rare meme, it still panics, goes into a massive reasoning loop, burns 8,000+ tokens, and sometimes fails to output a final answer. Gemma 4 remains vastly more concise (often using just 1,500 tokens for the same task).</p> <p><strong>- Bounding Boxes &amp; Scaling: Qwen still fights instructions</strong><br /> If you want to extract coordinates for bounding boxes or polygon segmentation masks, Gemma 4 is much better at following formatting instructions. Which make sense as I didn't find any information about this capability on Qwen. Visual models are usually trained on a 0–1000 coordinate grid. When I prompted them to output normalized coordinates (0 to 1), Gemma calculated the scaling perfectly in its thinking phase and output clean JSON. Qwen completely ignored the scaling instruction and output raw 0-1000 coordinates in a weird format most of times.</p> <p><strong>- The Cultural Divide (Memes &amp; GeoGuessr)</strong><br /> There is a regional bias in their training data.</p> <ul> <li><strong>Gemma 4</strong> easily won European/Western tasks (recognizing obscure European monuments as example).</li> <li><strong>Qwen 3.6</strong> seem to perform better on Asian context. It accurately identified the Chinese &quot;white people food&quot; meme and correctly guessed an obscure Malaysia/Indonesia border town in GeoGuessr—even without thinking mode enabled.</li> </ul> <p><strong>- Qwen 3.6 is a upgrade for Video tracking</strong><br /> I fed both models a video of me doing deadlifts (pre-processed to 2 FPS to avoid vLLM rejection). Qwen 3.6 was incredible here. With the thinking budget tuned, it correctly identified the exercise, counted the exact number of reps (Gemma missed one), and most accurately estimated the total weight on the bar by judging plate thickness.</p> <p><strong>- AI Video Detection is still a coin toss</strong><br /> I tested them on videos generated by LTX 2.3. Both models successfully caught blatant physics errors (like balls changing color or smoke without a source). But on more subtle AI videos, they were completely inconsistent. Running the exact same prompt twice would yield &quot;Real&quot; one time and &quot;AI generated&quot; the next. Neither is reliable for deepfake detection yet.</p> <p><strong>- Don't trust Inference Engines default visual token budget for Gemma</strong><br /> If you're running Gemma and it's failing at fine visual details (like small OCR text or complex graphs), check your max_soft_tokens. Inference engines like vLLM, Llama Cpp often default this to a shockingly low number, like 280. A lot of people think the model is just performing poorly, but it's actually just heavily compressing the image input. If you crank this value up (e.g., to over 1120), the accuracy instantly spikes. The best part? In my testing, maxing out this visual token budget added almost zero noticeable latency. Don't cheap out on your visual tokens!</p> <p><strong>- Video Pipeline Friction: Gemma eats raw video, Qwen demands 2 FPS</strong><br /> If you are building an automated pipeline, be aware of this input quirk: Gemma 4's encoder is incredibly forgiving and will accept pretty much any video format or framerate you throw directly at it. Qwen 3.6, on the other hand, is extremely strict. You must pre-process your video down to 2 FPS before passing it to vLLM, otherwise it will just throw errors or fail to process.</p> <p><strong>Resources:</strong><br /> If you want to see the actual latency differences, how I tuned the visual token budgets, and the live inference side-by-side, <strong>I put together a repo with uv sync etc here:</strong> <a href="https://github.com/lukaLLM/Gemma4_vs_Qwen3.5_3.6_Vision_Setup_Dockers"><strong>https://github.com/lukaLLM/Gemma4_vs_Qwen3.5_3.6_Vision_Setup_Dockers</strong></a> <strong>There is also video of tests if needed.</strong> </p> <p>Let me know also how you use it so far. </p> <p><a href="https://preview.redd.it/420ns466vqyg1.png?width=1024&amp;format=png&amp;auto=webp&amp;s=7aad733c5a3002c628e1cb9fe470f64032bee0b6">https://preview.redd.it/420ns466vqyg1.png?width=1024&amp;format=png&amp;auto=webp&amp;s=7aad733c5a3002c628e1cb9fe470f64032bee0b6</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/FantasticNature7590"> /u/FantasticNature7590 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1te8y/qwen_36_wins_the_benchmarks_but_gemma_4_wins/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1te8y/qwen_36_wins_the_benchmarks_but_gemma_4_wins/">[comments]</a></span> </td></tr></table>

</details>