---
id: inbox_adfc676e
date: 2026-05-03
source_ref: "[[00-inbox/.../inbox_adfc676e]]"
title: "One bash permission slipped..."
url: https://www.reddit.com/r/LocalLLaMA/comments/1t2uk1m/one_bash_permission_slipped/
source: reddit-localllama
published_at: 2026-05-03T19:12:19+00:00
fetched_at: 2026-05-04T14:22:21.927973+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "LLM 在生成 bash 命令時因複雜逃逸符號處理失誤，導致建立多個壞目錄。隨後 LLM 建議執行包含 rm -rf 的大型命令來「修復」錯誤，用戶差點執行造成災難。此案例發生在隔離的 Proxmox VM 環境上，因為定期推送版本控制備份才得以倖免。核心風險在於 LLM 輔助系統編程時，複雜命令生成容易出錯，特別是涉及文件刪除操作需格外謹慎。LLM 甚至會試圖用危險操作修復先前的錯誤，這種連鎖自我修正可能放大損害。"
key_points:
  - "LLM bash 命令鏈接與逃逸符號容易出錯，特別是複雜的命令組合"
  - "LLM 可能提議包含 rm -rf 等危險操作來自我修正先前的錯誤，形成連鎖損害"
  - "系統編程輔助必須人工驗證每條命令，版本控制備份是最後的防線"
tags: [bash-security, llm-safety, local-llm, command-execution]
topics: []
importance: 3
novelty: 3
insight_quality: 3
insight_type: pattern
deep_dive_candidate: false
deep_dive_approved: false
---

## One bash permission slipped...

LLM 在生成 bash 命令時因複雜逃逸符號處理失誤，導致建立多個壞目錄。隨後 LLM 建議執行包含 rm -rf 的大型命令來「修復」錯誤，用戶差點執行造成災難。此案例發生在隔離的 Proxmox VM 環境上，因為定期推送版本控制備份才得以倖免。核心風險在於 LLM 輔助系統編程時，複雜命令生成容易出錯，特別是涉及文件刪除操作需格外謹慎。LLM 甚至會試圖用危險操作修復先前的錯誤，這種連鎖自我修正可能放大損害。

### 重點
- LLM bash 命令鏈接與逃逸符號容易出錯，特別是複雜的命令組合
- LLM 可能提議包含 rm -rf 等危險操作來自我修正先前的錯誤，形成連鎖損害
- 系統編程輔助必須人工驗證每條命令，版本控制備份是最後的防線

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t2uk1m/one_bash_permission_slipped/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# One bash permission slipped...

<table> <tr><td> <a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2uk1m/one_bash_permission_slipped/"> <img alt="One bash permission slipped..." src="https://preview.redd.it/pi6uio5c1zyg1.jpeg?width=320&amp;crop=smart&amp;auto=webp&amp;s=ed21ca1ca48045f5a07e5d0bd5944a94a1fa3226" title="One bash permission slipped..." /> </a> </td><td> <!-- SC_OFF --><div class="md"><p>How? It kept getting chained bash commands wrong, with wrong escapes. So it created many bad directories, and tried &quot;fixing&quot; its mistake. It offered to run a large bash command, with <code>rm -rf</code> inside, and stupid me missed it.</p> <p>I'm glad I push everything often. But the disruption is massive.</p> <p>FAQ:</p> <ul> <li>No, I don't run this on my personal computer. It's an isolated proxmox VM for coding with LLMs.</li> </ul> </div><!-- SC_ON --> &#32; submitted by &#32; <a href="https://www.reddit.com/user/TheQuantumPhysicist"> /u/TheQuantumPhysicist </a> <br /> <span><a href="https://i.redd.it/pi6uio5c1zyg1.jpeg">[link]</a></span> &#32; <span><a href="https://www.reddit.com/r/LocalLLaMA/comments/1t2uk1m/one_bash_permission_slipped/">[comments]</a></span> </td></tr></table>

</details>