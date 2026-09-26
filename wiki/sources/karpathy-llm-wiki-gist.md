---
type: Source
title: "Karpathy — LLM Wiki (GitHub gist)"
description: Andrej Karpathy's April 2026 pattern for personal knowledge bases maintained by an LLM, and the discussion around it.
resource: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
tags: [ai, knowledge-management, digital-health]
timestamp: 2026-09-26T21:00:00+01:00
status: draft
share: yes
sources: []
---

# Karpathy — LLM Wiki

**What it is:** an "idea file" (April 2026) meant to be pasted into an AI agent, which then builds a personal knowledge base with you. It came to Richard's attention via a discussion in the *AI in the NHS* group on 26 September 2026, where [Keith Grimes](../people/keith-grimes.md) reported six months of using it.

## Key points

- **Contrast with retrieval (RAG).** Tools like NotebookLM re-derive answers from raw documents on every question, so nothing accumulates. Here the LLM **compiles** each new source into a persistent, interlinked set of markdown pages. Cross-references and contradictions are worked out once and kept current.
- **Three layers:** raw sources (immutable), the wiki (written entirely by the LLM), and a schema file telling the agent the conventions.
- **Three operations:** *ingest* (one source may touch 10–15 pages), *query* (good answers are filed back as new pages), *lint* (contradictions, stale claims, orphan pages, gaps).
- **Two special files:** `index.md` (a catalogue the agent reads first) and `log.md` (a dated history).
- **Tooling:** Obsidian as the reader ("Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase"); the Obsidian Web Clipper for capture; git for history.
- **Why it works:** people abandon wikis because the bookkeeping grows faster than the value. An LLM makes that maintenance nearly free. Karpathy links it to Vannevar Bush's Memex (1945).

## Discussion in the comments (to September 2026)

Implementers report a consistent theme: **the hard part is trust, not retrieval**. They describe a compiled wiki becoming confidently wrong, and unsupported answers filed back in and later treated as sources. Mitigations include verifying quoted evidence against the cited file, keeping human-written sources separate from AI-written pages, citation checks computed in code, and human review before anything becomes "fact". One commenter asked whether anyone had benchmarked the "why this works" claims; no one had.

Related standard: Google's **Open Knowledge Format** (June 2026) formalises the pattern as markdown plus YAML frontmatter so that wikis are portable between tools — see [LLM-maintained knowledge bases](../topics/llm-maintained-knowledge-bases.md).
