---
id: inbox_8d5d30d7
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-localllama-final-monster-32x-amd-mi50-32gb-at-9-7-t-48ea]]"
title: "Final Monster: 32x AMD MI50 32GB at 9.7 t/s (TG) &amp; 264 t/s (PP) with Kimi K2.6"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t0b0ie/final_monster_32x_amd_mi50_32gb_at_97_ts_tg_264/
source: reddit-localllama
published_at: 2026-04-30T22:24:07+00:00
fetched_at: 2026-05-01T13:31:34.633296+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "極端規模推理實驗報告：32 塊 AMD MI50 32GB GPU（分 2 節點各 16 塊，10G 以太網連接）運行 Kimi K2.6 int4 模型。實現文本生成 9.7 tok/s、預填充 263 tok/s，功耗為 idle 640W、peak 4800W。實驗者坦白該配置「不值得」除非擁有太陽能或免費電力。受限於 PCIe Gen3/Gen4 帶寬不足（實際 3.5GB/s 而非設計 7GB/s），認為升級至滿 PCIe 帶寬可達 600–1000 預填充和 9–12 生成 TPS，但投入回報率仍低。"
key_points:
  - "Kimi K2.6 int4 @ 32×MI50：9.7 tok/s (輸出 136 token) / 263 tok/s (預填充 14564 token)，peak 功耗 4800W"
  - "成本負效益：PCIe 帶寬瓶頸 (3.5GB/s 實際 vs 7GB/s 設計) 限制吞吐；作者結論『非免費電力不推薦』"
  - "改進空間有限：完整 PCIe + vLLM 優化可望預填充達 600–1000 tok/s，但仍不足以收回投資"
tags: [amd-gpu, large-scale-inference, kimi-k2.6, cost-analysis]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Final Monster: 32x AMD MI50 32GB at 9.7 t/s (TG) & 264 t/s (PP) with Kimi K2.6

極端規模推理實驗報告：32 塊 AMD MI50 32GB GPU（分 2 節點各 16 塊，10G 以太網連接）運行 Kimi K2.6 int4 模型。實現文本生成 9.7 tok/s、預填充 263 tok/s，功耗為 idle 640W、peak 4800W。實驗者坦白該配置「不值得」除非擁有太陽能或免費電力。受限於 PCIe Gen3/Gen4 帶寬不足（實際 3.5GB/s 而非設計 7GB/s），認為升級至滿 PCIe 帶寬可達 600–1000 預填充和 9–12 生成 TPS，但投入回報率仍低。

### 重點
- Kimi K2.6 int4 @ 32×MI50：9.7 tok/s (輸出 136 token) / 263 tok/s (預填充 14564 token)，peak 功耗 4800W
- 成本負效益：PCIe 帶寬瓶頸 (3.5GB/s 實際 vs 7GB/s 設計) 限制吞吐；作者結論『非免費電力不推薦』
- 改進空間有限：完整 PCIe + vLLM 優化可望預填充達 600–1000 tok/s，但仍不足以收回投資

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t0b0ie/final_monster_32x_amd_mi50_32gb_at_97_ts_tg_264/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0b0ie/final_monster_32x_amd_mi50_32gb_at_97_ts_tg_264/"> <img alt="Final Monster: 32x AMD MI50 32GB at 9.7 t/s (TG) &amp; 264 t/s (PP) with Kimi K2.6" src="https://external-preview.redd.it/Ds9LZV4Mk3ugH_EO_8DbA7Mm5PPdu5oRvhOQfDc9wh4.png?width=140&amp;height=70&amp;auto=webp&amp;s=39e99c290e6d048107c288b21026c08ab06dccbc" title="Final Monster: 32x AMD MI50 32GB at 9.7 t/s (TG) &amp; 264 t/s (PP) with Kimi K2.6" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p><a href="https://preview.redd.it/8186petvjeyg1.jpg?width=600&amp;format=pjpg&amp;auto=webp&amp;s=ad67f085d0a1df0a207f4750ed688958378cf178">32 MI50 32GB setup</a></p> <p><strong>moonshotai/Kimi-K2.6 int4 @ 9.7 tok/s</strong> (output of 136 tok) and <strong>263 tok/s</strong> (input of 14564 tok) on <strong>vllm-gfx906-mobydick</strong></p> <p><strong>Github link of vllm fork</strong>: <a href="https://github.com/ai-infos/vllm-gfx906-mobydick">https://github.com/ai-infos/vllm-gfx906-mobydick</a></p> <p><strong>Power draw</strong>: ~640W (idle) / ~4800W (peak inference)</p> <p><strong>Is it worth ? No, unless you’ve got solar panels or free energy…</strong></p> <p><strong>Setup details:</strong><br /> <strong>That’s just 2 nodes of 16 GPU that i plugged together with 10G cable ethernet. You can find details on 1 node of 16 GPU there:</strong></p> <p><a href="https://github.com/ai-infos/guidances-setup-16-mi50-deepseek-v32">https://github.com/ai-infos/guidances-setup-16-mi50-deepseek-v32</a></p> <p><strong>cmd i run:</strong> </p> <pre><code>NCCL_SOCKET_IFNAME=eno1 GLOO_SOCKET_IFNAME=eno1 PYTHONUNBUFFERED=1 VLLM_EXECUTE_MODEL_TIMEOUT_SECONDS=1200 OMP_NUM_THREADS=4 \ FLASH_ATTENTION_TRITON_AMD_REF=&quot;TRUE&quot; FLASH_ATTENTION_TRITON_AMD_ENABLE=&quot;TRUE&quot; VLLM_LOGGING_LEVEL=DEBUG \ python3 -m torch.distributed.run --nnodes=2 --node_rank=0 --nproc_per_node=16 --master_addr=10.0.0.8 --master_port=29500 /llm/models/shared/openai_server_kimi.py 2&gt;&amp;1 | tee log.txt NCCL_SOCKET_IFNAME=eno1 GLOO_SOCKET_IFNAME=eno1 PYTHONUNBUFFERED=1 VLLM_EXECUTE_MODEL_TIMEOUT_SECONDS=1200 OMP_NUM_THREADS=4 \ FLASH_ATTENTION_TRITON_AMD_REF=&quot;TRUE&quot; FLASH_ATTENTION_TRITON_AMD_ENABLE=&quot;TRUE&quot; VLLM_LOGGING_LEVEL=DEBUG \ python3 -m torch.distributed.run --nnodes=2 --node_rank=1 --nproc_per_node=16 --master_addr=10.0.0.8 --master_port=29500 /llm/models/shared/openai_server_kimi.py 2&gt;&amp;1 | tee log.txt </code></pre> <p>the script &quot;openai_server_kimi.py&quot; is just based on official vllm example with torchrun (modified to support openai api..and not really optimized... the vllm default command that included torchrun didn't work for me, need more investigation to debug...), i can share it on github too if there's any interest (but need to be more optimized)</p> <p><strong>ps</strong>: I still didn’t do a full guidance setup for this because i’m quite not satisfied of the perf… First, this setup run at pcie gen3 x8 and pcie gen4 x4 , all are supposed to be at 7GB/s but got one at 3.5GB/s (due to instability of risers…) Theoretically, if i manage to do a new setup with max pcie bandwidth : 28GB/s (if x16) or 14GB/s (if x8) in TP8 PP4 (or TP4 PP8) and with optimized vllm software stack, I believe we can jum to 600-1000 PP and 9-12 TG (without mtp)… and now this setup might be interesting if we compare to hybrid setup (ddr5-rtx 6000 pro, etc) but i think i’m done with all of it and I might just enjoy small models, much faster on smaller setups.</p> <p><strong>Feel free to ask any questions and/or share any comments.</strong></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/ai-infos"> /u/ai-infos </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0b0ie/final_monster_32x_amd_mi50_32gb_at_97_ts_tg_264/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t0b0ie/final_monster_32x_amd_mi50_32gb_at_97_ts_tg_264/">[comments]</a></span> </td></tr></table>

</details>