---
title: "Kodama Runtime Reading Notes"
date: 2026-06-09
summary: "A concise walkthrough of a lightweight coding-agent runtime from CLI entrypoint to the ask loop."
tags: ["Python", "LLM Agent", "Runtime"]
---

The core runtime path can be summarized as:

```text
cli.py -> build_agent -> Pico.ask()
-> ContextManager.build()
-> model_client.complete()
-> parse(<tool>/<final>)
-> run_tool()
-> trace / memory / checkpoint / report
```

This project is a good exercise for understanding agent runtime mechanics because it does not depend on LangChain, LangGraph, FastAPI, or MCP. It uses Python standard-library building blocks to implement model calls, tool protocols, context management, and run auditing.

While reading the code, I focused on three questions:

1. How model output is constrained into executable actions.
2. How tool execution is validated, audited, and bounded.
3. How multi-step work keeps continuity through history, memory, and checkpoints.
