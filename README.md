# ai-dev-rules

`ai-dev-rules` 是一套给多种 AI 编程助手共用的开发规范仓库。

它的目标不是“教 AI 聊天”，而是把你已经验证过的开发习惯固化成一套可以复用、可以扩展、可以给不同工具读取的规则库。

## 这套仓库解决什么问题

- 让 Codex、Cursor、Claude、Copilot、ChatGPT 等都能读懂同一套开发规则
- 把全局指令、编码规范、输出格式、项目模板拆成独立文件
- 保留项目内 `AGENTS.md` 的优先级，作为局部覆盖层
- 避免把规则绑死在某一个项目名或某一个 AI 平台上

## 仓库结构

```text
ai-dev-rules/
├── README.md                 # 仓库总说明
├── CONTRIBUTING.md           # 贡献指南
├── LICENSE                   # MIT 许可证
├── SECURITY.md               # 安全问题报告方式
├── CHANGELOG.md              # 版本变化记录
├── docs/                     # 文档区：快速开始、FAQ、路线图、决策记录
│   ├── roadmap.md            # 路线图
│   ├── quick-start.md        # 快速开始
│   ├── faq.md                # 常见问题
│   └── decision-log.md       # 设计决策记录
├── examples/                 # 真实项目接入示例
│   ├── HOW_TO_APPLY.md       # 通用接入步骤
│   ├── java-backend/         # Java 后端示例
│   │   └── README.md         # 后端接入说明
│   └── frontend-admin/       # 前端管理端示例
│       └── README.md         # 前端接入说明
├── rules/                    # 通用规则区
│   ├── core.md               # 通用协作与输出规则
│   ├── backend-java.md       # Java 后端规则
│   ├── frontend-ant-design-pro.md # Ant Design Pro 前端规则
│   ├── project-template.md   # 项目规则模板
│   └── project-naming.md     # 项目与产品对应关系
└── adapters/                 # 平台适配层
    └── codex/                # Codex 适配层
        ├── SKILL.md          # Codex 适配说明
        └── agents/           # Codex 的 UI 元数据
            └── openai.yaml   # UI 配置
```

## 如何使用

1. 先读 `docs/quick-start.md`。
2. 再按技术栈读对应规则：
   - Java 后端读 `rules/backend-java.md`
   - Ant Design Pro 前端读 `rules/frontend-ant-design-pro.md`
   - 需要项目命名说明时读 `rules/project-naming.md`
3. 如果某个项目有自己的 `AGENTS.md`，以项目内规则为准。
4. 如果要给某个具体仓库落地，参考 `examples/HOW_TO_APPLY.md`。
5. 如果你在 Codex 中使用，读 `adapters/codex/SKILL.md`。
6. 有疑问时，先看 `docs/faq.md`。

## 设计原则

- 不绑定单一 AI 平台
- 不保留具体业务项目名
- 保留规则意图，不保留无关示例
- 规则尽量短、明确、可执行
- 通用规则和项目规则分层管理

## 适合谁用

- 想把自己的编码习惯固定下来的人
- 想让多个 AI 工具遵守同一套开发规范的人
- 想把项目内约定沉淀成可复用规则的人

## 其他基础件

- `SECURITY.md`：安全问题的报告方式和处理范围
- `CHANGELOG.md`：后续版本变化记录
- `docs/roadmap.md`：项目里程碑和发布节奏
- `docs/quick-start.md`：最短接入方式
- `docs/faq.md`：常见问题说明
- `docs/decision-log.md`：设计取舍记录
- `examples/HOW_TO_APPLY.md`：通用接入步骤
- `examples/java-backend/README.md`：Java 后端接入示例
- `examples/frontend-admin/README.md`：前端管理端接入示例

## License

MIT