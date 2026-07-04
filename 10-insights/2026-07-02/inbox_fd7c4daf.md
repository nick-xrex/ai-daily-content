---
id: inbox_fd7c4daf
date: 2026-07-02
source_ref: "[[00-inbox/2026-07-02/0115-simon-willison-llm-coding-agent-0-1a0-f0a5]]"
title: "llm-coding-agent 0.1a0"
url: https://simonwillison.net/2026/Jul/2/llm-coding-agent/#atom-everything
source: simon-willison
published_at: 2026-07-02T19:33:12+00:00
fetched_at: 2026-07-04T01:23:13.278999+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Simon Willison 基於 Fable 5 開發了 llm-coding-agent v0.1a0，一個 Python 編碼 agent 框架。該專案使用 Claude Code 風格迭代，依賴 llm 最新 alpha 版本，實現 6 個核心工具：edit_file、execute_command、list_files、read_file、search_files、write_file。提供 CLI 介面（uvx llm code）與 Python API（CodingAgent 類），支援自動測試與多重權限控制。首個 alpha 已發布至 PyPI，展示了 Fable-powered 編碼 agent 的可行性。"
key_points:
  - "6 個編碼工具：edit_file、execute_command、list_files、read_file、search_files、write_file，支援 timeout 與行號定位"
  - "雙介面支援：CLI 模式（--yolo、權限控制）與 Python API（CodingAgent 類），自動化測試與提交"
  - "首個 alpha 發布至 PyPI，可用 uvx 快速試用，支援 GPT-5.5 與 Claude 等模型"
tags: [llm-coding-agent, python-agent, open-source, llm-tools]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## llm-coding-agent 0.1a0

Simon Willison 基於 Fable 5 開發了 llm-coding-agent v0.1a0，一個 Python 編碼 agent 框架。該專案使用 Claude Code 風格迭代，依賴 llm 最新 alpha 版本，實現 6 個核心工具：edit_file、execute_command、list_files、read_file、search_files、write_file。提供 CLI 介面（uvx llm code）與 Python API（CodingAgent 類），支援自動測試與多重權限控制。首個 alpha 已發布至 PyPI，展示了 Fable-powered 編碼 agent 的可行性。

### 重點
- 6 個編碼工具：edit_file、execute_command、list_files、read_file、search_files、write_file，支援 timeout 與行號定位
- 雙介面支援：CLI 模式（--yolo、權限控制）與 Python API（CodingAgent 類），自動化測試與提交
- 首個 alpha 發布至 PyPI，可用 uvx 快速試用，支援 GPT-5.5 與 Claude 等模型

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/2/llm-coding-agent/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: llm-coding-agent 0.1a0 
 Another Fable 5 experiment. Now that my LLM library has evolved into more of an agent framework it's time to see what a simple coding agent would look like built on it. 
 I started a new Python library using my python-lib-template-repository GitHub template repository, then ran these two prompts (here's the Claude Code for web transcript ): 
 
 Write a spec.md for this project - it will depend on the latest “llm” alpha from PyPI and implement a Claude code style coding agent complete with tools for reading and editing files and executing commands 
 
 Then: 
 
 Commit the spec, then build it using red/green TDD in a series of sensible commits (each with passing tests and updated docs) - occasionally manually test it using the OpenAI API key in your environment 
 
 Here's the spec , the resulting README file , and the sequence of commits . 
 I've shipped a slop-alpha to PyPI, so you can run the new agent like this: 
 uvx --prerelease=allow --with llm-coding-agent llm code
 
 It's pretty good for a first attempt! Here's the (Fable-authored) README , which lists recipes like llm code --yolo and llm code --allow "pytest*" --allow "git diff*" . 
 It also presents a Python API based around a CodingAgent(model="gpt-5.5", root="/path", approve=True).run("Fix the failing test in tests/test_parser.py") class which I didn't ask for but I'm delighted to see implemented. 
 Here's the suite of tools it implemented , listed using uvx ... llm tools : 
 
 CodingTools_edit_file(path: str, old_string: str, new_string: str, replace_all: bool = False) -&gt; str 
 Replace an exact string in a file. 
 old_string must match the file contents exactly (including
whitespace) and must identify a unique location unless replace_all
is true. Returns a diff of the change so it can be verified. 
 CodingTools_execute_command(command: str, timeout: int = 120) -&gt; str 
 Run a shell command in the session root directory. 
 Returns combined stdout and stderr followed by an Exit code line.
timeout is in seconds (maximum 600); on timeout the whole process
tree is killed. 
 CodingTools_list_files(pattern: str = '**/*', path: str = '.') -&gt; str 
 List files matching a glob pattern, newest first. 
 Skips hidden directories, node_modules, __pycache__ and (in a git
repository) anything covered by .gitignore. Returns at most 200
paths relative to the searched directory. 
 CodingTools_read_file(path: str, offset: int = 0, limit: int = 2000) -&gt; str 
 Read a text file, returning numbered lines like cat -n. 
 Paths are relative to the session root. Use offset (0-based first
line) and limit (max lines) to page through files too large to read
in one call. 
 CodingTools_search_files(pattern: str, path: str = '.', glob: str = None, max_results: int = 100) -&gt; str 
 Search file contents for a regular expression. 
 Returns matches as path:line_number:line, capped at max_results.
Use glob (e.g. "*.py") to restrict which files are searched. 
 CodingTools_write_file(path: str, content: str) -&gt; str 
 Create or overwrite a file with the given content. 
 Parent directories are created as needed. Prefer edit_file for
modifying existing files. 
 
 I tried it out by running llm code --yolo and then prompting: 
 
 mkdir /tmp/demo and then in that folder create a simple swiftui CLI app for telling the time in ascii art 
 
 Here's the transcript , in which GPT-5.5 reasoning notes that "SwiftUI isn't suitable for a true CLI" and then builds an app that outputs this on swift run AsciiTime : 
 
 █ █████ ████ █ █ ███ 
 ██ █ █ █ ██ █ ██ █ █ 
 █ ████ ███ █ █ █ 
 █ █ █ █ █ █ █ █ 
 ███ ████ ████ ███ ███ █████
 
 
 
 Tags: projects , ai , generative-ai , llm , llm-tool-use , coding-agents , claude-code , claude-mythos-fable

</details>