---
id: inbox_55e787b1
date: 2026-05-11
source_ref: "[[00-inbox/2026-05-11/0113-simon-willison-using-llm-in-the-shebang-line-of-a-scrip-f044]]"
title: "Using LLM in the shebang line of a script"
url: https://simonwillison.net/2026/May/11/llm-shebang/#atom-everything
source: simon-willison
published_at: 2026-05-11T18:48:57+00:00
fetched_at: 2026-05-12T01:17:36.623140+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 揭示可在 shell script 的 shebang 行直接使用 LLM CLI，無需額外 wrapper。最簡單形式為 `#!/usr/bin/env -S llm -f` 後接自然語言提示，腳本本身即成為 LLM 請求。進階用法支援 `-T tool_name` 調用具體工具（如 `llm_time`），或完整 YAML 定義自訂工具及模型，Python 函數可直接定義為工具供 LLM 調用。示例：計算器腳本使用 multiply 與 add 工具自動執行複雜計算。此技巧將 LLM 整合提升至開發工作流的基本層，使文本提示與可執行指令碼統一化。"
key_points:
  - "`#!/usr/bin/env -S llm -f` 可直接執行 LLM prompt，無需包裝；支援 `-T tool_name` 調用命名工具或完整 YAML 配置"
  - "YAML 定義自訂模型、系統提示、Python 函數工具；函數簽名自動轉換為工具定義供 LLM 調用"
  - "實例：計算器腳本 `./calc.sh 'what is 2344 * 5252 + 134'` 自動編排 multiply / add 工具調用，結果 12,310,822"
tags: [llm-cli, developer-tools, scripting, llm-integration]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Using LLM in the shebang line of a script

Simon Willison 揭示可在 shell script 的 shebang 行直接使用 LLM CLI，無需額外 wrapper。最簡單形式為 `#!/usr/bin/env -S llm -f` 後接自然語言提示，腳本本身即成為 LLM 請求。進階用法支援 `-T tool_name` 調用具體工具（如 `llm_time`），或完整 YAML 定義自訂工具及模型，Python 函數可直接定義為工具供 LLM 調用。示例：計算器腳本使用 multiply 與 add 工具自動執行複雜計算。此技巧將 LLM 整合提升至開發工作流的基本層，使文本提示與可執行指令碼統一化。

### 重點
- `#!/usr/bin/env -S llm -f` 可直接執行 LLM prompt，無需包裝；支援 `-T tool_name` 調用命名工具或完整 YAML 配置
- YAML 定義自訂模型、系統提示、Python 函數工具；函數簽名自動轉換為工具定義供 LLM 調用
- 實例：計算器腳本 `./calc.sh 'what is 2344 * 5252 + 134'` 自動編排 multiply / add 工具調用，結果 12,310,822

**原文：** [simon-willison](https://simonwillison.net/2026/May/11/llm-shebang/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

TIL: Using LLM in the shebang line of a script 
 Kim_Bruning on Hacker News : 
 
 But seriously, you can put a shebang on an english text file now (if you're sufficiently brave) [...] 
 
 This inspired me to look at patterns for doing exactly that with LLM . Here's the simplest, which takes advantage of LLM fragments : 
 #!/usr/bin/env -S llm -f
Generate an SVG of a pelican riding a bicycle
 
 But you can also incorporate tool calls using the -T name_of_tool option: 
 #!/usr/bin/env -S llm -T llm_time -f
Write a haiku that mentions the exact current time
 
 Or even execute YAML templates directly that define extra tools as Python functions: 
 # !/usr/bin/env -S llm -t 
 model : gpt-5.4-mini 
 system : | 
 Use tools to run calculations 
 functions : | 
 def add(a: int, b: int) -&gt; int: 
 return a + b 
 def multiply(a: int, b: int) -&gt; int: 
 return a * b 

 Then: 
 ./calc.sh 'what is 2344 * 5252 + 134' --td
 
 Which outputs (thanks to that --td tools debug option): 
 Tool call: multiply({'a': 2344, 'b': 5252})
 12310688

Tool call: add({'a': 12310688, 'b': 134})
 12310822

2344 × 5252 + 134 = **12,310,822**
 
 Read the full TIL for a more complex example that uses the Datasette SQL API to answer questions about content on my blog. 
 
 
 Tags: llm , llm-tool-use , llms , ai , generative-ai

</details>