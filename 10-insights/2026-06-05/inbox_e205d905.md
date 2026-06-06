---
id: inbox_e205d905
date: 2026-06-05
source_ref: "[[00-inbox/2026-06-05/1800-gitnexus-releases-rc-281ce2600c4c13ebdf43b697c90e2f0481d0e-86aa]]"
title: "rc/281ce2600c4c13ebdf43b697c90e2f0481d0ee76: fix(java): close parsing-layer coverage gaps F35/F38/F41 (#1928) (#2045)"
url: https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F281ce2600c4c13ebdf43b697c90e2f0481d0ee76
source: gitnexus-releases
published_at: 2026-06-05T05:39:12+00:00
fetched_at: 2026-06-05T18:05:41.420303+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "GitNexus 修復 Java 解析層覆蓋缺口 F35/F38/F41。F35 修正 qualified/generic constructor 呼叫解析（new pkg.Foo() 型式）；F38 合成 super()/this() 顯式 constructor 呼叫 CALLS 邊；F41 修復 qualified generic 型別引數的剝離順序（Map<String, com.example.User>）。並修正 Constructor 多載鍵註冊防止 this()/super() self-loop。加入低階單元測試及端對端解析器測試。"
key_points:
  - "修復 qualified/generic constructor 查詢捕獲（F35）及 super()/this() explicit constructor 邊合成（F38）"
  - "修正 qualified generic 型別引數剝離順序及 self-loop 多載鍵問題（F41、P2/P3）"
  - "擴充 Constructor 多載鍵註冊機制（node-lookup.ts、ids.ts）並加入完整單元/整合測試"
tags: [gitnexus, java, parser, type-resolution]
topics: []
importance: 1
novelty: 1
insight_quality: 2
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## rc/281ce2600c4c13ebdf43b697c90e2f0481d0ee76: fix(java): close parsing-layer coverage gaps F35/F38/F41 (#1928) (#2045)

GitNexus 修復 Java 解析層覆蓋缺口 F35/F38/F41。F35 修正 qualified/generic constructor 呼叫解析（new pkg.Foo() 型式）；F38 合成 super()/this() 顯式 constructor 呼叫 CALLS 邊；F41 修復 qualified generic 型別引數的剝離順序（Map<String, com.example.User>）。並修正 Constructor 多載鍵註冊防止 this()/super() self-loop。加入低階單元測試及端對端解析器測試。

### 重點
- 修復 qualified/generic constructor 查詢捕獲（F35）及 super()/this() explicit constructor 邊合成（F38）
- 修正 qualified generic 型別引數剝離順序及 self-loop 多載鍵問題（F41、P2/P3）
- 擴充 Constructor 多載鍵註冊機制（node-lookup.ts、ids.ts）並加入完整單元/整合測試

**原文：** [gitnexus-releases](https://github.com/abhigyanpatwari/GitNexus/releases/tag/rc%2F281ce2600c4c13ebdf43b697c90e2f0481d0ee76)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

fix(java): close parsing-layer coverage gaps F35/F38/F41 ( #1928 ) 
 
 Registry-primary scope-resolution path (the live one post- #942 / #943 ): 
 
 
 F35 [HIGH]: qualified / qualified-generic constructor calls. new pkg.Foo() 
parses as a scoped_type_identifier that the query bound only as 
 @reference.call.constructor.qualified with no @reference.name , so the 
scope extractor fell back to the whole-expression anchor and the reference 
name became the raw new pkg.Foo() text (never resolved). Bind the simple 
-name tail (end-anchored last child) and add an arm for the previously 
uncaptured new pkg.Box&lt;String&gt;() (qualified + generic) shape. 
 
 
 F38 [MEDIUM]: super(...) / this(...) explicit constructor invocations, 
modeled as explicit_constructor_invocation and never matched by the scope 
query, dropped the chained-constructor CALLS edges. Synthesize them with the 
target resolved structurally (this -&gt; enclosing type name; super -&gt; superclass 
tail via the shared javaBaseLookupNameNode, skipping implicit Object) plus 
arity for overload disambiguation. 
 
 
 F41 [LOW]: interpretJavaTypeBinding stripped the qualifier before generics, so 
a qualified generic type arg ( Map&lt;String, com.example.User&gt; ) was cut inside 
the generic into User&gt; . Strip generics first, then the qualifier; make the 
erasure fallback qualifier-tolerant. 
 
 
 F36/F37 already landed upstream ( #1940 / #1956 ); F39/F40 are legacy-bank remnants 
that are no longer consumed (legacy @import skipped in parse-worker; legacy 
 @call never read in parse-impl) so they are intentionally left untouched. 
 Tests: low-level capture unit tests (constructor shapes incl. double-match 
guard; super/this/enum/implicit-Object), interpretJavaTypeBinding unit tests 
(qualified generic args + the corruption case), and end-to-end resolver tests 
with new fixtures asserting the CALLS edges resolve to the correct constructors. 
 Co-authored-by: Cursor cursoragent@cursor.com 
 
 fix(scope-resolution): register Constructor overload keys so this()/super() chains don't self-loop ( #1928 F38 review) 
 
 Review of #2045 caught two gaps; both confirmed by reproduction. 
 P2 — F38 this() emitted a self-loop. On the java-explicit-constructor fixture, 
Child(int){ this(); } produced CALLS Child()#0 -&gt; Child()#0 instead of 
Child(int) #1 -&gt; Child()#0. Root cause is the language-agnostic graph-bridge: the 
parse phase mints distinct Constructor nodes (Child#0, Child#1) carrying 
parameterTypes, but node-lookup.ts registered the parameter-types / shape 
overload keys only for Function/Method, never Constructor, so both ctors 
collapsed onto the first-wins qualified/simple key and the caller Child(int) 
resolved to Child#0 (the this() target). Extend the overload keys to Constructor 
in both node-lookup.ts (registration) and ids.ts (lookup) via a shared 
isOverloadableCallable predicate. Verified the edge now connects distinct nodes 
(Child#1 -&gt; Child#0); super(1)-&gt;Base#1 still correct. No cross-language 
regressions (the 9 worker-path failures reproduce identically on clean HEAD). 
 Also harden the integration test: it matched the this() edge on name only, which 
a self-loop satisfies; now assert the endpoints are DISTINCT constructors. 
 P3 — F41 order-regression guard was inert (List&lt;Map&lt;String,User&gt;&gt; normalizes to 
List under both strip orders). Add List&lt;com.x.Foo&gt; -&gt; List, which is 
corrupted to Foo&gt; under the old order and only correct generics-first. 
 Co-authored-by: Cursor cursoragent@cursor.com 
 
 fix(java): update fingerprint and add notes for constructor query captures in baselines.json 
 
 Updated the fingerprint for the Java section and added detailed notes regarding the enhancements in constructor query captures, including qualified and qualified-generic constructor queries. This change reflects ongoing improvements in the parsing layer coverage and fixture updates. 
 
 Co-authored-by: Cursor cursoragent@cursor.com 
Co-authored-by: Gergő Magyar gergomagyar@icloud.com

</details>