---
id: inbox_627f804e
date: 2026-04-30
source_ref: "[[00-inbox/2026-04-30/1257-reddit-localllama-my-calculator-is-a-transformer-a25d]]"
title: "My calculator is a transformer"
url: https://www.reddit.com/r/LocalLLaMA/comments/1szy8y8/my_calculator_is_a_transformer/
source: reddit-localllama
published_at: 2026-04-30T14:49:18+00:00
fetched_at: 2026-05-01T13:33:00.718749+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "研究者探索將程序直接「編譯」到 Transformer 權重而非訓練方式，設計了在殘差流中使用「暫存器」、通過注意力權重與 MLP 函數執行 RPN 計算機的系統。雖然最終模型體積達 1.1GB 且實用性有限，但這個過程揭示了對 Transformer 和注意力機制工作原理的全新理解視角。"
key_points:
  - "使用殘差流「暫存器」與注意力權重完全由編譯器計算的設計"
  - "MLP 層非線性邏輯通過訓練蒸餾，未來可能支援直接計算"
  - "最終 RPN 計算機 1.1GB，雖不實用但啟發對 Transformer 工作原理的新理解"
tags: [transformer-compilation, attention-mechanism, program-synthesis]
topics: []
importance: 2
novelty: 4
insight_quality: 4
insight_type: framework
deep_dive_candidate: true
deep_dive_approved: false
---

## My calculator is a transformer

研究者探索將程序直接「編譯」到 Transformer 權重而非訓練方式，設計了在殘差流中使用「暫存器」、通過注意力權重與 MLP 函數執行 RPN 計算機的系統。雖然最終模型體積達 1.1GB 且實用性有限，但這個過程揭示了對 Transformer 和注意力機制工作原理的全新理解視角。

### 重點
- 使用殘差流「暫存器」與注意力權重完全由編譯器計算的設計
- MLP 層非線性邏輯通過訓練蒸餾，未來可能支援直接計算
- 最終 RPN 計算機 1.1GB，雖不實用但啟發對 Transformer 工作原理的新理解

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1szy8y8/my_calculator_is_a_transformer/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1szy8y8/my_calculator_is_a_transformer/"> <img alt="My calculator is a transformer" src="https://external-preview.redd.it/cz-g2UIhppSCNNKYkic1dzzT9FSuWIa85Ac7PKfwOh0.png?width=320&amp;crop=smart&amp;auto=webp&amp;s=a1c6d814e70eb89928a34029920e24db4a0bae4b" title="My calculator is a transformer" /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>I got interested in seeing whether I could &quot;compile&quot; a program into transformer weights, instead of training. I've been working on it for a couple of months now but finally decided to just stop and write it up, so this is a bit of a long post but maybe some of you will find it interesting.</p> <p>Basically I define the residual stream as a set of &quot;registers&quot; and generate the attention weights and MLP functions that execute an RPN interpreter (e.g. <code>2 3 + 2 *</code> should produce <code>10</code>.)</p> <p>For now I settled on distilling the non-linear logic into the MLPs by training, but the attention weights are fully calculated by the compiler. I think it could be possible to calculate the MLP weights eventually too but it probably needs more of an AST behind it.</p> <p>In a way it's a sort of useless exercise (who really needs an RPN interpreter that clocks in at 1.1 GB) but see the last bit for some thoughts about how this might have some application. I did learn to think of transformers and attention a bit differently after working on this, so I hope it's interesting to some people out there.</p> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/radarsat1"> /u/radarsat1 </a> <br /> <span><a href="https://sinclairs.gitlab.io/blog/my-calculator-is-a-transformer/">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1szy8y8/my_calculator_is_a_transformer/">[comments]</a></span> </td></tr></table>

</details>