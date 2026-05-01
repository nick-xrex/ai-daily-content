---
id: inbox_3b452c7f
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-localllama-cuda-rocm-simultaneously-with-dggml-back-5b91]]"
title: "Cuda + ROCm simultaneously with -DGGML_BACKEND_DL=ON !"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t0bkaf/cuda_rocm_simultaneously_with_dggml_backend_dlon/
source: reddit-localllama
published_at: 2026-04-30T22:46:46+00:00
fetched_at: 2026-05-01T13:31:34.636779+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "llama.cpp 突破性技術實現：使用 -DGGML_BACKEND_DL=ON 編譯標誌，在單機同時運行 CUDA 和 ROCm 後端，無需 Vulkan 中介。以 MiniMax 2.7 Q4 為例，CUDA 加載 83.6 GB 權重、ROCm 加載 40.3 GB 權重、CPU Host 622.8 MB，共 63 層全部離線至 GPU。主要優勢在於 prefill 速度提升。編譯需避免 CPU 變體衝突（如 Alderlake SSE42 等），在 Ryzen 5950X 上驗證可行。"
key_points:
  - "雙後端推理配置：MiniMax 2.7 Q4 同時使用 CUDA (83.6GB) 和 ROCm (40.3GB)，63 層全離線，優化 prefill 階段"
  - "編譯指令集：-DGGML_BACKEND_DL=ON 配合 HIP/CUDA 編譯器，需移除衝突的 CPU 變體；Windows 使用 ROCm 6.4 + CUDA 13.1"
  - "運行環境設置：PATH 包含 ROCm/bin，執行時設定 NCCL 和 Flash Attention 標誌"
tags: [llama-cpp, cuda-rocm, inference-optimization, hardware-integration]
topics: []
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## Cuda + ROCm simultaneously with -DGGML_BACKEND_DL=ON !

llama.cpp 突破性技術實現：使用 -DGGML_BACKEND_DL=ON 編譯標誌，在單機同時運行 CUDA 和 ROCm 後端，無需 Vulkan 中介。以 MiniMax 2.7 Q4 為例，CUDA 加載 83.6 GB 權重、ROCm 加載 40.3 GB 權重、CPU Host 622.8 MB，共 63 層全部離線至 GPU。主要優勢在於 prefill 速度提升。編譯需避免 CPU 變體衝突（如 Alderlake SSE42 等），在 Ryzen 5950X 上驗證可行。

### 重點
- 雙後端推理配置：MiniMax 2.7 Q4 同時使用 CUDA (83.6GB) 和 ROCm (40.3GB)，63 層全離線，優化 prefill 階段
- 編譯指令集：-DGGML_BACKEND_DL=ON 配合 HIP/CUDA 編譯器，需移除衝突的 CPU 變體；Windows 使用 ROCm 6.4 + CUDA 13.1
- 運行環境設置：PATH 包含 ROCm/bin，執行時設定 NCCL 和 Flash Attention 標誌

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t0bkaf/cuda_rocm_simultaneously_with_dggml_backend_dlon/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0bkaf/cuda_rocm_simultaneously_with_dggml_backend_dlon/"> <img alt="Cuda + ROCm simultaneously with -DGGML_BACKEND_DL=ON !" src="https://preview.redd.it/mwcq83ldoeyg1.png?width=640&amp;crop=smart&amp;auto=webp&amp;s=68b47688979f8139322fd922758df5627b53d0cb" title="Cuda + ROCm simultaneously with -DGGML_BACKEND_DL=ON !" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I invested quite a bit of time and it wasn't easy but finally I can run models like Minimax 2.7 Q4 using Cuda+ROCm at the same time bypassing Vulkan.</p> <p>load_tensors: offloaded 63/63 layers to GPU</p> <p>load_tensors: CUDA0 model buffer size = 83650.42 MiB</p> <p>load_tensors: CUDA_Host model buffer size = 622.76 MiB</p> <p>load_tensors: ROCm0 model buffer size = 40314.35 MiB</p> <p>the main advantage is the prefill.</p> <p>On windows :</p> <p>rmdir /s /q build</p> <p>cmake -B build -G Ninja ^</p> <p>-DCMAKE_C_COMPILER=&quot;C:/Program Files/AMD/ROCm/6.4/bin/clang-cl.exe&quot; ^</p> <p>-DCMAKE_CXX_COMPILER=&quot;C:/Program Files/AMD/ROCm/6.4/bin/clang-cl.exe&quot; ^</p> <p>-DCMAKE_HIP_COMPILER=&quot;C:/Program Files/AMD/ROCm/6.4/bin/clang-cl.exe&quot; ^</p> <p>-DCMAKE_PREFIX_PATH=&quot;C:/Program Files/AMD/ROCm/6.4&quot; ^</p> <p>-DHIP_ROOT_DIR=&quot;C:/Program Files/AMD/ROCm/6.4&quot; ^</p> <p>-DGGML_HIP=ON ^</p> <p>-DGGML_CUDA=ON ^</p> <p>-DGGML_BACKEND_DL=ON ^</p> <p>-DGGML_CPU_ALL_VARIANTS=ON ^</p> <p>-DGGML_AVX_VNNI=OFF ^</p> <p>-DGGML_AVX512=OFF ^</p> <p>-DGGML_AVX512_VBMI=OFF ^</p> <p>-DGGML_AVX512_VNNI=OFF ^</p> <p>-DGGML_AVX512_BF16=OFF ^</p> <p>-DGGML_AMX_TILE=OFF ^</p> <p>-DGGML_AMX_INT8=OFF ^</p> <p>-DGGML_AMX_BF16=OFF ^</p> <p>-DCMAKE_CUDA_COMPILER=&quot;C:/Program Files/NVIDIA GPU Computing Toolkit/CUDA/v13.1/bin/nvcc.exe&quot; ^</p> <p>-DCMAKE_CUDA_ARCHITECTURES=&quot;120&quot; ^</p> <p>-DCMAKE_BUILD_TYPE=Release</p> <p>___________________</p> <p>cmake --build build -j</p> <p>_______________________</p> <p>Unfortunately, this flag: -DGGML_CPU_ALL_VARIANTS=ON --&gt; creates many compilation errors and I had to edit, for example:</p> <p>notepad C:\llm\llamacpp\ggml\src\CMakeLists.txt</p> <p>and remove # ggml_add_cpu_backend_variant(alderlake SSE42 AVX F16C FMA AVX2 BMI2 AVX_VNNI)</p> <p>With Ryzen 5950x it's ok.</p> <p>then:</p> <p>set PATH=C:\Program Files\AMD\ROCm\6.4\bin;%PATH%</p> <p>llama-server.exe --model &quot;H:\gptmodel\unsloth\MiniMax-M2.7-GGUF\MiniMax-M2.7-UD-Q4_K_S-00001-of-00004.gguf&quot; --ctx-size 91920 --threads 16 --host <a href="http://127.0.0.1">127.0.0.1</a> --no-mmap --jinja --fit on --flash-attn on -sm layer --n-cpu-moe 0 --threads 16 --cache-type-k q8_0 --cache-type-v q8_0 --parallel 1</p> <p>Done. </p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/LegacyRemaster"> /u/LegacyRemaster </a> <br /> <span><a href="https://i.redd.it/mwcq83ldoeyg1.png">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0bkaf/cuda_rocm_simultaneously_with_dggml_backend_dlon/">[comments]</a></span> </td></tr></table>

</details>