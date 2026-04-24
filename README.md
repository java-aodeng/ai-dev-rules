# ai-dev-rules

`ai-dev-rules` 是一套给多种 AI 编程助手共用的开发规范仓库。

它的目标不是“教 AI 聊天”，而是把你已经验证过的开发习惯固化成一套可以复用、可以扩展、可以给不同工具读取的规则库。

## 这套仓库解决什么问题

- 让 Codex、Cursor、Claude、Copilot、ChatGPT 等都能读懂同一套开发规则
- 把通用规则、项目命名规则拆成独立文件
- 保留项目内 `AGENTS.md` 的优先级，作为局部覆盖层
- 避免把规则绑死在某一个项目名或某一个 AI 平台上

## 仓库结构

```text
ai-dev-rules/
├── README.md                 # 仓库总说明
├── LICENSE                   # MIT 许可证
├── .gitignore                # Git 忽略规则
└── rules/                    # 通用规则区
    ├── coding-standards.mdc  # 通用编码规范与协作约定
    └── project-naming.mdc    # 项目与产品对应关系
```

## 如何使用

1. 先读 `rules/coding-standards.mdc`。
2. 如果需要项目命名和主开发范围，再读 `rules/project-naming.mdc`。
3. 把 `rules/` 文件夹放到你当前工作的项目目录下，比如 `D:\work\xxx\`。
4. 让 AI 先读取 `rules/coding-standards.mdc` 再开始写代码，需要项目命名时再补读 `rules/project-naming.mdc`。
5. 如果某个项目有自己的 `AGENTS.md`，以项目内规则为准。

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

- `LICENSE`：开源许可说明
- `.gitignore`：Git 忽略规则

## License

MIT
