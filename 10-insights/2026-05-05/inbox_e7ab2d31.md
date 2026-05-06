---
id: inbox_e7ab2d31
date: 2026-05-05
source_ref: "[[00-inbox/.../inbox_e7ab2d31]]"
title: "Heretic 1.3 released: Reproducible models, integrated benchmarking system, reduced peak VRAM usage, broader model support, and more"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t4hwup/heretic_13_released_reproducible_models/
source: reddit-localllama
published_at: 2026-05-05T14:57:32+00:00
fetched_at: 2026-05-06T13:38:45.274355+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Heretic 1.3 發布，這是開源 LLM 去審查工具。該版本核心創新是解決可重現性問題，生成 reproduce 目錄包含所有環境資訊（PyTorch 版本、GPU、驅動、CUDA 庫），讓他人能逐位重現相同模型，該工作涉及貢獻者超過 250 次評論的多週協作。新版本整合基準測試系統，支援 MMLU、EQ-Bench、GSM8K、HellaSwag，無需手動配置即可直接運行，基於 lm-evaluation-harness 學術標準。另外優化了 VRAM 使用，支援最新模型架構如 Qwen 3.5、Gemma 4，GitHub stars 已達 20,000、累計 1,300 萬次模型下載。"
key_points:
  - "可重現性系統：生成完整環境信息讓他人逐位重現模型，解決張量運算非確定性問題"
  - "整合基準測試：支援 MMLU、EQ-Bench、GSM8K、HellaSwag，基於 lm-evaluation-harness 標準"
  - "優化 VRAM 使用、支援 Qwen 3.5 和 Gemma 4 等新模型架構"
tags: [heretic, reproducibility, model-decensoring, benchmarking, open-source]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## Heretic 1.3 released: Reproducible models, integrated benchmarking system, reduced peak VRAM usage, broader model support, and more

Heretic 1.3 發布，這是開源 LLM 去審查工具。該版本核心創新是解決可重現性問題，生成 reproduce 目錄包含所有環境資訊（PyTorch 版本、GPU、驅動、CUDA 庫），讓他人能逐位重現相同模型，該工作涉及貢獻者超過 250 次評論的多週協作。新版本整合基準測試系統，支援 MMLU、EQ-Bench、GSM8K、HellaSwag，無需手動配置即可直接運行，基於 lm-evaluation-harness 學術標準。另外優化了 VRAM 使用，支援最新模型架構如 Qwen 3.5、Gemma 4，GitHub stars 已達 20,000、累計 1,300 萬次模型下載。

### 重點
- 可重現性系統：生成完整環境信息讓他人逐位重現模型，解決張量運算非確定性問題
- 整合基準測試：支援 MMLU、EQ-Bench、GSM8K、HellaSwag，基於 lm-evaluation-harness 標準
- 優化 VRAM 使用、支援 Qwen 3.5 和 Gemma 4 等新模型架構

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t4hwup/heretic_13_released_reproducible_models/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Heretic 1.3 released: Reproducible models, integrated benchmarking system, reduced peak VRAM usage, broader model support, and more

<!-- SC_OFF --><div class="md"><p>Dear fellow Llamas, it is my distinct pleasure to announce the immediate availability of version 1.3 of <strong>Heretic</strong> (<a href="https://github.com/p-e-w/heretic">https://github.com/p-e-w/heretic</a>), the leading software for removing censorship from language models.</p> <p>This was a long and eventful release cycle, during which Heretic became a high-profile open source project with 20,000 GitHub stars and more than 13 million total model downloads (not counting the models from a certain &quot;competitor&quot; who was recently found to have been using a plagiarized fork of Heretic under the hood). The topic of model decensoring has exploded in popularity, with many clones and forks popping up, some of them clouding their techniques in mystique, technical jargon, or tens of thousands of lines of LLM-written junk code.</p> <p>I am happy to say that Heretic is moving in the exact opposite direction. Instead of making it more difficult to understand what is going on, the new release makes it easier and more transparent. The headline feature in Heretic 1.3 is <strong>reproducible runs</strong>. This was a much more difficult problem to solve than it might appear to be at first glance, because the results of tensor operations can depend on the PyTorch version, the GPU, the driver, the accelerator library, and whether Saturn is Ascendant or not. This means that in order to ensure reproducibility, <em>all</em> of that information must be collected and preserved. This mammoth task was taken up by long-time contributor Vinay-Umrethe, who wrote the majority of the code in the course of an intense multi-week collaboration in which over 250 comments were exchanged.</p> <p>As a result, when publishing an abliterated model to Hugging Face, you now have the option to have Heretic generate a <code>reproduce</code> directory in the repository, which contains everything another person needs to know in order to generate a byte-for-byte identical model themselves (<a href="https://huggingface.co/p-e-w/Qwen3.5-4B-heretic/blob/main/reproduce/README.md">example of such a directory</a>). Gone are the days of &quot;I can't seem to get such low numbers on my own machine&quot;; you now can! While the reproducibility system is already immensely helpful and educational by itself, in the future it will form the backbone of something even more ambitious and exciting, which I will announce soon. <em>Please note that publishing reproducibility information is completely optional, and Heretic always prompts before doing so. You are in control of what is uploaded at all times.</em></p> <p>There's more! You know how it can be difficult to tell with certainty whether an abliterated model has incurred significant damage to its capabilities? Heretic now includes <strong>the world's simplest benchmarking system</strong>, allowing you to run standard benchmarks like MMLU, EQ-Bench, GSM8K, and HellaSwag directly from Heretic, without having to fumble with any configuration and without even having to export the model first. This makes it much easier to decide whether a model is worth publishing, or whether you should look at another trial instead. The system is based on lm-evaluation-harness, the academic gold standard for running LLM benchmarks, allowing the resulting metrics to be <em>directly</em> compared against numbers published online.</p> <p>In the course of a typical run, Heretic computes various functions on tensors. This can involve intermediate tensors being manifested in GPU memory that take up large amounts of VRAM. magiccodingman analyzed this in detail, and implemented optimizations that <strong>substantially reduce peak VRAM usage</strong>, allowing larger models to be processed.</p> <p>Model architectures continue to evolve and become more complex, and Heretic is keeping up! farolone and MoonRide303 improved Heretic's layer and module handling logic, making it far more generic and <strong>allowing it to process latest-generation models like Qwen3.5 and Gemma 4</strong>, among others.</p> <p>Please see the release notes for the full list of improvements and fixes. More exciting stuff is coming in future versions!</p> <p>Cheers :)</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/-p-e-w-"> /u/-p-e-w- </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4hwup/heretic_13_released_reproducible_models/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t4hwup/heretic_13_released_reproducible_models/">[comments]</a></span>

</details>