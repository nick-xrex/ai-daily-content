---
id: inbox_56b52865
source: ruflo-releases
source_type: rss
url: "https://github.com/ruvnet/ruflo/releases/tag/v3.32.34"
author: "ruvnet"
published_at: 2026-07-29T13:39:58+00:00
fetched_at: 2026-07-29T22:26:10.231665+00:00
content_hash: "331f8dd4d3420f4e85deafb8ac7a50c88bcc53dcdcfd3d1b1f3ffc1ee2680daf"
lang: en
caption_quality: None
raw: true
topics: []
---

# Ruflo v3.32.34 — Reliable Memory Writes on Existing Installations

Ruflo v3.32.34: Reliable Memory Writes on Existing Installations 
 v3.32.34 repairs a migration gap that could prevent memory store and MCP 
 memory_store writes on databases created before ADR-323. 
 The native AgentDB bridge now adds the required provenance_type column to 
existing memory_entries tables before writing. If that migration cannot run 
because the database is read-only, locked, or damaged, Ruflo fails closed and 
reports the native bridge error instead of presenting an unrelated WAL fallback 
message. 
 The bridge failure latch is also recoverable: shutdown resets it, successful 
native writes clear stale diagnostics, and degradation notices remain visible. 
 Install or upgrade 
 npm install --global ruflo@3.32.34
ruflo doctor 
 Existing databases are migrated automatically on the first native bridge 
access. No manual SQL is required. 
 Verify memory round-trip 
 ruflo memory store \
 --key release-3.32.34-check \
 --value " memory bridge migration works " \
 --namespace verification

ruflo memory retrieve \
 --key release-3.32.34-check \
 --namespace verification 
 For MCP clients, the equivalent memory_store and memory_retrieve tools use 
the same repaired path. 
 What changed 
 
 Migrates provenance_type on pre-ADR-323 AgentDB files. 
 Retries schema setup when the database was not writable. 
 Preserves the actual native bridge error for diagnostics. 
 Clears obsolete bridge errors after a successful native write. 
 Resets a failed initialization latch during bridge shutdown. 
 Keeps native-driver fallback notices visible. 
 Adds regression coverage for legacy databases, idempotent migration, 
fail-closed migration, and failure-latch recovery. 
 
 Compatibility 
 The migration is additive and idempotent. New databases already contain the 
column; existing databases receive it once; installations without the optional 
native bridge continue to use the existing sql.js path. 
 This release resolves #2843 via 
 #2844 .