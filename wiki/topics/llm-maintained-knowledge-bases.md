---
type: Topic
title: LLM-maintained knowledge bases
description: What LLM-maintained wikis are, how they differ from retrieval tools, their risks for clinicians, and the Open Knowledge Format.
resource: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
tags: [ai, knowledge-management, digital-health, cpd]
timestamp: 2026-09-26T21:00:00+01:00
status: draft
share: yes
sources: [../sources/karpathy-llm-wiki-gist.md]
---

# LLM-maintained knowledge bases

An LLM reads each new source once and **integrates** it into a growing set of linked notes, rather than searching raw documents afresh for every question ([Karpathy](../sources/karpathy-llm-wiki-gist.md)). Knowledge compounds; the human curates sources and asks questions, and the machine does the bookkeeping.

## Compared with other approaches

| | Retrieval (RAG, NotebookLM) | LLM-maintained wiki |
|---|---|---|
| When synthesis happens | At every question | Once, at ingest; kept current |
| Contradictions | Rediscovered each time, if at all | Flagged when the new source arrives |
| What you can read | Chat answers | A browsable, linked set of pages (e.g. in Obsidian) |
| Main failure mode | Missing the right fragment | **Confidently wrong pages that later get treated as fact** |

## Relevance to clinicians

- **CPD and appraisal:** reading, podcasts and meetings become linked notes rather than scattered bookmarks, and CPD entries can be drafted from what was ingested.
- **Risks to manage:**
  - **Patient-identifiable data** must never be captured. Photos of clinical slides and meeting notes need checking before ingest.
  - **Verification:** AI-written summaries can drift from their sources. Keep sources separate from synthesis and check anything clinically important against the original.
  - **Governance:** where the model runs (cloud or local) and who can see the notes. Some people use local models (LM Studio, Ollama) for sensitive material.
- **For appraisers:** appraisees may increasingly present AI-assisted learning logs. The questions stay the same — what was learned, what changed, and whose reflection is it?

## Open Knowledge Format (OKF)

Google Cloud, June 2026. An open, vendor-neutral specification for this pattern: a folder of markdown files, one concept per file, YAML frontmatter with a required `type` (plus title, description, resource, tags, timestamp), ordinary markdown links, and reserved `index.md` and `log.md`. The aim is that knowledge written by one tool can be read by any other. This wiki follows it.

> **Open question:** No published evaluation yet shows these wikis are more accurate than retrieval for clinical questions.
