---
name: ai-dev-rules-codex
description: 当你在 Codex 中工作，并且需要套用 ai-dev-rules 的通用开发规范、分层 Java / Ant Design Pro 规则、输出约定和工作区协作约定时使用。
---

# ai-dev-rules Codex 适配层

当你在 Codex 中工作，并且这项任务应该遵守 `ai-dev-rules` 的共享规范时，使用这个适配层。

## 读取顺序

1. 先读 `../../rules/core.md`
2. 再读对应技术栈规则：
   - `../../rules/backend-java.md`
   - `../../rules/frontend-ant-design-pro.md`
3. 如果需要工作区协作、输出或 SQL 约定，再读 `../../rules/workspace-collaboration.md`
4. 如果目标项目有 `AGENTS.md`，先遵守项目文件
5. 如果需要项目模板，再读 `../../rules/project-template.md`

## 工作原则

- 保持改动尽量小，并和共享规则一致
- 不覆盖项目自己的专属说明
- 除非任务确实需要，否则保持仓库原有风格
- 在做结构性改动之前，优先先解释清楚再动手