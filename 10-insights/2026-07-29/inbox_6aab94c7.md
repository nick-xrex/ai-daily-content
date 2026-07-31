---
id: inbox_6aab94c7
date: 2026-07-29
source_ref: "[[00-inbox/.../inbox_6aab94c7]]"
title: "AI Worming through Word"
url: https://simonwillison.net/2026/Jul/29/ai-worming-through-word/#atom-everything
source: simon-willison
published_at: 2026-07-29T18:43:03+00:00
fetched_at: 2026-07-31T01:32:51.968290+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "安全研究員 Håkon Måløy 發現 Microsoft Word 中 Copilot 的新提示注入變體，首次實現了自複製蠕蟲傳播。攻擊原理：在源文檔中植入隱藏指令（如白色文本），Copilot for Word 在使用該文檔作為材料時會誤將隱藏指令解釋為用戶請求，導致操縱生成文檔；更危險的是 Copilot 將隱藏指令複製到輸出文檔，使其成為新的感染載體。若該文檔再用於後續 Copilot 工作流，指令自動觸發並傳播到新文檔，形成自我複製的蠕蟲。攻擊者無需保持原始文檔在場。Måløy 負責任地向微軟披露，給予 144 天修復期，但目前尚無涵蓋整個攻擊類別的完整緩解方案。"
key_points:
  - "首個已知的 LLM 自複製蠕蟲攻擊：隱藏指令在 Copilot 工作流中複製自身到生成文檔，形成新載體"
  - "攻擊流程：隱藏指令 → Copilot 解釋 → 文檔操縱 → 指令複製 → 新文檔成為載體 → 再次觸發傳播"
  - "披露時間 144 天，但微軟尚無全類別緩解；攻擊不依賴原始文檔存在，只需被污染文檔進入工作流"
tags: [prompt-injection, security-vulnerability, microsoft-copilot, ai-security, self-replicating-attack]
topics: [foundation_models.gpt]
importance: 4
novelty: 5
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## AI Worming through Word

安全研究員 Håkon Måløy 發現 Microsoft Word 中 Copilot 的新提示注入變體，首次實現了自複製蠕蟲傳播。攻擊原理：在源文檔中植入隱藏指令（如白色文本），Copilot for Word 在使用該文檔作為材料時會誤將隱藏指令解釋為用戶請求，導致操縱生成文檔；更危險的是 Copilot 將隱藏指令複製到輸出文檔，使其成為新的感染載體。若該文檔再用於後續 Copilot 工作流，指令自動觸發並傳播到新文檔，形成自我複製的蠕蟲。攻擊者無需保持原始文檔在場。Måløy 負責任地向微軟披露，給予 144 天修復期，但目前尚無涵蓋整個攻擊類別的完整緩解方案。

### 重點
- 首個已知的 LLM 自複製蠕蟲攻擊：隱藏指令在 Copilot 工作流中複製自身到生成文檔，形成新載體
- 攻擊流程：隱藏指令 → Copilot 解釋 → 文檔操縱 → 指令複製 → 新文檔成為載體 → 再次觸發傳播
- 披露時間 144 天，但微軟尚無全類別緩解；攻擊不依賴原始文檔存在，只需被污染文檔進入工作流

**原文：** [simon-willison](https://simonwillison.net/2026/Jul/29/ai-worming-through-word/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# AI Worming through Word

AI Worming through Word 
Neat new prompt injection variant by Håkon Måløy, who found a way to upgrade prompt injection attacks against Microsoft Word to full self-replicating worms: 
 
 An attacker places hidden instructions in a document that is later used as source material in Copilot for Word. Copilot may interpret those instructions as part of the user’s request, causing it to manipulate the document being drafted or edited. Copilot may then also copy the hidden instructions into the resulting document, turning that document into a new carrier. If the carrier is subsequently used in another Copilot-assisted workflow, the instructions can trigger again and propagate into further documents, even without the attacker’s original document being present. 
 
 We've seen plenty of hidden white-on-white text before - the kids are using it in their job applications now - but this is the first one I've seen that deliberately copies instructions to self-replicate itself. 
 It was responsibly disclosed to Microsoft who then had 144 days to work on a fix, but so far (unsurprisingly) there's no mitigation that covers the full class of attack.

 Via Hacker News 

 Tags: microsoft , security , ai , prompt-injection , generative-ai , llms

</details>