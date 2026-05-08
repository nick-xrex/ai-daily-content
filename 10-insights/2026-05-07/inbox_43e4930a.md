---
id: inbox_43e4930a
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-localllama-extracted-mtp-tensor-ggufs-smaller-donor-4747]]"
title: "Extracted MTP tensor GGUFs - smaller donor models for grafting."
url: https://www.reddit.com/r/LocalLLaMA/comments/1t6r1ny/extracted_mtp_tensor_ggufs_smaller_donor_models/
source: reddit-localllama
published_at: 2026-05-07T23:28:41+00:00
fetched_at: 2026-05-08T08:07:35.922321+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "開發者使用 Gemma 製作工具抽取 MTP tensor，製作了精簡版 GGUF 檔案，使下載尺寸從原始 38GB / 29GB 大幅縮至 900MB (35A3B) 和 450MB (27B)，完全相容於現有 MTP 轉換指令碼。轉換結果與原始模型一致（SHA256 驗證），但作者強調 MTP 實現尚未定案，模型可能隨時變更或過時。此工具特別適合頻寬或儲存受限的使用者快速取得必要 tensor。"
key_points:
  - "精簡 GGUF 檔案將下載尺寸縮減至 2.4% (900MB vs 38GB) 與 1.6% (450MB vs 29GB)，保持轉換結果完全相同"
  - "工具相容現有 MTP grafting 指令碼，無需修改下游流程"
  - "免責聲明：MTP 實現尚未最終定案，模型可能隨時更新而失效"
tags: [mtp, gguf, tensor-extraction, open-source, bandwidth-optimization]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## Extracted MTP tensor GGUFs - smaller donor models for grafting.

開發者使用 Gemma 製作工具抽取 MTP tensor，製作了精簡版 GGUF 檔案，使下載尺寸從原始 38GB / 29GB 大幅縮至 900MB (35A3B) 和 450MB (27B)，完全相容於現有 MTP 轉換指令碼。轉換結果與原始模型一致（SHA256 驗證），但作者強調 MTP 實現尚未定案，模型可能隨時變更或過時。此工具特別適合頻寬或儲存受限的使用者快速取得必要 tensor。

### 重點
- 精簡 GGUF 檔案將下載尺寸縮減至 2.4% (900MB vs 38GB) 與 1.6% (450MB vs 29GB)，保持轉換結果完全相同
- 工具相容現有 MTP grafting 指令碼，無需修改下游流程
- 免責聲明：MTP 實現尚未最終定案，模型可能隨時更新而失效

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t6r1ny/extracted_mtp_tensor_ggufs_smaller_donor_models/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

The script to graft MTP tensors requires a full GGUF model file. I felt that was a bit hefty, so I asked local Gemma to write something to just extract what's required. The results are two faux GGUFs weighing in at just 900MB ( 35A3B ) and 450MB ( 27B ), containing only the tensors and fully compatible with the script. A lot quicker to download compared to the original 38GB and 29GB models for those who just want to convert their existing library or save some bandwidth. Testing was done using SHA256 hashes, comparing the models made with these mini-GGUFs to those using the full models (identical results), along with some brief chats. Credits: am17an for the original GGUFs, and buzz for the original script. Disclaimers: The MTP implementation isn't finalized. These models might break or become obsolete at any time. Do not delete the original models in case there are updates to the conversion process. Testing was only done on the two models I use myself; other variants might not work well/at all. Also, 100% clueless vibecoding with a Q4_1 model. &#32; submitted by &#32; /u/AzerbaijanNyan [link] &#32; [comments]

</details>