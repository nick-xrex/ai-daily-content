---
id: inbox_a767e42f
date: 2026-08-10
source_ref: "[[00-inbox/2026-08-10/2207-gitnexus-releases-rc-414c1a569307f93db1d43770b4c9df1e6e269-6a77]]"
title: "rc/414c1a569307f93db1d43770b4c9df1e6e269eb2: fix(storage): give every registry write its own tmp path (#2888) (#2920)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F414c1a569307f93db1d43770b4c9df1e6e269eb2
source: gitnexus-releases
published_at: 2026-08-10T20:16:42+00:00
fetched_at: 2026-08-11T00:10:17.721136+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 修復一項關鍵的並發 bug，涉及 registry 檔案寫入時的 TOCTOU（Time-Of-Check-Time-Of-Use）race condition。問題根源在於 writeRegistry 使用固定的 ~/.gitnexus/registry.json.tmp 暫存路徑，多個 gitnexus 進程同時啟動時會競爭同一個 inode，導致第二個進程的 rename 覆蓋第一個進程的位元組，第一個進程因找不到暫存檔案（ENOENT）而 crash 並殺死 MCP server。實測 12 進程並發下有 4 個進程 crash。修復統一原子寫入邏輯為 writeFileAtomic 函式，使用隨機後綴暫存路徑、0o600 嚴格權限、原子 rename、失敗時清理，被四個寫入器共用（writeRegistry、writeMetaFile、writeBridgeMeta、writeContractRegistry）。次級改善在 listRegisteredRepos 清理寫入失敗時記錄警告而非拋出例外，提升 MCP 啟動韌性。新增 5 項單元測試和並發驗證，在 24 進程並發測試下將 crash 率從 4/12 降至 0/12。"
key_points:
  - "Registry write race condition：固定暫存路徑導致 inode 競爭 → rename 覆蓋 → ENOENT crash MCP server；實測 12 進程中 4 crash"
  - "修復方案：隨機後綴暫存路徑 + 原子 rename + 0o600 嚴格權限 + 失敗清理，統一為 writeFileAtomic 原始函式；四個寫入器共用"
  - "次級改善：listRegisteredRepos 清理寫入失敗改為 warn；新增 5 項並發單元測試；24 進程測試 crash 率 4/12 → 0/12"
tags: [concurrency, storage, bug-fix, race-condition, atomic-operations]
topics: []
importance: 5
novelty: 3
insight_quality: 5
insight_type: data-point
deep_dive_candidate: true
deep_dive_approved: false
---

## rc/414c1a569307f93db1d43770b4c9df1e6e269eb2: fix(storage): give every registry write its own tmp path (#2888) (#2920)

GitNexus 修復一項關鍵的並發 bug，涉及 registry 檔案寫入時的 TOCTOU（Time-Of-Check-Time-Of-Use）race condition。問題根源在於 writeRegistry 使用固定的 ~/.gitnexus/registry.json.tmp 暫存路徑，多個 gitnexus 進程同時啟動時會競爭同一個 inode，導致第二個進程的 rename 覆蓋第一個進程的位元組，第一個進程因找不到暫存檔案（ENOENT）而 crash 並殺死 MCP server。實測 12 進程並發下有 4 個進程 crash。修復統一原子寫入邏輯為 writeFileAtomic 函式，使用隨機後綴暫存路徑、0o600 嚴格權限、原子 rename、失敗時清理，被四個寫入器共用（writeRegistry、writeMetaFile、writeBridgeMeta、writeContractRegistry）。次級改善在 listRegisteredRepos 清理寫入失敗時記錄警告而非拋出例外，提升 MCP 啟動韌性。新增 5 項單元測試和並發驗證，在 24 進程並發測試下將 crash 率從 4/12 降至 0/12。

### 重點
- Registry write race condition：固定暫存路徑導致 inode 競爭 → rename 覆蓋 → ENOENT crash MCP server；實測 12 進程中 4 crash
- 修復方案：隨機後綴暫存路徑 + 原子 rename + 0o600 嚴格權限 + 失敗清理，統一為 writeFileAtomic 原始函式；四個寫入器共用
- 次級改善：listRegisteredRepos 清理寫入失敗改為 warn；新增 5 項並發單元測試；24 進程測試 crash 率 4/12 → 0/12

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F414c1a569307f93db1d43770b4c9df1e6e269eb2)

---



<!-- deep-analysis:begin -->
## 📌 摘要 (TL;DR)

- GitNexus 修掉一個會讓 MCP server 直接斷線的競態條件（race condition）：`writeRegistry` 把全域 registry 一律經由**固定路徑** `~/.gitnexus/registry.json.tmp` 暫存，而這是機器上每個 gitnexus 進程都會寫的同一個檔案。
- 兩個進程同時啟動時共用同一個 inode：後者的 `writeFile` 蓋掉前者的位元組、後者 `rename` 把該 inode 搬走，前者的 `rename` 找不到來源，拋出 `ENOENT: no such file or directory, rename '/registry.json.tmp' -> '/registry.json'`。
- 這條錯誤落在啟動路徑 `mcpCommand → LocalBackend.init → refreshRepos → listRegisteredRepos({validate:true})` 上，沒有任何地方 catch，客戶端只會看到「Server disconnected」。
- 實測：在父 commit 上，12 個進程同時 prune 過期 registry、另有一個進程持有 registry lock 時，**4/12 崩潰**；同一套 harness 用 24 進程但無鎖爭用時是 0/24。修復後同條件為 **0/12**。
- 修法是把四份 byte-identical 的原子寫入邏輯收斂成 `storage/fs-atomic.ts` 的 `writeFileAtomic`（隨機 tmp 後綴、`wx` + `0o600`、`retryRename`、失敗時 unlink tmp），並讓 prune 的寫入失敗只記 warning 而非拋出。

## 🎯 核心概念

- **原子寫入（atomic write）**：先寫暫存檔、再以 `rename` 一次性換上目標檔，讓讀者永遠只看到完整內容。
- **暫存檔私有性（tmp path privacy）**：`rename` 對「讀者」是原子的，但若暫存路徑不是寫入者私有的，多個「寫入者」之間仍會互相踩踏。
- **`withRegistryLock`（#2716）**：序列化 registry 寫入的鎖，但在 5 秒 `IndexLockTimeoutError` 後會刻意降級成 UNLOCKED（選可用性而非序列化）。
- **prune（修剪）**：`listRegisteredRepos({validate:true})` 順手把失效 repo 從 registry 移除的家務性寫入，並非呼叫端請求的動作。
- **冷啟動預算（cold-start budget）**：`gitnexus augment` 這條路徑要求 500ms 以內完成，因此 rename 重試的 backoff 時間在此非常昂貴。

## 📖 整理分析

### 1. 固定 tmp 路徑如何殺死 MCP server

`writeRegistry` 一直用同一個固定暫存路徑 `~/.gitnexus/registry.json.tmp`。這個檔案的特殊之處在於：它是機器上**每一個** gitnexus 進程都會寫的那一個檔案。兩個進程同時啟動就會 stage 到同一個 inode，第二個 `writeFile` 覆蓋第一個的位元組，第二個 `rename` 把該 inode 搬到 `registry.json`，第一個進程隨後的 `rename` 在來源端已經沒有東西可搬，於是以 ENOENT 拒絕。

### 2. 為什麼 #2716 的鎖擋不住

#2716 引入的 `withRegistryLock` 會序列化呼叫端，在正常路徑上把這個 bug 遮住。但它在 5 秒 `IndexLockTimeoutError` 之後**刻意降級為 UNLOCKED**（設計取捨是可用性優先於序列化），所以危險視窗仍然存在。作者用實驗把兩者切開：父 commit + 12 進程 + 有人持鎖 → 4/12 崩潰；同 harness + 24 進程但無鎖爭用 → 0/24。結論是寫入本身必須「防碰撞」，不能靠鎖。

### 3. 四份重複邏輯收斂為 writeFileAtomic

`writeMetaFile`（repo-manager）、`writeBridgeMeta`（group/bridge-db）、`writeContractRegistry`（group/storage）其實**早就是正確形狀**——隨機 tmp 後綴、`'wx'` + `0o600`、`retryRename`——但它們是三份 byte-identical 的複製，且沒有一份會在失敗時清掉 tmp。與其新增第四份複製，這段邏輯搬進 `storage/fs-atomic.ts` 的 `writeFileAtomic`（就放在它使用的 `retryRename` 旁邊），四個寫入者全部改呼叫它。helper 額外在 rethrow 之前 unlink tmp：固定檔名時洩漏的 tmp 會被下一個寫入者覆蓋而自我限制，但隨機後綴會在每次發佈失敗時，在目標旁留下一個新的孤兒檔。

附帶行為變更：`registry.json` 現在以 `0o600` 建立（先前繼承 umask，通常是 `0o644`），與 `gitnexus.json` 一直以來的做法一致；既有安裝會在下一次改寫時被收緊權限。

### 4. prune 的寫入不該炸掉整個 server

崩潰的另一半在於 `listRegisteredRepos({validate:true})` 內部那次 prune 寫入。所有呼叫端消費的是回傳的 valid 陣列，而 prune 集合會在下一次 validating read 重新算出來，所以寫入失敗的代價只是「下次再試一遍」，永遠不影響正確性——但把它 rethrow 出去卻會弄垮整個 MCP server。現在改為 catch 並記錄警告，順帶也涵蓋了 home 目錄唯讀、磁碟寫滿這兩種同樣會在啟動時致命的變體。

### 5. 後續 refactor：attempts 與 saveMeta

第二個 commit 是收尾打磨。`writeFileAtomic` 拿掉 `mode` 參數（沒有任何呼叫端變動過它）並內聯 `0o600`，改為透傳 `attempts` 給 `retryRename`。`listRegisteredRepos` 的 prune 寫入傳 `attempts: 1`：反正失敗就丟棄，那 300ms 的 rename backoff 毫無收益，卻是在持有 registry lock 的狀態下、又落在 `gitnexus augment` 這種 sub-500ms 冷啟動預算與 MCP 啟動路徑上被白白花掉。

`saveMeta` 改成只序列化 meta 一次而非每個寫出檔案各一次：meta 每個檔案帶一筆 `fileHashes`，在此 repo 上是 263KB、約 420us，且隨檔案數線性成長，而它原本每次 save 被 stringify 兩次、每次 analyze 又發生數次。`writeMetaFile` 在前一個 commit 後只剩一行轉發，於是併回 `saveMeta`。註解方面，四個寫入者原本各自複述同一份契約、#2888 的來龍去脈出現在四個檔案裡，現在只保留 helper 裡一份權威說明，加上 `writeRegistry` 處一句「為什麼光靠鎖不夠」的 registry 專屬註記。

### 6. 測試與驗證

新增的 `test/unit/repo-manager-registry-atomic-write.test.ts` 五個測試在父 commit 上**全數失敗**，其中四個正是上述那個 ENOENT，在本 commit 上全數通過；進程層級的重現腳本在持鎖情況下從 4/12 崩潰降到 0/12。後續 commit 再加上 `test/unit/storage/fs-atomic.test.ts`，以行為而非原始碼文字驗證這個原語：發佈出去的位元組、結果檔的 `0o600`、三個並發發佈者對同一目標全部 resolve、以及發佈失敗時不留 tmp 殘骸且原內容完好。原本 `insecure-tempfile.test.ts` 用原始碼 regex 近似的就是這些性質，因此縮回到 regex 真正擅長的那一件事：這個模組沒有自己手刻 tmp 路徑。

作者標註為 Gergo Magyar 與 Claude Opus 5（1M context）共同完成。

## 🧭 流程圖 / 架構圖

```mermaid
flowchart TB
    subgraph before["修復前：共用固定 registry.json.tmp"]
        A1["進程 A writeFile 到固定 tmp"] --> B1["進程 B writeFile 覆蓋同一 inode"]
        B1 --> C1["B rename 成功，tmp 已被搬走"]
        C1 --> D1["A rename 找不到來源 → ENOENT"]
        D1 --> E1["落在 mcpCommand → LocalBackend.init → refreshRepos → listRegisteredRepos 無人 catch"]
        E1 --> F1["客戶端顯示 Server disconnected"]
    end
    subgraph after["修復後：storage/fs-atomic.ts 的 writeFileAtomic"]
        A2["每個寫入者取得隨機後綴 tmp"] --> B2["以 wx 旗標建立，權限 0o600"]
        B2 --> C2["retryRename 原子搬到目標"]
        C2 --> D2["失敗則 unlink tmp 後再 rethrow"]
        D2 --> E2["prune 寫入失敗只記 warning"]
    end
```

## 🧠 Mindmap

```mermaid
mindmap
  root((registry 原子寫入修復))
    問題
      固定 tmp 路徑非寫入者私有
      共用 inode 導致 rename ENOENT
      落在 MCP 啟動路徑無人 catch
    為何鎖無效
      withRegistryLock 5s 後降級 UNLOCKED
      12 進程持鎖時 4/12 崩潰
      24 進程無爭用時 0/24
    修復
      writeFileAtomic 收斂四份重複邏輯
      隨機 tmp 後綴 加 wx 加 0o600
      失敗時 unlink tmp
    韌性
      prune 寫入改記 warning
      涵蓋唯讀 home 與磁碟寫滿
    效能收尾
      prune 傳 attempts 1 省 300ms backoff
      saveMeta 只序列化一次 263KB meta
    驗證
      5 個新測試在父 commit 全失敗
      崩潰率 4/12 降到 0/12
```
<!-- deep-analysis:end -->
### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(storage): give every registry write its own tmp path ( #2888 ) 
 
 writeRegistry staged the global registry through a FIXED 
 ~/.gitnexus/registry.json.tmp . The rename is atomic with respect to 
readers, but the tmp path is not private to the writer, and that file is 
the one file every gitnexus process on the machine writes. Two of them 
starting together stage through the same inode: the second writeFile 
overwrites the first's bytes, the second rename moves that inode onto 
 registry.json , and the first's own rename then finds nothing at the 
source and rejects with 
 ENOENT: no such file or directory, rename '/registry.json.tmp' -&gt; '/registry.json' 
 which kills the MCP server, because it lands on the startup path 
( mcpCommand -&gt; LocalBackend.init -&gt; refreshRepos -&gt; 
 listRegisteredRepos({validate:true}) ) where nothing catches — the 
client just reports "Server disconnected". 
 #2716 's withRegistryLock serializes the callers and hides this in the 
normal path, but it deliberately degrades to UNLOCKED after a 5s 
 IndexLockTimeoutError (availability over serialization), so the window 
is still live. Measured on this branch's parent with 12 concurrent 
processes pruning a stale registry while another process held the 
registry lock: 4/12 crashed with the trace above. Same harness with 24 
processes and no lock contention: 0/24. So the write itself has to be 
collision-proof rather than relying on the lock. 
 writeMetaFile (repo-manager), writeBridgeMeta (group/bridge-db) and 
 writeContractRegistry (group/storage) already carried the correct 
shape — random tmp suffix, 'wx' + 0o600 , retryRename — as three 
byte-identical copies, none of which cleaned up its tmp file on failure. 
Rather than adding a fourth copy, that sequence moves to 
 writeFileAtomic in storage/fs-atomic.ts (beside retryRename , which 
it uses) and all four writers call it. The helper also unlinks the tmp 
before rethrowing: with a fixed name a leaked tmp was self-limiting 
because the next writer overwrote it, but a random suffix would drop a 
fresh orphan beside the target on every failed publish. 
 Second half of the same crash: the prune write inside 
 listRegisteredRepos({validate:true}) is housekeeping, not the caller's 
request. Every caller consumes the returned valid array and the prune 
set is recomputed from scratch on the next validating read, so a failed 
write costs a retry, never correctness — while rethrowing it took down 
the whole MCP server. It is now caught and warned about, which also 
covers the read-only-home and full-disk variants of the same startup 
death. 
 Note: registry.json is now created 0o600 (it inherited the umask 
before, typically 0o644 ), matching what gitnexus.json has always 
used. A rewrite tightens the mode on existing installs. 
 Verified: the five new tests in 
test/unit/repo-manager-registry-atomic-write.test.ts all fail on the 
parent commit — four with the exact ENOENT above — and pass here; the 
process-level repro goes 4/12 -&gt; 0/12 crashes with the lock held. 
 Co-Authored-By: Claude Opus 5 (1M context) noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_01VXSu2fTmm7EZGDVquWeBrL 
 
 refactor(storage): trim the atomic-write helper and its guards 
 
 Follow-up polish on the #2888 fix, no behaviour change except where noted. 
 
 writeFileAtomic drops the mode parameter (no caller ever varied it) 
and inlines 0o600 , and gains an attempts pass-through to 
 retryRename . The prune write in listRegisteredRepos now passes 
 attempts: 1 : it discards a failure anyway, so the 300ms of rename 
backoff bought nothing and was spent holding the registry lock, on a 
path with a sub-500ms cold-start budget ( gitnexus augment ) and on MCP 
startup. 
 saveMeta serialises meta once instead of once per written file. 
 meta carries a fileHashes entry per file — 263KB and ~420us on this 
repo, linear in file count — and it was being stringified twice per 
save, several times per analyze. writeMetaFile was a one-line 
forwarder after the previous commit, so it folds into saveMeta . 
 Comments: the four writers were each restating the primitive's 
contract, and the #2888 narrative appeared in four files. Kept one 
authoritative copy in the helper, one registry-specific note at 
 writeRegistry (why the lock is not enough), and deleted the rest. 
 Tests: new test/unit/storage/fs-atomic.test.ts covers the primitive 
behaviourally — published bytes, 0o600 on the result, three 
concurrent publishers to one target all resolving, no leftover tmp and 
intact previous content when the publish fails. That is what the 
source-text regexes in insecure-tempfile.test.ts were approximating, so 
those shrink to the one thing regex is good for: this module does not 
hand-roll a tmp path. The registry test drops the assertions the 
primitive now owns, an unused fs.writeFile capture, a type alias with 
two as unknown as casts the sibling harnesses do without, and moves 
its two path-only temp repos to beforeAll . 
 
 Co-Authored-By: Claude Opus 5 (1M context) noreply@anthropic.com 
Claude-Session: https://claude.ai/code/session_01VXSu2fTmm7EZGDVquWeBrL 
 
 Co-authored-by: Gergo Magyar gergomagyar0@gmail.com 
Co-authored-by: Claude Opus 5 (1M context) noreply@anthropic.com

</details>