---
id: inbox_1ed5f260
date: 2026-07-16
source_ref: "[[00-inbox/2026-07-16/0012-codex-releases-python-v0-144-4-support-custom-transport-27a2]]"
title: "python-v0.144.4: Support custom transports for Amazon Bedrock (#33695)"
url: https://github.com/openai/codex/releases/tag/python-v0.144.4
source: codex-releases
published_at: 2026-07-16T21:41:00+00:00
fetched_at: 2026-07-17T00:16:45.376269+00:00
model: claude-haiku-4-5
tokens_in: 0
tokens_out: 0
summary_zh: "OpenAI Codex Python SDK v0.144.4 發布，增加 Amazon Bedrock provider 的客製化傳輸層支援。開發者可覆蓋 base_url、auth 與 http_headers，同時保留預設 Bedrock 配置的區域端點解析。支援 command-based bearer authentication，無需依賴 AWS request signing。credentialSource enum 重構為 usesCodexManagedCredentials boolean。使 command-authenticated 與外部託管認證配置能夠一致地報告。此變更增加企業環境與自訂代理伺服器整合的靈活性。"
key_points:
  - "Bedrock provider 支援 base_url、auth、http_headers 自訂覆蓋，消除 AWS 簽署依賴"
  - "credentialSource enum 改為 usesCodexManagedCredentials boolean，統一 managed/external 認證報告"
  - "保留區域端點解析能力，支援 command-based bearer authentication 與自訂端點搭配"
tags: [codex-sdk, amazon-bedrock, custom-transports, provider-integration, credential-management]
topics: []
importance: 2
novelty: 2
insight_quality: 3
insight_type: announcement
deep_dive_candidate: false
deep_dive_approved: false
---

## python-v0.144.4: Support custom transports for Amazon Bedrock (#33695)

OpenAI Codex Python SDK v0.144.4 發布，增加 Amazon Bedrock provider 的客製化傳輸層支援。開發者可覆蓋 base_url、auth 與 http_headers，同時保留預設 Bedrock 配置的區域端點解析。支援 command-based bearer authentication，無需依賴 AWS request signing。credentialSource enum 重構為 usesCodexManagedCredentials boolean。使 command-authenticated 與外部託管認證配置能夠一致地報告。此變更增加企業環境與自訂代理伺服器整合的靈活性。

### 重點
- Bedrock provider 支援 base_url、auth、http_headers 自訂覆蓋，消除 AWS 簽署依賴
- credentialSource enum 改為 usesCodexManagedCredentials boolean，統一 managed/external 認證報告
- 保留區域端點解析能力，支援 command-based bearer authentication 與自訂端點搭配

**原文：** [codex-releases](https://github.com/openai/codex/releases/tag/python-v0.144.4)

---

### 📄 原文內容

<details>
<summary>點此展開 / 收合</summary>

What changed 
 
 Allow the built-in amazon-bedrock provider to override base_url , auth , 
and http_headers in addition to its AWS profile and region. 
 Use command-based bearer authentication and configured endpoints without 
applying AWS request signing, while retaining regional endpoint resolution 
for the default Bedrock configuration. 
 Replace the Bedrock account credentialSource enum with the 
 usesCodexManagedCredentials boolean so command-authenticated and other 
externally managed configurations are reported consistently. 
 
 Testing 
 
 Cover configuration merging and validation, command-authenticated proxy 
requests with custom headers, and account reporting for managed and external 
credentials. 
 
 GitOrigin-RevId: d1acbe602060470583b5e12f8d304bee5be46f4c

</details>