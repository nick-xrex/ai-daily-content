---
id: inbox_e2efd167
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-claudeai-alien-pinball-postmortem-how-i-made-a-fu-128c]]"
title: "Alien Pinball Postmortem - How I made a full physics pinball game with Claude"
url: https://www.reddit.com/r/ClaudeAI/comments/1t6kz9m/alien_pinball_postmortem_how_i_made_a_full/
source: reddit-claudeai
published_at: 2026-05-07T19:35:50+00:00
fetched_at: 2026-05-08T08:10:27.782240+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者用 Claude Code Max (Opus)、ChatGPT 圖像生成、Suno 5.5 音樂、LittleJS 引擎製作全功能彈珠台遊戲《Alien Pinball》(browser + mobile)，包括多球、技術射擊、升級連擊、精靈模式等。工作流程：約 50% 語音轉文字輸入、50% 手動編輯，強調共同開發而非代碼生成。核心洞察：AI 在遊戲邏輯、物理系統、工具生成上近乎完美，但「feel」(彈性、力度、軌跡微調)、sound passes 與 ramp angles 仍需人類關鍵把控。提出藝術技巧：用碰撞幾何輪廓作圖像生成提示，確保美術與物理完全對齊。"
key_points:
  - "工作分工：Claude 負責遊戲邏輯+Box2D 物理+custom spinners/ramps/locks，人類負責調參與 feel (彈性係數 1.49→1.491 級微調)"
  - "藝術技巧：輸出碰撞幾何輪廓給圖像生成器，確保視覺與物理完全對齊（「physics is the prompt」）"
  - "完整工具鏈：Opus 邏輯、ChatGPT 圖像、Suno 5.5 音樂、ZzFX 程序音效、LittleJS+Box2D 引擎；in-game table editor 可復用於未來遊戲"
tags: [game-development, ai-workflow, physics-simulation, claude-code]
topics: [foundation_models.claude]
importance: 4
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## Alien Pinball Postmortem - How I made a full physics pinball game with Claude

開發者用 Claude Code Max (Opus)、ChatGPT 圖像生成、Suno 5.5 音樂、LittleJS 引擎製作全功能彈珠台遊戲《Alien Pinball》(browser + mobile)，包括多球、技術射擊、升級連擊、精靈模式等。工作流程：約 50% 語音轉文字輸入、50% 手動編輯，強調共同開發而非代碼生成。核心洞察：AI 在遊戲邏輯、物理系統、工具生成上近乎完美，但「feel」(彈性、力度、軌跡微調)、sound passes 與 ramp angles 仍需人類關鍵把控。提出藝術技巧：用碰撞幾何輪廓作圖像生成提示，確保美術與物理完全對齊。

### 重點
- 工作分工：Claude 負責遊戲邏輯+Box2D 物理+custom spinners/ramps/locks，人類負責調參與 feel (彈性係數 1.49→1.491 級微調)
- 藝術技巧：輸出碰撞幾何輪廓給圖像生成器，確保視覺與物理完全對齊（「physics is the prompt」）
- 完整工具鏈：Opus 邏輯、ChatGPT 圖像、Suno 5.5 音樂、ZzFX 程序音效、LittleJS+Box2D 引擎；in-game table editor 可復用於未來遊戲

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t6kz9m/alien_pinball_postmortem_how_i_made_a_full/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Postmortem: Alien Pinball — built with Claude + ChatGPT + Suno + LittleJS Just shipped a browser pinball game. Short writeup of the AI workflow in case it's useful here. The game — Full physics pinball: multiball, an A-L-I-E-N rollover multiplier (caps at 5x), skill shots, escalating combos, outlane gutter saves, and a wizard-mode centipede boss you fight while juggling 3 balls. Browser, mobile-friendly, no install. Play it: https://focaccai.itch.io/alien-pinball Setup. Claude Code Max, Opus model for the heavy lifting. Roughly half my input was via speech-to-text — talking at the codebase rather than typing — the other half was typing plus a lot of manual code editing. It genuinely felt co-developed rather than code-generated: describe what I want, riff with Claude, dive in by hand to steer or clean up. Tool stack Code: Claude. All game logic, custom Box2D parts (slingshots, drop targets, spinners, ramps, ball locks, break targets), plus a full in-game table editor I built so I could drag/place/tune every part visually. Reusable for future pinball games. Art: ChatGPT image gen. I had Claude write the image prompts too. Music: Suno 5.5 — three tracks, lots of iteration to find the right vibe. Claude wrote the music prompts. Sounds: ZzFX — every sound generated procedurally at game start, no audio files. Claude tuned the parameters by ear-by-ear iteration. This combo was a joy with AI. Engine: LittleJS + Box2D WASM. Small, fast, AI handles it beautifully — minimal API surface, no framework ceremony to wade through. The art trick that actually worked. I exported a silhouette of the collision geometry (walls, ramps, bumpers, drop targets — exact positions) and handed it to the image generator with: &quot;create an alien-themed pinball playfield that exactly matches this silhouette.&quot; Took many generations plus manual compositing — stitching the best parts from different outputs — but conceptually it nailed the brief on the first try. The art lines up with the physics because the physics is the prompt. Co-developed, not just code-generated. A bunch of design ideas came from the AI. The bumpers being giant eyeballs? Came out of an image gen, I just ran with it. I also kept asking Claude pinball-specific design questions (&quot;what does a complete pinball table have?&quot;, &quot;how should wizard mode work?&quot;, &quot;what's missing here?&quot;). I have plenty of video gamedev experience but very little pinball-specific, and Claude was a useful domain consultant for filling in genre conventions and sanity-checking the system. Things that came together easily: The alien centipede boss — multi-segmented, loses tail segments as you hit it, speeds up and turns red. Worked basically first try. An AI debug player that auto-flips and knocks the ball around. Not great, but good enough to flip on and watch while I think. Surprisingly useful — you get ideas just watching the machine play your machine. What still needed me: feel. Restitution values, flipper torque, ramp curvature, slingshot kick angles, peg bounce. The git log has an embarrassing number of &quot;tweak peg bounce&quot; / &quot;1.49 → 1.491&quot; commits. The model can write the system; a human still has to sit there bouncing balls until it feels right. The polish tail is brutal. Last week of commits is sound passes, ramp angles, message priorities, and a multiball end-check race condition. All small. None optional. Budget for it. Happy to answer workflow / Claude / LittleJS questions in the comments. &#32; submitted by &#32; /u/Slackluster [link] &#32; [comments]

</details>