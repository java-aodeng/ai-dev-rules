# Java 后端接入示例

这是一个示例，展示如何把 `ai-dev-rules` 接入到真实的 Java 后端项目里。

## 示例目标

把通用规则落到一个典型的 Java 后端项目中，让 AI 在开发时先遵守通用规则，再遵守项目自己的规则。

## 你需要做什么

### 1. 在仓库根目录放一个 `AGENTS.md`

项目自己的规则优先级更高，所以先把项目专属约定写进去。

示例：

```md
# AGENTS.md

- 以本项目规则为准
- Controller 只接 apps 层 Req/Resp
- 禁止新增 Swagger 注解
- 分页优先 XML
- 先读项目结构，再开始改动
```

### 2. 把通用规则作为参考挂进来

做法有两种：

- 直接把 `ai-dev-rules/rules/*.md` 复制到项目里
- 或者把它作为外部参考仓库，在 AI 任务里先让模型读通用规则，再读项目规则

### 3. 在项目里保留自己的技术栈规则

如果项目是 Java 后端，优先再放一份自己的后端约定，例如：

- 应用分层
- 包结构
- 实际的 DTO / Req / Resp 命名
- 数据库和分页约定

### 4. 让 AI 按顺序读取

推荐顺序：

1. 读 `ai-dev-rules/rules/core.md`
2. 读 `ai-dev-rules/rules/backend-java.md`
3. 读项目根目录的 `AGENTS.md`
4. 再开始改代码

## 最小接入示例

```text
project/
├── AGENTS.md
├── backend/
│   ├── apps/
│   ├── core/
│   └── commons/
└── ai-dev-rules/
    ├── rules/
    └── adapters/
```

## 适合什么场景

- 你想让 AI 在每个项目里都按同一套开发习惯工作
- 你想把自己的编码规范沉淀成可复用规则
- 你想先看一个示例，再决定怎么把它接到自己的仓库
