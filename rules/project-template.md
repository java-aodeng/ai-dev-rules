# Project Template

## How to Adapt

把下面占位符替换成当前项目的真实信息：

- `<current-project>`：当前项目名
- `<current-admin-app>`：当前管理端应用名
- `<current-h5-app>`：当前 H5 应用名
- `<current-backend-module>`：当前后端模块名

## Project-Specific Override

- 先继承 `rules/core.md`
- 再按技术栈继承 `rules/backend-java.md` 或 `rules/frontend-ant-design-pro.md`
- 如果项目内 `AGENTS.md` 与本模板冲突，以项目内文件为准

## Recommended Local Additions

- 项目自己的命名约定
- 项目自己的接口前缀与目录结构
- 项目自己的检查命令
- 项目自己的禁用项
- 项目自己的主开发范围说明

## Example Structure

```text
project/
├── AGENTS.md
├── backend/
│   ├── apps/
│   ├── core/
│   └── commons/
└── frontend/
    ├── src/
    └── services/
```