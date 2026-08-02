# PinkIntel LLM Dataset Guide

## What this repository is

This private repository begins with one clean baseline containing the complete corpus currently published through PinkPanther.News. It is not a dump of every item ever encountered by the collector: hidden, orphaned and no-longer-public records are excluded.

The baseline includes article records and complete story records. A story record is the machine-readable equivalent of an opened PinkPanther.News story page: all connected source articles with full archived text and revisions, story synthesis, L/S/D and comparison views, classification, placement, source and image provenance, automated audit trace, and current “Read more” cards.

## Layout

```text
baseline/YYYY-MM-DD/                 # clean starting snapshot
  manifest.json                      # scope, hashes and signature metadata
  manifest.sig                       # detached Ed25519 signature of package_sha256
  README.md                          # package-specific orientation
  pink-article-intelligence.jsonl.gz # one JSON record per article
  pink-story-intelligence.jsonl.gz   # one complete JSON record per public story
  articles/
    001-source-title-id.json.gz      # individual machine article record
    001-source-title-id.md           # readable article sidecar
  stories/
    001-story-slug-id.json.gz        # individual complete story record
    001-story-slug-id.md             # readable story sidecar
  images/
    sha256.ext                       # actual archived image bytes, de-duplicated
daily/YYYY-MM-DD/                    # later signed deltas
identity/
  pinkpanther-data-signing-ed25519-public.pem
```

`*.json.gz` and `*.jsonl.gz` are UTF-8 JSON compressed with gzip. Image filenames are content-addressed SHA-256 archive keys. Compression and hashing are not access control.

## Preparation workflow

1. Work only inside the agreed recipient environment.
2. Verify the manifest signature before unpacking or indexing a package.
3. Keep article, story, source and `record_hash` provenance in every downstream index, evaluation set, model card or experiment ledger.
4. Decompress text and stage image assets only in encrypted, access-controlled storage.
5. Treat later daily packages as auditable deltas; never silently replace earlier provenance.

Example:

```bash
# Stream a baseline record without writing uncompressed text to disk.
gzip -cd baseline/2026-08-02/pink-story-intelligence.jsonl.gz | head -n 1 | jq .

# Inspect a single complete story record.
gzip -cd baseline/2026-08-02/stories/001-...json.gz | jq .
```

## Signature verification

`manifest.sig` is an Ed25519 signature of the textual `package_sha256` from `manifest.json`.

```bash
node - <<'NODE'
const fs = require('node:fs');
const crypto = require('node:crypto');
const dir = process.argv[1] || 'baseline/2026-08-02';
const manifest = JSON.parse(fs.readFileSync(`${dir}/manifest.json`, 'utf8'));
const publicKey = fs.readFileSync('identity/pinkpanther-data-signing-ed25519-public.pem', 'utf8');
const signature = Buffer.from(manifest.signature.value_base64, 'base64');
const valid = crypto.verify(null, Buffer.from(manifest.package_sha256, 'utf8'), publicKey, signature);
console.log({ valid, dataset_day: manifest.dataset_day, articles: manifest.scope.articles_included, stories: manifest.scope.stories_included });
process.exit(valid ? 0 : 1);
NODE
```

The record marker `PINKPANTHER.NEWS/LLM-DATASET/v1` and the PinkPanther.News PGP fingerprint are provenance metadata. The Ed25519 signature verifies the delivered package.

## Visual assets

The `images/` directory contains actual archived source image bytes, not generated illustrations. Every image used by a story or its “Read more” cards is referenced by `storage_key` and `package_path` in the relevant record. The same bytes appear once per SHA-256 filename even if several sources use them. Use these images only under the written agreement and retain attribution metadata.

## Use boundary

PinkPanther.News processing is fully automatic. Stored classifications, comparisons and source profiles are machine-generated analytical outputs, not human editorial determinations or statements of fact.

Permitted use is only what the written agreement allows: internal RAG with provenance, evaluation of clustering/classification/summarisation, controlled model training or public-interest research. Do not publish, redistribute, sublicense or expose raw text, images or packages; strip provenance; claim independent collection; or treat automated classifications as proof of political facts, truthfulness, bias, legality or liability.
