---
id: inbox_71b53c9b
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_71b53c9b]]"
title: "I tested Kimi K2.6 vs Claude Opus 4.7 on a weird game coding task"
url: https://www.reddit.com/r/ClaudeAI/comments/1t4f005/i_tested_kimi_k26_vs_claude_opus_47_on_a_weird/
source: reddit-claudeai
published_at: 2026-05-05T13:08:56+00:00
fetched_at: 2026-05-06T13:29:59.481649+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "詳細對標測試：Kimi K2.6（廉價中文模型）vs Claude Opus 4.7 在遊戲編碼任務中的性能與成本。測試 1（本地模組）：Opus 花費 $3.59、12 分鐘 API 耗時完成，Kimi 花費 $0.39、9 分 27 秒完成，但代碼冗餘 2 倍且 Minetest 配置有誤；測試 2（Google Sheets 集成）：Opus 成功耗資 $16.03，Kimi 失敗於開發伺服器與測試問題，耗資 $5.03 後放棄。價格對比：Kimi 輸入 $0.95/M、輸出 $4/M、快取 $0.16/M；Opus 輸入 $5/M、輸出 $25/M。"
key_points:
  - "廉價模型在隔離簡單任務的性價比優勢明顯（Kimi $0.39 完成 Lua+TS 模組），但代碼質量（2 倍冗餘）與細節配置易出錯，除錯成本隱性抵銷成本優勢"
  - "複雜多工具集成工作流存在明顯能力差異：Opus 可迭代除錯並整合 Composio，Kimi 無法克服開發循環與外部 API 集成難題，成功率 0%"
  - "成本爆炸與可靠性權衡：Opus 在複雜任務費用跳增 4 倍至 $16.03，但提供可部署結果；Kimi 維持低成本結構但無法交付，對時間成本敏感的開發不可行"
tags: [model-comparison, kimi-k2.6, claude-opus-4.7, cost-analysis, integration-complexity]
topics: [foundation_models.claude]
importance: 4
novelty: 3
insight_quality: 5
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## I tested Kimi K2.6 vs Claude Opus 4.7 on a weird game coding task

詳細對標測試：Kimi K2.6（廉價中文模型）vs Claude Opus 4.7 在遊戲編碼任務中的性能與成本。測試 1（本地模組）：Opus 花費 $3.59、12 分鐘 API 耗時完成，Kimi 花費 $0.39、9 分 27 秒完成，但代碼冗餘 2 倍且 Minetest 配置有誤；測試 2（Google Sheets 集成）：Opus 成功耗資 $16.03，Kimi 失敗於開發伺服器與測試問題，耗資 $5.03 後放棄。價格對比：Kimi 輸入 $0.95/M、輸出 $4/M、快取 $0.16/M；Opus 輸入 $5/M、輸出 $25/M。

### 重點
- 廉價模型在隔離簡單任務的性價比優勢明顯（Kimi $0.39 完成 Lua+TS 模組），但代碼質量（2 倍冗餘）與細節配置易出錯，除錯成本隱性抵銷成本優勢
- 複雜多工具集成工作流存在明顯能力差異：Opus 可迭代除錯並整合 Composio，Kimi 無法克服開發循環與外部 API 集成難題，成功率 0%
- 成本爆炸與可靠性權衡：Opus 在複雜任務費用跳增 4 倍至 $16.03，但提供可部署結果；Kimi 維持低成本結構但無法交付，對時間成本敏感的開發不可行

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t4f005/i_tested_kimi_k26_vs_claude_opus_47_on_a_weird/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I tested Kimi K2.6 vs Claude Opus 4.7 on a weird game coding task

<!-- SC_OFF --><div class="md"><p>Kimi K2.6 has been getting a lot of hype recently, mostly because it seems like a “good enough for coding, way cheaper than frontier models” option.</p> <p>So I wanted to test it properly.</p> <p>So I tested it against my favorite, Claude Opus 4.7 on a weird but practical coding task.</p> <p>The task was to build a small Minetest/Luanti bounty board game mod with a TypeScript backend, then extend it with Google Sheets logging through Composio.</p> <p>The idea is that, player joins a local world, runs <code>/bounty</code>, gets a task, completes it in-game, gets rewarded, and then the backend records the completion. In the second test, completions also get logged to Google Sheets.</p> <p>Both models got the same prompts.</p> <p>Setup:</p> <ul> <li><strong>Claude Opus 4.7:</strong> Claude Code</li> <li><strong>Kimi K2.6:</strong> OpenCode via OpenRouter</li> <li>Same repo, same task, same success criteria</li> <li>Measured: working result, code quality, debugging pain, time, token usage, and cost</li> </ul> <p>For pricing context, Claude Opus 4.7 costs $5/M input and $25/M output, while Kimi K2.6 is listed at $0.95/M for input tokens and $4/M for output tokens, with cached input even lower at $ 0.16/M.</p> <h1>Test 1: local bounty board</h1> <p>Opus 4.7 got the local version working cleanly. It built the Express/Zod/Vitest backend, Lua mod, <code>/bounty</code> flow, rewards, leaderboard, and tests passed.</p> <p>Stats:</p> <ul> <li><strong>Cost:</strong> ~$3.59</li> <li><strong>Time:</strong> 12min API, 23min wall</li> <li><strong>Code:</strong> +1,688 / -0</li> <li><strong>Output:</strong> 54.8k</li> <li><strong>Cache read:</strong> 2.8M</li> </ul> <p>Pretty clean MVP.</p> <p>Kimi K2.6 was honestly better than I expected here.</p> <p>It also got the local bounty board working. Backend routes were there, Lua mod was there, and the basic game flow worked.</p> <p>But it felt a little messier.</p> <p>The annoying part was Minetest config. It wrote <code>secure.http_mods = bountykimi</code> in the global config, but also created a world-level config with a different mod name. So the HTTP API was not enabled for the actual mod that was running. Took me like 30+ minutes to debug because I do not play this game.</p> <p>Stats:</p> <ul> <li><strong>Cost:</strong> ~$0.39</li> <li><strong>Duration:</strong> ~9min 27sec</li> <li><strong>Code changes:</strong> +4,671 / -0</li> <li><strong>Context used:</strong> 52,073 tokens</li> <li><strong>Context window used:</strong> 20%</li> </ul> <p>So yeah, Kimi passed Test 1. But it wrote way more code, over 2X for the same thing.</p> <h1>Test 2: Composio + Google Sheets</h1> <p>This is where the gap showed up.</p> <p>Opus 4.7 got the Google Sheets sync working. It had some issues with tsx watch and env loading, but after a bit of back and forth, the backend could complete a bounty and append it to Google Sheets through Composio.</p> <p>Stats:</p> <ul> <li><strong>Cost:</strong> $16.03</li> <li><strong>Time:</strong> 28min API, 1hr 17min wall</li> <li><strong>Code:</strong> +1,848 / -507</li> <li><strong>Cache read:</strong> 22.3M</li> <li><strong>Output:</strong> 123.3k</li> </ul> <p>Painfully expensive, but it worked.</p> <p>Kimi K2.6 failed this one.</p> <p>It got stuck on dev server issues, tests, build problems, and never wired the Composio integration into a clean working state. After ~25 minutes and 135k+ tokens, I stopped it.</p> <p>Stats:</p> <ul> <li><strong>Cost:</strong> ~$5.03</li> <li><strong>Time:</strong> ~25min</li> <li><strong>Tokens:</strong> 135k+</li> </ul> <h1>Takeaway</h1> <p>Kimi K2.6 is actually interesting for cheaper local coding tasks. For $0.39, getting a working Lua + TypeScript game mod is not bad at all.</p> <p>But once the task involved external tools, config issues, and real integration work, Opus 4.7 was clearly ahead.</p> <p>My rough verdict:</p> <ul> <li><strong>Best local MVP:</strong> Opus, but Kimi is way better value</li> <li><strong>Best real integration:</strong> Opus by a lot</li> <li><strong>Cleaner code:</strong> Opus</li> <li><strong>Cheaper experiment model:</strong> Kimi</li> <li><strong>Most painful cost:</strong> definitely Opus lol</li> </ul> <p>I have a full breakdown with commits, screenshots, demos and the costs here:</p> <p><a href="https://composio.dev/content/kimi-k2.6-vs-opus-4.7">Kimi K2.6 vs. Claude Opus 4.7 in a Weird Game Coding Test</a></p> <p>Anyone else using Kimi K2.6 for real coding work? How is it holding up in a real coding workflow?</p> <p>Open models have not always been the best in my experience with real-world projects, but with every new model, my expectations rise a little.</p> <p>Let's see where Kimi K2.6 goes from here.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/shricodev"> /u/shricodev </a> <br /> <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t4f005/i_tested_kimi_k26_vs_claude_opus_47_on_a_weird/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/ClaudeAI/comments/1t4f005/i_tested_kimi_k26_vs_claude_opus_47_on_a_weird/">[comments]</a></span>

</details>