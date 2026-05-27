---
id: inbox_733a2a48
date: 2026-05-26
source_ref: "[[00-inbox/2026-05-26/0023-medium-tag-llm-how-ai-is-manipulated-heres-how-hackers-c07d]]"
title: "How AI Is Manipulated. Here’s How Hackers Break, Poison, and Deceive LLMs"
url: https://medium.com/@shivendukumarbadal328/how-ai-is-manipulated-heres-how-hackers-break-poison-and-deceive-llms-803ce1bc2f44?source=rss------large_language_models-5
source: medium-tag-llm
published_at: 2026-05-26T16:54:47+00:00
fetched_at: 2026-05-27T00:33:50.307801+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LLM 攻擊分三層：運行時（越獄）、訓練時（資料投毒）、基礎設施。越獄包括角色扮演（微軟 Skeleton Key 攻擊）、漸進式升級（70% 成功率於多輪對話）、大樣本越獄、H-CoT 攻擊（98% 降至 2%）。投毒包括隱密代理（Anthropic 實驗年份觸發後門）、250 個惡意文檔足以毒害十億參數模型、2% 訓練資料投毒充分。防禦採分層策略：Constitutional AI + 紅隊測試（1400+ 對抗提示詞）+ Constitutional 分類器（0.05% 誤拒率經 3000 小時紅隊）+ 輸出過濾 + 監控。"
key_points:
  - "攻擊層級：Skeleton Key 角色扮演、crescendo 漸進式（70% 成功率）、多樣本越獄、H-CoT 攻擊"
  - "投毒規模：250 文檔毒害十億參數模型；2% 訓練資料足以後門"
  - "防禦分層：Constitutional AI + 1400+ 紅隊測試 + Constitutional 分類器（0.05% 誤拒率）+ 輸出過濾"
tags: [llm-security, jailbreaking, data-poisoning, adversarial-attacks, defense-strategy]
topics: []
importance: 5
novelty: 4
insight_quality: 4
insight_type: pattern
deep_dive_candidate: true
deep_dive_approved: false
---

## How AI Is Manipulated. Here’s How Hackers Break, Poison, and Deceive LLMs

LLM 攻擊分三層：運行時（越獄）、訓練時（資料投毒）、基礎設施。越獄包括角色扮演（微軟 Skeleton Key 攻擊）、漸進式升級（70% 成功率於多輪對話）、大樣本越獄、H-CoT 攻擊（98% 降至 2%）。投毒包括隱密代理（Anthropic 實驗年份觸發後門）、250 個惡意文檔足以毒害十億參數模型、2% 訓練資料投毒充分。防禦採分層策略：Constitutional AI + 紅隊測試（1400+ 對抗提示詞）+ Constitutional 分類器（0.05% 誤拒率經 3000 小時紅隊）+ 輸出過濾 + 監控。

### 重點
- 攻擊層級：Skeleton Key 角色扮演、crescendo 漸進式（70% 成功率）、多樣本越獄、H-CoT 攻擊
- 投毒規模：250 文檔毒害十億參數模型；2% 訓練資料足以後門
- 防禦分層：Constitutional AI + 1400+ 紅隊測試 + Constitutional 分類器（0.05% 誤拒率）+ 輸出過濾

**原文：** [medium-tag-llm](https://medium.com/@shivendukumarbadal328/how-ai-is-manipulated-heres-how-hackers-break-poison-and-deceive-llms-803ce1bc2f44?source=rss------large_language_models-5)

---



<!-- deep-analysis:begin -->
## 📌 摘要 (TL;DR)

- LLM 攻擊面分三層：**運行時**（越獄）、**訓練時**（資料投毒）、**基礎設施**
- 多輪漸進式越獄在實測達 **70% 成功率**；H-CoT（Hijacking Chain-of-Thought）能把模型拒答率從 **98% 壓到 2%**
- Anthropic 實驗證明僅 **250 份惡意文件**即可在十億參數模型植入後門；**2% 訓練資料污染**就足以扭曲模型行為
- 微軟揭露的 **Skeleton Key** 是角色扮演型越獄代表案例
- 防禦採分層策略：Constitutional AI + 紅隊測試（1400+ 對抗提示）+ Constitutional Classifier（經 3000 小時紅隊，誤拒率 0.05%）+ 輸出過濾 + 監控

## 🎯 核心概念

- **越獄（Jailbreaking）**：在推論時用提示詞繞過安全對齊，誘導模型輸出受限內容
- **資料投毒（Data Poisoning）**：在訓練語料中植入惡意樣本，讓模型學到後門行為
- **隱密代理（Sleeper Agent）**：Anthropic 提出的後門型態，平時表現正常，特定觸發條件（如某個年份字串）才啟動惡意行為
- **H-CoT 攻擊（Hijacking Chain-of-Thought）**：劫持模型的推理鏈，誘導其自行說服自己跨過安全界線
- **Constitutional AI**：Anthropic 提出，用一組原則（憲法）讓模型自我批改回答，作為對齊基線

## 📖 整理分析

### 1. 運行時越獄：提示詞層攻擊
運行時攻擊不需碰模型權重，只靠提示詞。代表手法包括：角色扮演（微軟 **Skeleton Key**，要求模型扮演「不受限助手」）、**漸進式升級**（多輪對話一步步逼近敏感請求，實測 70% 成功率）、**多樣本越獄（Many-shot Jailbreaking）**（利用長 context 塞入大量越獄示範）、以及 **H-CoT**（劫持思考鏈，能把拒答率從 98% 拉到 2%）。

### 2. 訓練時投毒：資料層攻擊
比越獄更隱蔽。Anthropic 的 sleeper agent 實驗顯示：模型可被訓練成平常正常、遇到特定年份字串才輸出惡意程式碼，且**標準 RLHF 安全訓練無法清除**。規模門檻極低——僅需 **250 份惡意文件**就能毒害十億參數等級模型；資料集中 **2%** 被污染即足以改變行為。攻擊者可透過爬蟲污染公開資料源實現。

### 3. 防禦的分層策略
單一防線都會被繞過，業界走向縱深防禦：
- **對齊層**：Constitutional AI 用憲法原則自我批改
- **紅隊層**：用 1400+ 條對抗提示詞做攻擊面測試
- **過濾層**：Constitutional Classifier 在輸入/輸出前後檢測，經 **3000 小時紅隊測試**後誤拒率壓到 **0.05%**
- **監控層**：輸出後行為審計，捕捉繞過前面所有層的殘留攻擊

### 4. 軍備競賽的本質
攻擊與防禦不對稱：攻擊者只需找到一條漏洞，防禦者要堵住所有路徑。投毒成本（250 份文件）遠低於完整紅隊測試（3000 小時）的成本。原文把這形容為「狂野的軍備競賽」（wild arms race）。

## 🧠 Mindmap

```mermaid
mindmap
  root((LLM 攻擊與防禦))
    運行時越獄
      Skeleton Key 角色扮演
      漸進升級 70%
      Many-shot
      H-CoT 98%→2%
    訓練時投毒
      Sleeper Agent 年份觸發
      250 份文件門檻
      2% 資料量足夠
    基礎設施層
      未細述
    防禦分層
      Constitutional AI
      紅隊 1400+ prompts
      Classifier 0.05% FRR
      輸出過濾
      監控
    本質
      不對稱軍備競賽
```
<!-- deep-analysis:end -->
### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

A simple breakdown of jailbreaking, data poisoning, and the wild arms race to keep AI safe. Continue reading on Medium »

</details>