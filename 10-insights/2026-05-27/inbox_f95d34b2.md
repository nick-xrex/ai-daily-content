---
id: inbox_f95d34b2
date: 2026-05-27
source_ref: "[[00-inbox/2026-05-27/2345-gitnexus-releases-rc-d9d6318b64cd76a800ded7ae055561568b416-25f0]]"
title: "rc/d9d6318b64cd76a800ded7ae055561568b416477: feat(group): add Kotlin Spring HTTP consumer extraction (#1855)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fd9d6318b64cd76a800ded7ae055561568b416477
source: gitnexus-releases
published_at: 2026-05-27T20:32:24+00:00
fetched_at: 2026-05-27T23:50:57.795427+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 擴展 Kotlin Spring HTTP 消費者提取，支持三大模式以提升多語言倉庫的程式碼智能。RestTemplate 全動詞族（getForObject/getForEntity → GET、postForObject/postForEntity → POST、put → PUT、delete → DELETE、patchForObject → PATCH），與 Java 外掛共享單一 contract ID 確保多語言一致。WebClient 短形式（webClient.get().uri(\"/x\")）透過巢狀 call_expression 雙層查詢解析動詞，OkHttp Request.Builder().url(\"/x\") 因 Kotlin navigation_expression 結構採異形查詢但維持相同 contract 格式。受 sibling 呼叫鏈限制，OkHttp 和 WebClient 長形式（.method(HttpMethod.X).uri(\"/y\")）目前預設 GET 方法（與 Java 外掛同步），已補充防迴歸測試文件化此已知限制，未來 verb-walk 實裝可同步更新多語言。"
key_points:
  - "三種 HTTP 消費者模式：RestTemplate (getForObject/postForObject/put/delete/patchForObject)、WebClient 短形式 (.get().uri() / .post().uri() / 等) 及 OkHttp Request.Builder().url()；共 5 正向測試 + 2 防迴歸測試涵蓋 25+ 呼叫"
  - "接收器名稱約束策略（#eq? @obj \"restTemplate\" / #eq? @cls \"Request\"）：降低誤判率優先於完全精度，無法捕捉別名接收器（文件化於檔案頭），符合 Java 外掛啟發式方法"
  - "已知限制與設計決策：OkHttp POST-chain 預設 GET（java.ts 同步行為）、WebClient 長形式推遲實裝（需 sibling walk helper），限制條款與測試綁定，未來 verb-walk 可同步更新多語言外掛與註解"
tags: [kotlin-support, http-extraction, code-patterns, polyglot-architecture, design-decision]
topics: [agents.mcp]
importance: 3
novelty: 4
insight_quality: 4
insight_type: technique
deep_dive_candidate: true
deep_dive_approved: false
---

## rc/d9d6318b64cd76a800ded7ae055561568b416477: feat(group): add Kotlin Spring HTTP consumer extraction (#1855)

GitNexus 擴展 Kotlin Spring HTTP 消費者提取，支持三大模式以提升多語言倉庫的程式碼智能。RestTemplate 全動詞族（getForObject/getForEntity → GET、postForObject/postForEntity → POST、put → PUT、delete → DELETE、patchForObject → PATCH），與 Java 外掛共享單一 contract ID 確保多語言一致。WebClient 短形式（webClient.get().uri("/x")）透過巢狀 call_expression 雙層查詢解析動詞，OkHttp Request.Builder().url("/x") 因 Kotlin navigation_expression 結構採異形查詢但維持相同 contract 格式。受 sibling 呼叫鏈限制，OkHttp 和 WebClient 長形式（.method(HttpMethod.X).uri("/y")）目前預設 GET 方法（與 Java 外掛同步），已補充防迴歸測試文件化此已知限制，未來 verb-walk 實裝可同步更新多語言。

### 重點
- 三種 HTTP 消費者模式：RestTemplate (getForObject/postForObject/put/delete/patchForObject)、WebClient 短形式 (.get().uri() / .post().uri() / 等) 及 OkHttp Request.Builder().url()；共 5 正向測試 + 2 防迴歸測試涵蓋 25+ 呼叫
- 接收器名稱約束策略（#eq? @obj "restTemplate" / #eq? @cls "Request"）：降低誤判率優先於完全精度，無法捕捉別名接收器（文件化於檔案頭），符合 Java 外掛啟發式方法
- 已知限制與設計決策：OkHttp POST-chain 預設 GET（java.ts 同步行為）、WebClient 長形式推遲實裝（需 sibling walk helper），限制條款與測試綁定，未來 verb-walk 可同步更新多語言外掛與註解

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2Fd9d6318b64cd76a800ded7ae055561568b416477)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

feat(group): add Kotlin Spring HTTP consumer extraction 
 
 Follow-up to #1849 (Kotlin providers). Extends http-patterns/kotlin.ts 
with three call-site patterns common in Kotlin Spring projects: 
 
 
 RestTemplate: restTemplate.getForObject("/x", ...) and the 
full verb family (getForObject/getForEntity → GET, 
postForObject/postForEntity → POST, put → PUT, delete → DELETE, 
patchForObject → PATCH). Mirrors the Java plugin's 
 REST_TEMPLATE_TO_HTTP map so polyglot repos coalesce on a 
single contract id. 
 
 
 WebClient short form: webClient.get().uri("/x") and the 
 .post() / .put() / .delete() / .patch() siblings. The 
chain parses as two nested call_expression nodes; the query 
anchors on the outer .uri(...) and walks one level inward 
to constrain the verb. 
 
 
 OkHttp: Request.Builder().url("/x") . Kotlin parses 
 Request.Builder() as a call_expression whose callee is a 
 navigation_expression (not Java's object_creation_expression ), 
so the query shape differs from java.ts but the receiver/method 
constraints ( Request / Builder / url ) and emitted 
contract format match. 
 
 
 Out of scope: webClient.method(HttpMethod.X).uri("/y") long form. 
The verb sits on a sibling call_expression two hops away, so it 
needs a walk-up helper rather than a flat tree-sitter query. A 
dedicated anti-overreach test pins the current behavior so a future 
short-form change can't accidentally start matching the long form. 
 Receiver name constraints ( #eq? @obj "restTemplate" , 
 #eq? @cls "Request" ) match the Java plugin's heuristic — a project 
that aliases the receiver under a different name won't be picked up. 
This trade-off keeps false-positive rates low and is documented in 
the file header. 
 Tests: 5 new cases under consumer extraction — fetch patterns , 
gated by tree-sitter-kotlin grammar availability. 
 positive (3) 
 
 RestTemplate verbs (5 calls × 5 verbs) 
 WebClient short-form verbs (5 calls × 5 verbs) 
 OkHttp Request.Builder().url("/x") 
anti-regression (2) 
 WebClient long form .method(HttpMethod.X) produces no 
consumer (deferred-feature pin) 
 non-restTemplate receiver does not match (receiver-name pin) 
 
 Reverse-validated: removing the (#eq? @obj "restTemplate") 
constraint causes the receiver-name anti-regression test to fail. 
 Local validation: 
 
 test/unit/group/http-route-extractor.test.ts: 59/59 ✅ 
 test/unit/group: 539/539 ✅ 
 npm run format:check: clean ✅ 
 
 
 test(group): pin Kotlin OkHttp POST-chain heuristic-default GET behavior 
 
 Address Claude review on PR #1855 (Finding 1). 
 The OkHttp query in kotlin.ts:OK_HTTP_PATTERNS matches the 
 .url("/x") sub-expression of a builder chain, but the verb is 
encoded on a separate sibling call ( .post(body) / .delete() / 
...). The query intentionally does not walk the chain to recover 
the verb — it emits method: 'GET' for every match, mirroring the 
Java plugin's OK_HTTP_PATTERNS (java.ts). 
 Concretely: Request.Builder().url("/x").post(body).build() becomes 
 http::GET::/x , not http::POST::/x . This is an already-accepted 
Java parity heuristic, but it was untested on the Kotlin side. 
 This commit: 
 
 Adds an anti-overreach test pinning the current behavior:
 
 exactly one consumer is emitted with method=GET 
 no second http::POST::/x consumer appears 
 
 
 Documents the limitation in kotlin.ts as a "Known limitation" 
block tied to the test, so a future verb-walk implementation 
has to update the comment in lockstep with the assertion. 
 
 Rationale for not implementing verb-walk in this PR: 
 
 Verb-walk requires walking sibling call_expression nodes (the 
 .post(body) chain), which is the same shape as the 
deferred WebClient long-form work 
 Java has the same limitation in production today; fixing only 
Kotlin would create polyglot drift 
 A coordinated future PR can add verb-walk to both plugins at 
once and update both comments + the pin tests together 
 
 Finding 2 (silent test-skip when tree-sitter-kotlin grammar is 
unavailable) is intentionally NOT addressed here — same gating 
pattern was accepted in #1849 for Provider tests, and a coordinated 
follow-up should add a CI sentinel covering both Provider and 
Consumer suites in one place. 
 Local validation: 
 
 test/unit/group/http-route-extractor.test.ts: 60/60 ✅ 
 test/unit/group: 540/540 ✅ 
 npm run format:check: clean ✅ 
 
 
 Co-authored-by: henry zhangwei2017@unipus.cn

</details>