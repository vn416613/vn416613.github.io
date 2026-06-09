---
title: "Pico Agent Runtime 源码阅读笔记"
date: 2026-06-09
summary: "从 CLI 入口到 Pico.ask() 主循环，梳理一个轻量级 Coding Agent 的运行机制。"
tags: ["Python", "LLM Agent", "Runtime"]
---

Pico 的核心链路可以概括为：

```text
cli.py -> build_agent -> Pico.ask()
-> ContextManager.build()
-> model_client.complete()
-> parse(<tool>/<final>)
-> run_tool()
-> trace / memory / checkpoint / report
```

这个项目适合作为理解 Agent Runtime 底层机制的练习项目，因为它没有依赖 LangChain、LangGraph 或 MCP，而是直接用 Python 标准库实现模型调用、工具协议、上下文管理和运行审计。

阅读这个项目时，我重点关注三个问题：

1. 模型输出如何被限制成可执行动作。
2. 工具执行前后如何做安全校验和审计记录。
3. 多轮任务如何通过 history、memory 和 checkpoint 保持连续性。
