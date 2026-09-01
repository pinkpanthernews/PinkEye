# PINKINTEL

### A private research corpus for Slovenian news.

![Private research corpus](https://img.shields.io/badge/PinkIntel-private%20research%20corpus-ff3d8d?style=flat-square)
![Public corpus rule](https://img.shields.io/badge/scope-currently%20public%20corpus-17233a?style=flat-square)
![Signed packages](https://img.shields.io/badge/integrity-Ed25519%20signed-2f855a?style=flat-square)

> **One event. Many reports. One traceable record.**
>
> PinkIntel turns fragmented Slovenian reporting into connected evidence: public source material, event links, automatic analysis, revisions and a verifiable chain of provenance.

[The brief](#the-brief) · [Signal board](#signal-board) · [Inside a record](#inside-a-record) · [Use cases](#llm-and-research-use-cases) · [Access](#access-and-partnership)

---

## The brief

This repository starts with a single clean snapshot of the corpus currently visible through PinkPanther.News. It is deliberately not a dump of everything the collector has ever seen: hidden, orphaned and no-longer-public records are excluded from delivery.

The useful unit is not only *what one article says*. It is the relationship between reports: who covered the same event, which facts and time frames were included, how a story changed, and which fields are source-derived versus automatic analysis.

## Signal path

```text
Public reporting
      ↓
PinkPanther.News collection and source preservation
      ↓
Article context · revisions · story links · automatic analysis
      ↓
Signed PinkIntel baseline and later daily deltas
      ↓
Approved LLM, RAG and public-interest research
```

## Signal board · latest signed package 2026-08-24

| Signal | Current value |
| --- | ---: |
| Public article records at this export | **3774** |
| Published cross-source story groups at this export | **1341** |
| Articles added in this daily delta | 206 |
| Stories added in this daily delta | 81 |
| Records currently stored in the pipeline | 16939 |
| Files in this daily package | 745 |
| Signed daily deltas after baseline | 21 |
| Baseline article records / story groups | 321 / 107 |
| Baseline distinct media sources | 16 |

**Latest package:** `daily/2026-08-24/`  
**Generated:** `2026-09-01T09:34:56.414Z`  
**Integrity:** `signed` Ed25519 signature · package digest `cbd0e147e26de62889810b3651aac240bbcf596f216719b59d0683214500436d`  
**Baseline reference:** `baseline/2026-08-02/` · 1231 files · 210 records with collected full text · 151 revision snapshots

## Value we can defend

The value is not just text. It is the relationship layer: canonical URLs, timestamps, extraction traces, source identity, event links, revisions, classifications, comparative coverage outputs, placement decisions and integrity records.

At a conservative **12 minutes** to locate, open, normalise, attribute and preserve one article, the **3774 currently public records in this latest signed export** represent at least **754.8 hours** of manual reconstruction work — about **20.1 full-time research weeks** — before cross-source matching, revision tracking or analytical enrichment.

This is a transparent replacement-effort indicator, **not** a sale price, valuation, quality guarantee or substitute for source verification.

## Inside a record

- **Source:** publisher, domain, profile and ownership context where available.
- **Document:** canonical URL, timestamps, title, excerpt and collected text when available.
- **Change:** content hashes, fetch history and revision snapshots.
- **Story:** event membership, linked evidence, comparison outputs and clustering signals.
- **Analysis:** automated classification, entities, event signatures, framing evidence and confidence.
- **Placement:** where and why a story appeared on PinkPanther.News.
- **Integrity:** record hash, package manifest, file hashes, Ed25519 signature and provenance metadata.

## LLM and research use cases

Subject to a written agreement, the corpus can support:

1. Slovenian-language LLM evaluation and controlled fine-tuning preparation.
2. RAG systems that preserve source provenance and citations.
3. Event clustering, similarity and cross-outlet coverage research.
4. Studies of framing, updates, omissions and media ecosystems.
5. Public-interest research by trusted academic or non-commercial partners.

## Access and partnership

This is a private research repository. Access is granted only through an explicit agreement with PinkPanther.News. Trusted public-interest and academic partners may receive no-cost access when purpose, security and attribution terms fit the project.

Raw material, derived datasets and provenance markers must not be redistributed, stripped or presented as independently collected. Read [LLM-DATASET-GUIDE.md](LLM-DATASET-GUIDE.md) before processing a package and [DATA-ACCESS.md](DATA-ACCESS.md) before using it.

> [!IMPORTANT]
> PinkIntel is built for AI systems that retain attribution, provenance and uncertainty. Automated analysis is evidence-bearing model output — not ground truth.
