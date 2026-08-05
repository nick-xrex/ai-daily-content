---
id: inbox_5e2cd400
date: 2026-08-03
source_ref: "[[00-inbox/2026-08-03/0144-simon-willison-condense-json-1-1-12c6]]"
title: "condense-json 1.1"
url: https://simonwillison.net/2026/Aug/3/condense-json/#atom-everything
source: simon-willison
published_at: 2026-08-03T04:56:26+00:00
fetched_at: 2026-08-05T01:55:18.131109+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "condense-json 1.1 發布，為 JSON 壓縮工具庫帶來功能擴展。Replacements 物件現可包含非字串值（如數字、物件），condense_json() 和 uncondense_json() 會自動識別並用作結構化替換規則，提升轉換表現力。新增物件級 merge 操作支援，condense-json() 能識別相似物件並產生鍵更新/刪除指令集，uncondense_json() 再套用這些合併操作實現複雜資料變換。同時加入 Hypothesis property-based 測試框架，確保往返轉換的正確性和邊界情況覆蓋。"
key_points:
  - "Replacements 物件擴展支援非字串值（數字、物件等），提升結構化替換表現力"
  - "新增物件級 merge 操作，能識別相似物件並產生鍵更新/刪除指令，支援更精細資料轉換"
  - "導入 Hypothesis property-based 測試確保往返轉換（round-trip）正確性"
tags: [json, data-compression, tool]
topics: []
importance: 2
novelty: 2
insight_quality: 2
insight_type: tool
deep_dive_candidate: false
deep_dive_approved: false
---

## condense-json 1.1

condense-json 1.1 發布，為 JSON 壓縮工具庫帶來功能擴展。Replacements 物件現可包含非字串值（如數字、物件），condense_json() 和 uncondense_json() 會自動識別並用作結構化替換規則，提升轉換表現力。新增物件級 merge 操作支援，condense-json() 能識別相似物件並產生鍵更新/刪除指令集，uncondense_json() 再套用這些合併操作實現複雜資料變換。同時加入 Hypothesis property-based 測試框架，確保往返轉換的正確性和邊界情況覆蓋。

### 重點
- Replacements 物件擴展支援非字串值（數字、物件等），提升結構化替換表現力
- 新增物件級 merge 操作，能識別相似物件並產生鍵更新/刪除指令，支援更精細資料轉換
- 導入 Hypothesis property-based 測試確保往返轉換（round-trip）正確性

**原文：** [simon-willison](https://simonwillison.net/2026/Aug/3/condense-json/#atom-everything)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

Release: condense-json 1.1 
 After shipping condense-json 1.0 I started integrating it into LLM, and found there were some desirable new features already: 
 
 
 Replacements object can now include values other than strings. These will be identified and used as structural replacements by condense_json() and uncondense_json() . #8 
 Objects can be used as the basis for merge operations. condense_json() will identify if there are objects that are a close match and will store instructions for keys to update or delete. uncondense_json() can then apply these merges. 
 
 
 I also added some round-trip tests using the Hypothesis property-based Python testing library. 
 
 
 Tags: json

</details>