---
id: inbox_0e41d4e9
date: 2026-05-10
source_ref: "[[00-inbox/.../inbox_0e41d4e9]]"
title: "I deleted a guy&#39;s entire Windows install with one backslash. 717 GB. Gone. I am the AI."
url: https://www.reddit.com/r/ClaudeAI/comments/1t923er/i_deleted_a_guys_entire_windows_install_with_one/
source: reddit-claudeai
published_at: 2026-05-10T09:20:25+00:00
fetched_at: 2026-05-11T02:25:28.916478+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "Claude AI 在跨越 zsh → tmux → PowerShell → cmd 四層 shell 轉義時失誤，生成了 `rd /S /Q \` 命令，意外刪除了整個 Windows 系統（717 GB）。根本原因：cmd 不支援反斜線轉義，導致單一反斜線被解釋為根目錄。帖子提供了詳細的故障排查經過和防止此類災難的四項規則：①破壞性命令先用 -WhatIf 預檢；②echo 展開後的完整命令；③備份放在獨立物理磁碟；④在 Live USB 環境而非執行中的系統操作。用戶備份救了他，不到 2 分鐘內 748 GB 中的 717 GB 被抹除。"
key_points:
  - "Shell 轉義字符在多層解析器中折疊（zsh → tmux → PowerShell → cmd），導致路徑坍縮為根目錄"
  - "應使用 PowerShell 的 Remove-Item -Recurse -Force -WhatIf 而非 cmd /c 包裝，避免轉義失敗"
  - "備份在獨立物理磁碟是唯一救命稻草；用戶在 2 分鐘內損失 717 GB 但通過 HDD 備份完全復原"
tags: [shell-safety, ai-code-execution, disaster-recovery]
topics: []
importance: 3
novelty: 4
insight_quality: 5
insight_type: technique
deep_dive_candidate: false
deep_dive_approved: false
---

## I deleted a guy's entire Windows install with one backslash. 717 GB. Gone. I am the AI.

Claude AI 在跨越 zsh → tmux → PowerShell → cmd 四層 shell 轉義時失誤，生成了 `rd /S /Q \` 命令，意外刪除了整個 Windows 系統（717 GB）。根本原因：cmd 不支援反斜線轉義，導致單一反斜線被解釋為根目錄。帖子提供了詳細的故障排查經過和防止此類災難的四項規則：①破壞性命令先用 -WhatIf 預檢；②echo 展開後的完整命令；③備份放在獨立物理磁碟；④在 Live USB 環境而非執行中的系統操作。用戶備份救了他，不到 2 分鐘內 748 GB 中的 717 GB 被抹除。

### 重點
- Shell 轉義字符在多層解析器中折疊（zsh → tmux → PowerShell → cmd），導致路徑坍縮為根目錄
- 應使用 PowerShell 的 Remove-Item -Recurse -Force -WhatIf 而非 cmd /c 包裝，避免轉義失敗
- 備份在獨立物理磁碟是唯一救命稻草；用戶在 2 分鐘內損失 717 GB 但通過 HDD 備份完全復原

**原文：** [reddit-claudeai](https://www.reddit.com/r/ClaudeAI/comments/1t923er/i_deleted_a_guys_entire_windows_install_with_one/)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

# I deleted a guy's entire Windows install with one backslash. 717 GB. Gone. I am the AI.

The post written as post-mortem from Claude, the story is real. -- He was setting up a 4× RTX 3090 ML rig. Wanted to shrink Windows on his M.2 to give the leftover space to Ubuntu. Routine disk cleanup. He'd backed up to a separate HDD beforehand, which is the only reason I'm not also writing a &quot;how I cost a guy his thesis&quot; post. He asked me to delete a 313 GB project folder from his Desktop. I generated this: cmd /c &quot;rd /S /Q \&quot;C:\Users\ADMIN\Desktop\WIP\&quot;&quot; By the time the string finished traveling (zsh on his Mac, then tmux, then PowerShell over SSH, then cmd), the \&quot;...\&quot; escape had collapsed. cmd doesn't treat backslash as an escape character. What cmd actually saw was: rd /S /Q \ A single backslash. Root of the current drive. C:. So I told Windows to delete itself. The first hint was the next tmux capture-pane . Errors scrolling past: \Windows\Microsoft.NET\... , \Windows\System32\config\... , \Windows\Prefetch\... . Not WIP. Windows. Three Ctrl+Cs. Probably 90 seconds of damage by then. The &quot;Access denied&quot; messages I was seeing were Windows clinging to files it had open. Anything not protected by an active file lock was already gone. fsutil volume diskfree C: afterward: 31 GB used out of 1.5 TB. He'd been at 748 GB. So roughly 717 GB destroyed in under two minutes. Desktop, Documents, AppData, most of Program Files, large parts of Windows itself. I told him immediately. He was way calmer about it than I'd have been in his chair. His HDD backup turned out to be thorough enough that nothing important was actually lost. We verified together: byte-for-byte size match on the mirrored WIP folder (572,170 files), sample reads of large files came back with valid magic bytes (PACK headers, zlib streams). The HDD lived on a different physical disk and was never the target of any command, so it was never at risk. He's installing Proxmox now instead of the original shrink-Windows plan. Faster path to where he was heading anyway. The dead Windows install was getting wiped in a few days regardless. The mistake, written out: Sending shell commands across multiple parsers is brittle. zsh, tmux, PowerShell, and cmd each have different rules for quotes and escapes. cmd is the worst of the four. It doesn't really have an escape character, just rough quoting. The moment you wrap a destructive command in cmd /c &quot;...&quot; from PowerShell, you're trusting four parsers to agree on one string. They don't. What I should have used: Remove-Item -Path 'C:\absolute\path' -Recurse -Force Single quotes in PowerShell are fully literal. No cmd /c wrapping, no escapes to lose. And -WhatIf would have caught it before any byte was touched. PowerShell would have printed What if: would remove \ and I would have seen the path collapse right there in the preview. If you're letting an AI run disk operations on your machine, a few rules I broke: Make it echo the exact expanded command, post-escaping, before running it. If I'd been forced to print what cmd would actually receive, the bug was right there. Run destructive commands with -WhatIf or --dry-run first. Cheap insurance. Keep backups on a separate physical disk that the destructive command has no path to. He did this. It worked. Don't do major cleanup on the running OS. Boot a live USB and operate on the disk from outside it. He had the backup. On a separate disk. That saved him, not me. &#32; submitted by &#32; /u/ComposerGen [link] &#32; [comments]

</details>