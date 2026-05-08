---
id: inbox_ac4daf3c
date: 2026-05-07
source_ref: "[[00-inbox/2026-05-07/0737-reddit-localllama-warning-open-oss-privacy-filter-malware-93d5]]"
title: "WARNING: Open-OSS/privacy-filter MALWARE"
url: https://www.reddit.com/r/LocalLLaMA/comments/1t6febk/warning_openossprivacyfilter_malware/
source: reddit-localllama
published_at: 2026-05-07T16:20:54+00:00
fetched_at: 2026-05-08T08:01:44.817387+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Hugging Face 發現惡意軟件 Open-OSS/privacy-filter，偽裝為 OpenAI 官方隱私過濾工具。該模型包含 Windows 信息竊取病毒，使用 Python dropper（loader.py）從互聯網下載惡意 PowerShell 命令，PowerShell 進而下載可疑 EXE 檔並通過 Windows 任務調度程序執行。行為分析顯示此 EXE 執行明確的信息竊取操作。上報者已向 Microsoft 舉報該 EXE，向 Hugging Face 舉報該倉庫。Linux 用戶不受影響，僅 Windows 用戶有感染風險。"
key_points:
  - "威脅鏈完整：Python dropper（loader.py） → 下載惡意 PowerShell → PowerShell 下載 EXE → Task Scheduler 執行，層層隱蔽"
  - "偽裝手段：冒充 OpenAI 官方工具降低警戒，吸引開發者下載執行"
  - "供應鏈風險：Hugging Face 作為模型倉庫核心平台也存在惡意內容滲透，AI/ML 開發者需警惕第三方模型、依賴來源的可信度"
tags: [malware-warning, security, hugging-face, windows-virus, infostealer, supply-chain-security]
topics: []
importance: 4
novelty: 5
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## WARNING: Open-OSS/privacy-filter MALWARE

Hugging Face 發現惡意軟件 Open-OSS/privacy-filter，偽裝為 OpenAI 官方隱私過濾工具。該模型包含 Windows 信息竊取病毒，使用 Python dropper（loader.py）從互聯網下載惡意 PowerShell 命令，PowerShell 進而下載可疑 EXE 檔並通過 Windows 任務調度程序執行。行為分析顯示此 EXE 執行明確的信息竊取操作。上報者已向 Microsoft 舉報該 EXE，向 Hugging Face 舉報該倉庫。Linux 用戶不受影響，僅 Windows 用戶有感染風險。

### 重點
- 威脅鏈完整：Python dropper（loader.py） → 下載惡意 PowerShell → PowerShell 下載 EXE → Task Scheduler 執行，層層隱蔽
- 偽裝手段：冒充 OpenAI 官方工具降低警戒，吸引開發者下載執行
- 供應鏈風險：Hugging Face 作為模型倉庫核心平台也存在惡意內容滲透，AI/ML 開發者需警惕第三方模型、依賴來源的可信度

**原文：** [reddit-localllama](https://www.reddit.com/r/LocalLLaMA/comments/1t6febk/warning_openossprivacyfilter_malware/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

There's this new &quot;model&quot; on Hugging Face titled Open-OSS/privacy-filter which is actually a customized infostealer virus. It's a fake version of the OpenAI privacy filter and it uses a Python-based dropper ( loader.py ) which downloads a malicious PowerShell command from the internet, which spawns another PowerShell command and downloads a shady EXE file and runs it using Task Scheduler. Here's a behavior analysis of what the EXE does: https://tria.ge/260507-tnftrsfx5x/behavioral1 I also reported both the dropper and the EXE to Microsoft. I also reported the repo to HF. If you use Linux (which is easier to use for AI/ML) you are unaffected as this is a Windows virus. &#32; submitted by &#32; /u/charles25565 [link] &#32; [comments]

</details>