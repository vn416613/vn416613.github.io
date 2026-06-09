---
title: "Context Management and Working Memory Notes"
date: 2026-06-09
summary: "Notes on how the context manager compresses prefix, memory, history, and the current request into a usable prompt."
tags: ["Prompt", "Memory", "Context"]
---

The context manager divides each prompt into several sections:

- `prefix`
- `memory`
- `relevant_memory`
- `history`
- `current_request`

The latest user request is preserved, older history can be compressed, and repeated file reads can reuse file summaries. This design helps an agent remain stable during long conversations and multi-step tasks.

The key takeaway is that agent quality does not only depend on the model. It also depends on how the runtime organizes context. A careful budget strategy, old-context compression, and current-request protection can be more reliable than simply sending a longer prompt.
