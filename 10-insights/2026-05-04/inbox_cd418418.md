---
id: inbox_cd418418
date: 2026-05-04
source_ref: "[[00-inbox/.../inbox_cd418418]]"
title: "Mistral-Medium-3.5-128B-Q3_K_M on 3x3090 (72GB VRAM)"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t32ps4/mistralmedium35128bq3_k_m_on_3x3090_72gb_vram/
source: reddit-localllama
published_at: 2026-05-04T00:46:26+00:00
fetched_at: 2026-05-04T14:25:08.692047+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "使用者展示 Mistral-Medium-3.5-128B-Q3_K_M 量化版本在 3 張 RTX 3090（共 72GB VRAM）配置上的推理基準，涵蓋 Python 代碼生成、SVG 圖形生成及 HTML 結構化輸出等多個應用場景的性能表現。（具體延遲數值依賴附帶圖表，但驗證了該硬體配置下該模型可穩定運行。）"
key_points:
  - "Mistral-Medium-3.5-128B-Q3_K_M 在 72GB VRAM（3x3090）上可穩定推理多種輸出格式"
  - "應用場景覆蓋 Python 代碼、SVG、HTML 等結構化輸出，驗證了模型的代碼生成與標記化能力"
  - "Q3_K_M 量化策略在該硬體配置下達到可用性能——量化壓縮與推理速度的平衡點"
tags: [mistral, benchmark, 3x3090, quantization-q3]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: data-point
deep_dive_candidate: false
deep_dive_approved: false
---

## Mistral-Medium-3.5-128B-Q3_K_M on 3x3090 (72GB VRAM)

使用者展示 Mistral-Medium-3.5-128B-Q3_K_M 量化版本在 3 張 RTX 3090（共 72GB VRAM）配置上的推理基準，涵蓋 Python 代碼生成、SVG 圖形生成及 HTML 結構化輸出等多個應用場景的性能表現。（具體延遲數值依賴附帶圖表，但驗證了該硬體配置下該模型可穩定運行。）

### 重點
- Mistral-Medium-3.5-128B-Q3_K_M 在 72GB VRAM（3x3090）上可穩定推理多種輸出格式
- 應用場景覆蓋 Python 代碼、SVG、HTML 等結構化輸出，驗證了模型的代碼生成與標記化能力
- Q3_K_M 量化策略在該硬體配置下達到可用性能——量化壓縮與推理速度的平衡點

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t32ps4/mistralmedium35128bq3_k_m_on_3x3090_72gb_vram/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# Mistral-Medium-3.5-128B-Q3_K_M on 3x3090 (72GB VRAM)

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t32ps4/mistralmedium35128bq3_k_m_on_3x3090_72gb_vram/"> <img alt="Mistral-Medium-3.5-128B-Q3_K_M on 3x3090 (72GB VRAM)" src="https://preview.redd.it/3blnqya7o0zg1.png?width=140&amp;height=101&amp;auto=webp&amp;s=8eded90559f5e7a6f9655efbda8b8d3961d57bcd" title="Mistral-Medium-3.5-128B-Q3_K_M on 3x3090 (72GB VRAM)" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>Here is the actual speed of Mistral Medium Q3 running locally on 3x3090</p> <p>first some Python</p> <p><a href="https://preview.redd.it/3blnqya7o0zg1.png?width=1670&amp;format=png&amp;auto=webp&amp;s=bab477f9889c16558044ccebb22e3ebfb6a56118">https://preview.redd.it/3blnqya7o0zg1.png?width=1670&amp;format=png&amp;auto=webp&amp;s=bab477f9889c16558044ccebb22e3ebfb6a56118</a></p> <p><a href="https://preview.redd.it/76a3j6u7o0zg1.png?width=1620&amp;format=png&amp;auto=webp&amp;s=e302a90ae32a7d01959dfee5f7a921dc73ef20b5">https://preview.redd.it/76a3j6u7o0zg1.png?width=1620&amp;format=png&amp;auto=webp&amp;s=e302a90ae32a7d01959dfee5f7a921dc73ef20b5</a></p> <p><a href="https://preview.redd.it/xmd5tzj8o0zg1.png?width=1276&amp;format=png&amp;auto=webp&amp;s=45bc1d77391da81049b6f026dcf6a4af40dc9ec3">https://preview.redd.it/xmd5tzj8o0zg1.png?width=1276&amp;format=png&amp;auto=webp&amp;s=45bc1d77391da81049b6f026dcf6a4af40dc9ec3</a></p> <p>then svg</p> <p><a href="https://preview.redd.it/8q5am5alo0zg1.png?width=1594&amp;format=png&amp;auto=webp&amp;s=a7feeb832c17481526838e8488f4be3069f56443">https://preview.redd.it/8q5am5alo0zg1.png?width=1594&amp;format=png&amp;auto=webp&amp;s=a7feeb832c17481526838e8488f4be3069f56443</a></p> <p><a href="https://preview.redd.it/u4mbv1klo0zg1.png?width=1600&amp;format=png&amp;auto=webp&amp;s=7c83a3437c67ebefe1b0339861f05b9d67c6f030">https://preview.redd.it/u4mbv1klo0zg1.png?width=1600&amp;format=png&amp;auto=webp&amp;s=7c83a3437c67ebefe1b0339861f05b9d67c6f030</a></p> <p><a href="https://preview.redd.it/e8vw83rlo0zg1.png?width=782&amp;format=png&amp;auto=webp&amp;s=fadb4f04bba756056d38049c465d0f7a4323b66d">https://preview.redd.it/e8vw83rlo0zg1.png?width=782&amp;format=png&amp;auto=webp&amp;s=fadb4f04bba756056d38049c465d0f7a4323b66d</a></p> <p>then html</p> <p><a href="https://preview.redd.it/zs9c36xbp0zg1.png?width=1626&amp;format=png&amp;auto=webp&amp;s=428cb84d3158e4285eb4f1d47283646e876f55be">https://preview.redd.it/zs9c36xbp0zg1.png?width=1626&amp;format=png&amp;auto=webp&amp;s=428cb84d3158e4285eb4f1d47283646e876f55be</a></p> <p><a href="https://preview.redd.it/6dw74a5cp0zg1.png?width=1540&amp;format=png&amp;auto=webp&amp;s=cc5af763d980329c0d98064e4f53265cfdf9ec2f">https://preview.redd.it/6dw74a5cp0zg1.png?width=1540&amp;format=png&amp;auto=webp&amp;s=cc5af763d980329c0d98064e4f53265cfdf9ec2f</a></p> <p><a href="https://preview.redd.it/4s3zccecp0zg1.png?width=3796&amp;format=png&amp;auto=webp&amp;s=6defbc181dcbee1fe4523559792e1642aaf504f8">https://preview.redd.it/4s3zccecp0zg1.png?width=3796&amp;format=png&amp;auto=webp&amp;s=6defbc181dcbee1fe4523559792e1642aaf504f8</a></p> <p><a href="https://preview.redd.it/30n07tlcp0zg1.png?width=3782&amp;format=png&amp;auto=webp&amp;s=4ae343f915f4f70e48bc17add7ff856e1af5ceab">https://preview.redd.it/30n07tlcp0zg1.png?width=3782&amp;format=png&amp;auto=webp&amp;s=4ae343f915f4f70e48bc17add7ff856e1af5ceab</a></p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/jacek2023"> /u/jacek2023 </a> <br /> <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t32ps4/mistralmedium35128bq3_k_m_on_3x3090_72gb_vram/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t32ps4/mistralmedium35128bq3_k_m_on_3x3090_72gb_vram/">[comments]</a></span> </td></tr></table>

</details>