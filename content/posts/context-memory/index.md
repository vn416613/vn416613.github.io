---
title: "上下文管理与工作记忆学习记录"
date: 2026-06-09
summary: "记录 ContextManager 如何把 prefix、memory、history 和当前请求压缩进 prompt。"
tags: ["Prompt", "Memory", "Context"]
---

Pico 的 ContextManager 会将 prompt 拆分为：

- `prefix`
- `memory`
- `relevant_memory`
- `history`
- `current_request`

其中当前用户请求不会被裁剪，旧历史会被压缩，重复读文件记录会复用文件摘要。这种设计可以帮助 Agent 在长对话和多步任务中保持稳定。

这部分给我的启发是：Agent 的效果不只取决于模型能力，也取决于运行时如何组织上下文。合理的上下文预算、旧信息压缩和最新请求保护，往往比单纯堆长 prompt 更可靠。
