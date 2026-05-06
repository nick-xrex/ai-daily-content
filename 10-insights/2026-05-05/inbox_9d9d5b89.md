---
id: inbox_9d9d5b89
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_9d9d5b89]]"
title: "ProgramBench: Can we really rebuild huge binaries from scratch? (doesn&#39;t look like it)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t4j4s9/programbench_can_we_really_rebuild_huge_binaries/
source: reddit-localllama
published_at: 2026-05-05T15:40:52+00:00
fetched_at: 2026-05-06T13:38:45.285374+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Meta 等機構開源 ProgramBench，一個 200 個任務的基準測試，用於評估 AI agent 從零開始重建大型二進制文件的能力。Agent 僅獲得目標可執行檔和 readme，無互聯網存取、無反編譯。為防止作弊和提升任務多樣性，團隊耗費 $50k 生成 600 萬行行為測試並篩選最佳版本。目前公開的結果為閉源模型，開源模型表現更差（因過度擬合 SWE-bench 導致泛化能力不足）。完整開源於 GitHub、Hugging Face 和 Docker，可用 `pip install programbench && programbench eval` 快速評估，網站 programbench.com 提供詳細 FAQ。"
key_points:
  - "200 個任務基準測試，$50k 生成 600 萬行行為測試，黑盒評估無反編譯"
  - "開源模型在新任務上泛化能力顯著不足，傾向過度擬合現有基準如 SWE-bench"
  - "提供 pip 安裝和 Docker 鏡像，支援自動評估和防作弊檢查"
tags: [programbench, benchmark, program-synthesis, agent-evaluation, meta]
topics: []
importance: 4
novelty: 4
insight_quality: 4
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## ProgramBench: Can we really rebuild huge binaries from scratch? (doesn't look like it)

Meta 等機構開源 ProgramBench，一個 200 個任務的基準測試，用於評估 AI agent 從零開始重建大型二進制文件的能力。Agent 僅獲得目標可執行檔和 readme，無互聯網存取、無反編譯。為防止作弊和提升任務多樣性，團隊耗費 $50k 生成 600 萬行行為測試並篩選最佳版本。目前公開的結果為閉源模型，開源模型表現更差（因過度擬合 SWE-bench 導致泛化能力不足）。完整開源於 GitHub、Hugging Face 和 Docker，可用 `pip install programbench && programbench eval` 快速評估，網站 programbench.com 提供詳細 FAQ。

### 重點
- 200 個任務基準測試，$50k 生成 600 萬行行為測試，黑盒評估無反編譯
- 開源模型在新任務上泛化能力顯著不足，傾向過度擬合現有基準如 SWE-bench
- 提供 pip 安裝和 Docker 鏡像，支援自動評估和防作弊檢查

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t4j4s9/programbench_can_we_really_rebuild_huge_binaries/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# ProgramBench: Can we really rebuild huge binaries from scratch? (doesn't look like it)

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4j4s9/programbench_can_we_really_rebuild_huge_binaries/"> <img alt="ProgramBench: Can we really rebuild huge binaries from scratch? (doesn't look like it)" src="https://preview.redd.it/0u4039bq8czg1.png?width=140&amp;height=128&amp;auto=webp&amp;s=c4a72fdaa2f31ddc58fcbf309f1bccc3ecab55f5" title="ProgramBench: Can we really rebuild huge binaries from scratch? (doesn't look like it)" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>There's been quite a few case studies recently on agents building whole programs from scratch, but most of them test a single or just a few projects with hand-tuned setups.</p> <p>We've spent the last couple of months formalizing this setting and building a benchmark of 200 tasks while doubling down on testing, cheat prevention, and task diversity.</p> <p>Our agent ONLY gets a target executable and some readme/usage files. The agent must choose a language, design abstraction layers, and architect the entire program. No internet access or any other way of cheating. No decompilation.</p> <p>We've also spent some 50k to generate 6M lines of behavioral tests and then filtered them down to keep the best ones. Because they are just testing executables as a black box, we do not make any assumptions on even the language that the LM uses to implement the program.</p> <p>All of the results are at <a href="http://programbench.com">programbench.com</a> . There's also a big FAQ at the bottom.</p> <p>We've just open-sourced our github, huggingface and docker images.</p> <p>Essentially you can just start evaluating with <code>pip install programbench &amp;&amp; programbench eval &lt;your submission&gt;</code></p> <p>Github is at <a href="https://github.com/facebookresearch/programbench">https://github.com/facebookresearch/programbench</a></p> <p>Sorry that it's just closed source models right now, we have a few open-source models in the pipeline, but so far we've had an even harder time at getting them to behave well with these tasks (open source models tend to be somewhat more overfitted to things like SWE-bench, so they often have a harder time with new benchmarks).</p> <p>We're also planning to open the benchmark for submissions quite soon, similar to what we did on SWE-bench and its variants.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/klieret"> /u/klieret </a> <br /> <span><a href="https://www.reddit.com/gallery/1t4j4s9">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4j4s9/programbench_can_we_really_rebuild_huge_binaries/">[comments]</a></span> </td></tr></table>

</details>