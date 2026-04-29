---
id: inbox_d3361bb8
date: 2026-04-28
source_ref: "[[00-inbox/2026-04-28/0657-simon-willison-what-s-new-in-pip-26-1-lockfiles-and-dep-3429]]"
title: "What&#39;s new in pip 26.1 - lockfiles and dependency cooldowns!"
url: https://simonwillison.net/2026/Apr/28/pip-261/#atom-everything
source: simon-willison
published_at: 2026-04-28T05:23:05+00:00
fetched_at: 2026-04-29T07:04:34.167300+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Python 套件管理工具 pip 發布 26.1 版本，主要移除 Python 3.9 支援（該版本已於 2024 年 10 月終止維護）。核心新功能之一是 `pip lock` 命令，可自動生成 pylock.toml 鎖定文件，記錄所有依賴的完整版本樹（測試示例：Datasette + LLM 的完整依賴達 519 行）。另一項重要功能是依賴冷卻期機制（`--uploaded-prior-to PXD` 選項），允許指定最少發布距離，遵循 ISO 8601 duration format（例 P4D 表示至少 4 天前發布），強化供應鏈安全性，降低引入新套件漏洞的風險。"
key_points:
  - "新 pip lock 命令生成 pylock.toml 鎖定文件，記錄完整依賴樹（Datasette+LLM 範例達 519 行）"
  - "依賴冷卻期（--uploaded-prior-to）：指定最少發布距離（如 P4D=至少 4 天前發布），減少新套件風險"
  - "移除 Python 3.9 支援（已 EOL），聚焦現代版本"
tags: [python, pip, dependency-management, supply-chain-security]
topics: []
importance: 2
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## What's new in pip 26.1 - lockfiles and dependency cooldowns!

Python 套件管理工具 pip 發布 26.1 版本，主要移除 Python 3.9 支援（該版本已於 2024 年 10 月終止維護）。核心新功能之一是 `pip lock` 命令，可自動生成 pylock.toml 鎖定文件，記錄所有依賴的完整版本樹（測試示例：Datasette + LLM 的完整依賴達 519 行）。另一項重要功能是依賴冷卻期機制（`--uploaded-prior-to PXD` 選項），允許指定最少發布距離，遵循 ISO 8601 duration format（例 P4D 表示至少 4 天前發布），強化供應鏈安全性，降低引入新套件漏洞的風險。

### 重點
- 新 pip lock 命令生成 pylock.toml 鎖定文件，記錄完整依賴樹（Datasette+LLM 範例達 519 行）
- 依賴冷卻期（--uploaded-prior-to）：指定最少發布距離（如 P4D=至少 4 天前發布），減少新套件風險
- 移除 Python 3.9 支援（已 EOL），聚焦現代版本

**原文：** [simon-willison](https://simonwillison.net/2026/Apr/28/pip-261/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<p><strong><a href="https://ichard26.github.io/blog/2026/04/whats-new-in-pip-26.1/">What&#x27;s new in pip 26.1 - lockfiles and dependency cooldowns!</a></strong></p>
Richard Si describes an excellent set of upgrades to Python's default <code>pip</code> tool for installing dependencies.</p>
<p>This version drops support for Python 3.9 - fair enough, since it's been EOL <a href="https://devguide.python.org/versions/">since October</a>. macOS still ships with <code>python3</code> as a default Python 3.9, so I tried out the new Python version against Python 3.14 like this:</p>
<pre><code>uv python install 3.14
mkdir /tmp/experiment
cd /tmp/experiment
python3.14 -m venv venv
source venv/bin/activate
pip install -U pip
pip --version
</code></pre>
<p>This confirmed I had <code>pip 26.1</code> - then I tried out the new lock files:</p>
<pre><code>pip lock datasette llm
</code></pre>
<p>This installs Datasette and LLM and all of their dependencies and writes the whole lot to a 519 line <code>pylock.toml</code> file - <a href="https://gist.github.com/simonw/ff52c33f4d3a381b8e53c6a3aa0213f8">here's the result</a>.</p>
<p>The new release also supports dependency cooldowns, <a href="https://simonwillison.net/2026/Mar/24/package-managers-need-to-cool-down/">discussed here previously</a>, via the new <code>--uploaded-prior-to PXD</code> option where X is a number of days. The format is <code>P-number-of-days-D</code>, following <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations">ISO duration format</a> but only supporting days.</p>
<p>I shipped a new release of LLM, version 0.31, <a href="https://simonwillison.net/2026/Apr/24/llm/">three days ago</a>. Here's how to use the new <code>--uploaded-prior-to P4D</code> option to ask for a version that is at least 4 days old.</p>
<pre><code>pip install llm --uploaded-prior-to P4D
venv/bin/llm --version
</code></pre>
<p>This gave me version 0.30.

    <p><small></small>Via <a href="https://lobste.rs/s/w2oiaq/what_s_new_pip_26_1_lockfiles_dependency">Lobste.rs</a></small></p>


    <p>Tags: <a href="https://simonwillison.net/tags/packaging">packaging</a>, <a href="https://simonwillison.net/tags/pip">pip</a>, <a href="https://simonwillison.net/tags/python">python</a>, <a href="https://simonwillison.net/tags/security">security</a>, <a href="https://simonwillison.net/tags/supply-chain">supply-chain</a></p>

</details>