---
id: inbox_6d96e553
date: 2026-05-03
source_ref: "[[00-inbox/.../inbox_6d96e553]]"
title: "Qwen3-TTS but in OpenVINO, from scratch"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t2v0zh/qwen3tts_but_in_openvino_from_scratch/
source: reddit-localllama
published_at: 2026-05-03T19:30:02+00:00
fetched_at: 2026-05-04T14:28:44.712716+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者從零開始用 PyTorch 重新實作 Qwen3-TTS 並轉換為 OpenVINO IR 格式，代碼已在 GitHub 公開並於 2026 年 3 月合併到 OpenArc 專案。核心學習是透過分析 nn.Module 的數據流和設備放置策略，讓 OpenVINO 編譯器自動選擇最優 kernel，避免手動幹預。作者使用 Claude Opus 4.5 進行開發協助，但發現其在有狀態 KV cache 和 kernel fusion 決策上存在限制。目前實現支援 1.7B 模型在 CPU/GPU 上運行，NPU 支援正在開發中。OpenVINO 文檔不充分導致優化流程複雜，但透過 AI 工具和大量測試仍可實現高效轉換。"
key_points:
  - "Qwen3-TTS 1.7B 模型透過 OpenVINO 優化，支援 CPU/GPU（如 A770）語音克隆推理"
  - "優化方法：分析 PyTorch nn.Module 數據流和設備放置邏輯，由編譯器自動融合 kernel，無需手動幹預"
  - "Claude Opus 4.5 輔助開發，但在有狀態 KV cache 和 kernel fusion 預測上需人工指導"
tags: [qwen3-tts, openvino-optimization, pytorch-conversion, device-placement, kv-cache]
topics: []
importance: 3
novelty: 3
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Qwen3-TTS but in OpenVINO, from scratch

開發者從零開始用 PyTorch 重新實作 Qwen3-TTS 並轉換為 OpenVINO IR 格式，代碼已在 GitHub 公開並於 2026 年 3 月合併到 OpenArc 專案。核心學習是透過分析 nn.Module 的數據流和設備放置策略，讓 OpenVINO 編譯器自動選擇最優 kernel，避免手動幹預。作者使用 Claude Opus 4.5 進行開發協助，但發現其在有狀態 KV cache 和 kernel fusion 決策上存在限制。目前實現支援 1.7B 模型在 CPU/GPU 上運行，NPU 支援正在開發中。OpenVINO 文檔不充分導致優化流程複雜，但透過 AI 工具和大量測試仍可實現高效轉換。

### 重點
- Qwen3-TTS 1.7B 模型透過 OpenVINO 優化，支援 CPU/GPU（如 A770）語音克隆推理
- 優化方法：分析 PyTorch nn.Module 數據流和設備放置邏輯，由編譯器自動融合 kernel，無需手動幹預
- Claude Opus 4.5 輔助開發，但在有狀態 KV cache 和 kernel fusion 預測上需人工指導

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t2v0zh/qwen3tts_but_in_openvino_from_scratch/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Qwen3-TTS but in OpenVINO, from scratch

<!-- SC_OFF --><div class="md"><p>Hello everyone,</p> <p>I finally got around to preparing my implementation of Qwen3-TTS in OpenVINO format as a codebase. This work was done in early 2026, merged to OpenArc in March and I kept forgetting about releasing the code. Here we are. <a href="https://github.com/SearchSavior/Qwen3-TTS-OpenVINO">https://github.com/SearchSavior/Qwen3-TTS-OpenVINO</a></p> <p>One guy from our discord speaks russian and I wanted to voice clone elmo on my A770,so I decided to from scratch Qwen3-TTS in pytorch, ignoring transformers (except for AutoTokenizer, my beloved) to really get inside how you design an OpenVINO conversion to their model format. </p> <p>The key learning is: you take an <code>nn.Module</code> with some logic, it's forward method, study the data flow, then iterate until you find the combination of data flow and device placement which lets the openvino compiler choose the best kernels. Interfering with this process ie, custom kernels is a totally seperate mission for future work. There were a ton of steps in between, and a key learning for me in this project was taking better notes. </p> <p>AI assistance was used... but honestly I'm not sure how it could be done without it. Even Opus 4.5 could not make good openvino flavored choices, especially around stateful kv cache and could not anticipate kernel fusion without extensive guidance. Intel does not put enough effort into documenting their engineering practices... which makes openvino feel not so open after all. BUT, with AI tools and some effort, it is possible.</p> <p>This codebase can be generalized for optimizing any pytorch model for openvino IR format. I tried to make sure the code is easy to follow, but it is quite demanding conceptually, drawing on poorly documented openvino concepts Opus implemented based on targeted examples from the upstream source I was able to conjure from memory, with hours of testing on top. Though AI assisted, this code was in no way <em>full send vibe coded</em>.</p> <p>It's all live in OpenArc now, covering only 1.7B size for CPUs and GPUs; I had issues with 0.6B I did not investigate further. NPU support PRs are most welcome. </p> <p>Unlike other implementation posts, I haven't included any benchmarks mostly due to time constraints plus changes I made to the inference code in the OpenArc PR vs what's in this repo. If there is interest we can bench OpenArc vs pytorch cpu/xpu.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/Echo9Zulu-"> /u/Echo9Zulu- </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2v0zh/qwen3tts_but_in_openvino_from_scratch/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2v0zh/qwen3tts_but_in_openvino_from_scratch/">[comments]</a></span>

</details>