# PinkIntel LLM Dataset Guide

**Documentation generated:** `2026-09-01T10:12:08Z`  
**Baseline:** `baseline/2026-08-02/`  
**Latest signed delta:** `daily/2026-08-29/`

## What this repository is

This private repository begins with one clean baseline containing the corpus currently published through PinkPanther.News. It is not a dump of every item ever encountered by the collector: hidden, orphaned and no-longer-public records are excluded. The current baseline contains **321** public article records, **107** connected story groups and **16** distinct media sources.

## Layout

```text
baseline/YYYY-MM-DD/                 # clean starting snapshot
  manifest.json                      # scope, hashes and signature metadata
  manifest.sig                       # detached Ed25519 signature of package_sha256
  README.md                          # package-specific orientation
  pink-article-intelligence.jsonl.gz # one machine-readable JSON record per article
  pink-story-intelligence.jsonl.gz   # one complete machine-readable record per public story
  articles/ and stories/             # compressed records with readable .md sidecars
  images/                            # source image bytes, de-duplicated by SHA-256
daily/YYYY-MM-DD/                    # later signed deltas
identity/pinkpanther-data-signing-ed25519-public.pem
```

The machine files are UTF-8 JSON compressed with gzip. The Markdown sidecars are readable orientations, not a replacement for the signed machine record.

## Required preparation

1. Work only in the agreed recipient environment.
2. Verify the manifest signature before unpacking or indexing a package.
3. Preserve article, story, source and `record_hash` provenance in every downstream index, evaluation set, model card or experiment ledger.
4. Treat daily packages as auditable deltas; never silently replace earlier provenance.

## Signature verification

`manifest.sig` is an Ed25519 signature of the textual `package_sha256` in `manifest.json`. Verify the signature with `identity/pinkpanther-data-signing-ed25519-public.pem` before processing the material. The current baseline reports a `signed` signature and package digest `f040188533a97b7c1a5c1a56eef6ba0f703345e264d5df35a83b401f212a740a`.

## Use boundary

PinkPanther.News processing is fully automatic. Stored classifications, comparisons and source profiles are machine-generated analytical outputs, not human editorial determinations or statements of fact. Do not publish, redistribute, sublicense or expose raw text, images or packages; remove provenance; claim independent collection; or treat automated labels as proof of political facts, truthfulness, bias, legality or liability.
