---
id: inbox_b74e7c7b
date: 2026-05-02
source_ref: "[[00-inbox/2026-05-02/0131-reddit-localllama-qwen3-6-27b-at-72-tok-s-on-rtx-3090-on-w-8df4]]"
title: "Qwen3.6-27B at 72 tok/s on RTX 3090 on Windows using native vLLM (no WSL, no Docker), portable launcher and installer"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t1judm/qwen3627b_at_72_toks_on_rtx_3090_on_windows_using/
source: reddit-localllama
published_at: 2026-05-02T08:12:35+00:00
fetched_at: 2026-05-03T01:57:37.396532+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者釋出 Qwen3.6-27B 在 Windows 原生環境（無 WSL/Docker）的優化套件，RTX 3090 達成 72 tok/s（短提示）、64.5 tok/s（~25K tokens）、53.4 tok/s（127K context）。安裝流程極簡：下載 ZIP → 解壓 → 雙擊 start.bat → 選擇快照，首次運行自動下載 Lorbus AutoRound INT4 量化模型。技術基礎：vLLM Windows 補丁版本、OpenAI 相容 API（http://127.0.0.1:5001/v1）、便攜式啟動器，支援 Ampere/Ada 架構（3090、4090、A6000）。開源無遙測，彌補 Windows 與 Linux 性能差距（社區已達 80–82 tok/s），RTX 50 系列支援規劃中。"
key_points:
  - "RTX 3090 達 72 tok/s（短提示），127K context 達 53.4 tok/s，相比社區最高 80–82 tok/s 大幅縮小差距"
  - "Windows 原生執行免除 WSL/Docker 開銷；安裝簡化為三步驟，大幅降低上手難度"
  - "OpenAI 相容 API；開源無遙測；支援 Ampere/Ada；RTX 50 系列修復進行中"
tags: [qwen, vllm, windows, native-execution, portable-launcher]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen3.6-27B at 72 tok/s on RTX 3090 on Windows using native vLLM (no WSL, no Docker), portable launcher and installer

開發者釋出 Qwen3.6-27B 在 Windows 原生環境（無 WSL/Docker）的優化套件，RTX 3090 達成 72 tok/s（短提示）、64.5 tok/s（~25K tokens）、53.4 tok/s（127K context）。安裝流程極簡：下載 ZIP → 解壓 → 雙擊 start.bat → 選擇快照，首次運行自動下載 Lorbus AutoRound INT4 量化模型。技術基礎：vLLM Windows 補丁版本、OpenAI 相容 API（http://127.0.0.1:5001/v1）、便攜式啟動器，支援 Ampere/Ada 架構（3090、4090、A6000）。開源無遙測，彌補 Windows 與 Linux 性能差距（社區已達 80–82 tok/s），RTX 50 系列支援規劃中。

### 重點
- RTX 3090 達 72 tok/s（短提示），127K context 達 53.4 tok/s，相比社區最高 80–82 tok/s 大幅縮小差距
- Windows 原生執行免除 WSL/Docker 開銷；安裝簡化為三步驟，大幅降低上手難度
- OpenAI 相容 API；開源無遙測；支援 Ampere/Ada；RTX 50 系列修復進行中

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t1judm/qwen3627b_at_72_toks_on_rtx_3090_on_windows_using/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1judm/qwen3627b_at_72_toks_on_rtx_3090_on_windows_using/"> <img alt="Qwen3.6-27B at 72 tok/s on RTX 3090 on Windows using native vLLM (no WSL, no Docker), portable launcher and installer" src="https://preview.redd.it/iy44v5yzloyg1.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=2efd77e3ce68aba6d2b2c4078b3a4fed8448d5de" title="Qwen3.6-27B at 72 tok/s on RTX 3090 on Windows using native vLLM (no WSL, no Docker), portable launcher and installer" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>The angle here is native Windows, no WSL. Simple installation, open source, no telemetry. Not selling or promoting anything: <a href="https://github.com/devnen/qwen3.6-windows-server">https://github.com/devnen/qwen3.6-windows-server</a></p> <p><strong>Numbers (RTX 3090, Windows 10):</strong> - 72 tok/s short prompt - 64.5 tok/s long prompt (~25k tokens) - 53.4 tok/s at 127k ctx (single GPU) - 160k ctx on PP=2 (2×3090 GPUs)</p> <p>Honestly, these aren't <a href="https://www.reddit.com/r/LocalLLaMA">r/LocalLLaMA</a> records. Community has hit 80–82 tok/s on a 3090 with TurboQuant 3-bit KV, and 160 tok/s on a 5090 on Linux. My launcher and patched vLLM closes that gap on Windows. </p> <p><strong>Simple installation:</strong> 1. Download <code>qwen3.6-windows-server-portable-x64.zip</code> from the Release 2. Unzip anywhere. No admin, no pip, no Python required 3. Double-click <code>start.bat</code>, pick a snapshot, hit Enter 4. OpenAI-compatible endpoint at <code>http://127.0.0.1:5001/v1</code></p> <p>I had to build a patched vLLM fork for Windows to fix a few issues and make this work. I am including a portable launcher that ships the prebuilt wheel. </p> <p>First run installs the bundled vLLM wheel + deps into the embedded Python (~5–15 min, one-time), then offers to auto-download the Lorbus AutoRound INT4 quant from HuggingFace if you don't already have it. Subsequent launches skip straight to the TUI.</p> <p>Tested on Windows 10 + 2× RTX 3090 with the Lorbus AutoRound INT4 quant. Should work on any Ampere or Ada card (3090, 4090, A6000). Won't work on Pascal, Turing, Arc, or AMD.</p> <p>I have a similar launcher and a patched vLLM for Linux with some very competitive numbers, but it is still a work in progress.</p> <p>If you're on a 3090, 4090, or A6000 on Windows, give it a spin and post your numbers.</p> <p>Full details, patches, benchmarks, and config snapshots: <a href="https://github.com/devnen/qwen3.6-windows-server">https://github.com/devnen/qwen3.6-windows-server</a></p> <p>RTX 50-series (Blackwell) update: the bundled wheel doesn't ship sm_120 kernels, so 50-series cards fail at boot today. SystemPanic just shipped vllm-windows v0.20.0 with CUDA 13 + Blackwell, so it's fixable. I need to rebase my patches onto it before a 50-series build can ship.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/One_Slip1455"> /u/One_Slip1455 </a> <br /> <span><a href="https://i.redd.it/iy44v5yzloyg1.png">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t1judm/qwen3627b_at_72_toks_on_rtx_3090_on_windows_using/">[comments]</a></span> </td></tr></table>

</details>