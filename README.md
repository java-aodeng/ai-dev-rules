# ai-dev-rules

这是一个只保留核心规则文件的开发规范仓库。

## 读取顺序

1. 先读 `rules/coding-standards.mdc`。
2. 如果需要项目命名和主开发范围，再读 `rules/project-naming.md`。

## 使用教程

- 把 `rules/` 文件夹放到你当前工作的项目目录下，比如 `D:\work\xxx\`。
- 让 AI 先读取 `rules/coding-standards.mdc` 再开始写代码，需要项目命名时再补读 `rules/project-naming.md`。

## 说明

- `rules/coding-standards.mdc` 里放通用编码规范、协作原则、前后端约定、输出格式和文件处理规则。
- `rules/project-naming.md` 只放项目与产品的匿名对应关系，不写真实项目名。
- 项目内 `AGENTS.md` 仍然优先于仓库规则。
