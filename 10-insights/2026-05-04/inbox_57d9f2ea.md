---
id: inbox_57d9f2ea
date: 2026-05-04
source_ref: "[[00-inbox/2026-05-04/0819-reddit-localllama-do-cheap-32gb-v100s-still-make-sense-for-1b95]]"
title: "Do cheap 32GB V100s still make sense for homelab AI?"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t3oc0t/do_cheap_32gb_v100s_still_make_sense_for_homelab/
source: reddit-localllama
published_at: 2026-05-04T17:22:56+00:00
fetched_at: 2026-05-05T08:42:49.909551+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "社群成員提問：在 2026 年購買便宜二手 Tesla V100 32GB GPU 是否仍具成本效益。提問者已擁有 RTX 5060 Ti 16GB 和 5070 Ti 兩張現代 GPU。購買 V100 的主要動機是利用其充足的 32GB VRAM 來應對大型量化模型和長上下文推理實驗。V100 存在老化、高功耗和軟體支援不足等劣勢。但其 32GB VRAM 相比新卡更具成本優勢。提問涉及硬體選擇的經典權衡問題，但未獲社群定論性答案。"
key_points:
  - "提問場景：已有 RTX 5060 Ti 16GB + 5070 Ti，考慮添加 V100 32GB 以擴展 VRAM"
  - "用例：本地 LLM 實驗、大型量化模型運行、長上下文推理、跨卡卸載"
  - "權衡要素：V100 老化/功耗劣勢 vs. 32GB VRAM 成本優勢"
tags: [v100-gpu, hardware-economics, vram-capacity, homelab-ai, cost-analysis]
topics: []
importance: 1
novelty: 1
insight_quality: 1
insight_type: none
deep_dive_candidate: false
deep_dive_approved: false
---

## Do cheap 32GB V100s still make sense for homelab AI?

社群成員提問：在 2026 年購買便宜二手 Tesla V100 32GB GPU 是否仍具成本效益。提問者已擁有 RTX 5060 Ti 16GB 和 5070 Ti 兩張現代 GPU。購買 V100 的主要動機是利用其充足的 32GB VRAM 來應對大型量化模型和長上下文推理實驗。V100 存在老化、高功耗和軟體支援不足等劣勢。但其 32GB VRAM 相比新卡更具成本優勢。提問涉及硬體選擇的經典權衡問題，但未獲社群定論性答案。

### 重點
- 提問場景：已有 RTX 5060 Ti 16GB + 5070 Ti，考慮添加 V100 32GB 以擴展 VRAM
- 用例：本地 LLM 實驗、大型量化模型運行、長上下文推理、跨卡卸載
- 權衡要素：V100 老化/功耗劣勢 vs. 32GB VRAM 成本優勢

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t3oc0t/do_cheap_32gb_v100s_still_make_sense_for_homelab/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<!-- SC_OFF --><div class="md"><p>I already have an RTX 5060 Ti 16GB and a 5070 Ti, but I’m wondering whether picking up a couple of Tesla V100 32GB cards could actually make sense as a value proposition specifically for larger local models.</p> <p>I know the V100 is old, power-hungry, and missing newer consumer-card features, and I’m not expecting it to beat modern RTX cards for speed or general efficiency. The appeal is mostly the 32GB VRAM per card, especially if they can be found cheap enough.</p> <p>Use case would be local LLM experimentation: running larger quantized models, testing longer context, maybe splitting/offloading across cards where supported. I already have newer RTX hardware for faster smaller models and image generation, so this would mainly be about getting more VRAM for less money.</p> <p>Is there a point where 32GB V100s still make sense in 2026 for homelab AI, or is the age/platform/power/software support enough of a downside that I’d be better off putting the money toward a newer single GPU?</p> <p>Interested in real-world experiences, especially from people who have run V100s alongside newer RTX cards.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/SKX007J1"> /u/SKX007J1 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3oc0t/do_cheap_32gb_v100s_still_make_sense_for_homelab/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t3oc0t/do_cheap_32gb_v100s_still_make_sense_for_homelab/">[comments]</a></span>

</details>