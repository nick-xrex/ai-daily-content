---
id: inbox_df8ffac9
date: 2026-05-11
source_ref: "[[00-inbox/.../inbox_df8ffac9]]"
title: "8 Advanced Claude Code Tips I&#39;ve Discovered After Heavy Daily Use (Cost saving, Context, Custom Commands)"
url: https://www.reddit.com/r/ClaudeAI/comments/1t9w9w2/8_advanced_claude_code_tips_ive_discovered_after/
source: reddit-claudeai
published_at: 2026-05-11T07:38:49+00:00
fetched_at: 2026-05-12T01:40:58.779165+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "一位重度使用者分享了8項Claude Code進階技巧。核心包括：(1)利用自然語言讓Claude自動化git workflow，如自動摘要更改並建立PR、自動生成缺失文件和測試；(2)透過拖拽或絕對路徑在CLI中使用multimodal功能(圖片分析)；(3)用開源套件ccusage追蹤API usage和成本；(4)關鍵技巧：在40–50% context使用/compact而非等到95%，可顯著節省API成本；(5)用--continue或--resume回復中斷的session；(6)透過CLAUDE.md定義rules，支援project-specific（遞迴向上搜尋）和全域兩級別；(7)透過natural language wording調整thinking層級(light/medium/heavy/ultrathink)；(8)建立自訂命令如./.claude/commands/optimize.md以別名形式執行workflow。這套技巧體系反映了Claude Code已成為全功能開發環境的成熟度。"
key_points:
  - "/compact 在 40–50% context 時手動執行，而非自動等待 95%，可顯著降低 API 成本"
  - "CLAUDE.md 分為 project-specific (~/.claude/CLAUDE.md) 和全域層級，支援遞迴上行搜尋與 @ 引用其他文件"
  - "自訂命令 ./.claude/commands/optimize.md 支援 $ARGUMENTS 參數，可建立 git-alias-on-steroids 類型的 AI 驅動工作流"
tags: [claude-code, workflow-automation, cost-optimization, cli-tips, mcp]
topics: []
importance: 4
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## 8 Advanced Claude Code Tips I've Discovered After Heavy Daily Use (Cost saving, Context, Custom Commands)

一位重度使用者分享了8項Claude Code進階技巧。核心包括：(1)利用自然語言讓Claude自動化git workflow，如自動摘要更改並建立PR、自動生成缺失文件和測試；(2)透過拖拽或絕對路徑在CLI中使用multimodal功能(圖片分析)；(3)用開源套件ccusage追蹤API usage和成本；(4)關鍵技巧：在40–50% context使用/compact而非等到95%，可顯著節省API成本；(5)用--continue或--resume回復中斷的session；(6)透過CLAUDE.md定義rules，支援project-specific（遞迴向上搜尋）和全域兩級別；(7)透過natural language wording調整thinking層級(light/medium/heavy/ultrathink)；(8)建立自訂命令如./.claude/commands/optimize.md以別名形式執行workflow。這套技巧體系反映了Claude Code已成為全功能開發環境的成熟度。

### 重點
- /compact 在 40–50% context 時手動執行，而非自動等待 95%，可顯著降低 API 成本
- CLAUDE.md 分為 project-specific (~/.claude/CLAUDE.md) 和全域層級，支援遞迴上行搜尋與 @ 引用其他文件
- 自訂命令 ./.claude/commands/optimize.md 支援 $ARGUMENTS 參數，可建立 git-alias-on-steroids 類型的 AI 驅動工作流

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t9w9w2/8_advanced_claude_code_tips_ive_discovered_after/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# 8 Advanced Claude Code Tips I've Discovered After Heavy Daily Use (Cost saving, Context, Custom Commands)

(hey mods plz dont delete this post fr this is my own experience using claude i really wanna share some tips here but ngl my english aint great so i used ai a bit to tidy it up make it look nicer but its def my own hands-on stuff hope it helps yall thx...) 1. Automate your Git Workflow completely If you have a messy git history, or you're just deep into vibe coding and don't want to break focus to write commit messages, just let Claude Code handle it via natural language: Auto-summarize &amp; create PRs: Summarize the changes I've made so far and create a PR Generate missing docs before committing: Generate JSDocs for undocumented functions in this PR Auto-generate tests: Generate new tests for this feature and include in the PR 2. Yes, you CAN add images (Multimodal in CLI) A lot of people ditch Claude Code because they assume a CLI tool can't handle images. It fully supports vision! Here are 3 ways to do it: Drag &amp; Drop: Just drag the image file directly into your terminal (Note: Doesn't work inside Cursor's integrated terminal). Clipboard: Copy the image from your file explorer, go to the terminal, and press Ctrl + V (Yes, even on macOS, use Ctrl+V in the CLI to paste the path). Absolute Path: If you know the path, just prompt: Analyze this image: /absolute/path/to/your/image.png 3. Track your API Usage gracefully If you are on the Pro tier ($20/mo), you know the fear of exceeding limits and getting hit with overage charges. You can always type /cost natively, but Pro-tip: Use the open-source package ccusage for a much better breakdown of tokens and costs. Install: npm install -g ccusage Run: ccusage daily (Provides a beautifully formatted usage stat in your terminal). 4. /compact is your best friend (Save your API credits!) This is arguably the most important tip. Claude Code defaults to automatically compacting your conversation only when the context reaches 95% of the limit. Because every new message carries the entire previous history, your context grows exponentially . Don't wait for 95%. If you want to save money, build the habit of manually running /compact (summarizes the convo and starts a fresh one with the summary as context) or /clear (wipes context entirely) when you are around 40-50% full. 5. Resuming interrupted sessions Laptop died? Accidentally closed the terminal? No worries. Claude Code retains tools and context from previous sessions. Quick continue: claude --continue picks up exactly where you left off. Manual resume: claude --resume opens an interactive menu allowing you to select a specific past session based on start time, summary, or initial prompt. 6. Rule Management (Like .cursor/rules but for Claude) If you like .cursor/rules, you'll love this. You can define rules to stop repeating yourself about code formatting or architectural preferences. (Manage them visually by typing /memory). ./CLAUDE.md: For project-specific rules (architecture, team workflows). Note: Claude reads recursively upwards, so you can place this in any subdirectory. ~/.claude/CLAUDE.md: For global/personal preferences. Quick Rule Trick: Start your prompt with # to instantly append a rule to your local CLAUDE.md. Example: # Use arrow functions when possible You can also use @ inside rules to reference other docs: # Use my git workflows listed in u/docs/git-instructions .md 7. Triggering different levels of &quot;Thinking&quot; You might have noticed you can't explicitly toggle &quot;thinking mode&quot; when calling models via /model. Instead, you trigger it via natural language in your prompt. Depending on your wording, Claude allocates different compute: Light: think about ways to refactor. Medium: think hard for security issues. Heavy: think harder about edge cases. Maximum (Terminator mode): ultrathink why I wrote this s**t. 8. Custom Commands (AI-powered aliases) Think of these as git alias on steroids. If you create a file at ./.claude/commands/optimize.md and write: Analyze the performance of this code and suggest $ARGUMENTS optimizations From then on, you can just type: /project:optimize 3 and Claude will automatically run that exact workflow and give you 3 optimization suggestions. Custom commands have different scopes and can be incredibly powerful. I might do a Part 2 specifically on Custom Commands and open-source integrations if you guys are interested! &#32; submitted by &#32; /u/National_Honey7103 [link] &#32; [comments]

</details>