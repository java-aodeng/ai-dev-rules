# ai-dev-rules

`ai-dev-rules` 是一套给多种 AI 编程助手共用的开发规范仓库。

## 仓库结构

```text
ai-dev-rules/
├── README.md                 # 仓库总说明
├── LICENSE                   # MIT 许可证
├── .gitignore                # Git 忽略规则
└── rules/                    # 通用规则区
    ├── coding-standards.mdc  # 通用编码规范与协作约定
    ├── project-naming.mdc    # 项目与产品对应关系
    └── local-overrides.mdc   # 本机私有配置文件，需要自己创建，创建教程见下方说明
```

## 如何使用

1. 把 `ai-dev-rules` 放到你的工作目录里，和业务项目同级。
2. 在 `ai-dev-rules/rules/` 目录下创建 `local-overrides.mdc`。
3. 在 `local-overrides.mdc` 里填写你的本机路径和项目映射。
4. 让 AI 读取 `ai-dev-rules/rules/coding-standards.mdc`、`ai-dev-rules/rules/project-naming.mdc` 和 `ai-dev-rules/rules/local-overrides.mdc`。

`local-overrides.mdc` 示例：

```md
# local-overrides.mdc

WORKSPACE_ROOT = 这个填你的工作目录 如：D:\work
RULES_ROOT = 这个填 ai-dev-rules 的 rules 目录 如：D:\work\ai-dev-rules\rules
MEMORY_DIR = 这个填你的会话记忆目录 如 D:\work\ai-dev-rules\memory

PROJECT_MAIN_NAME = 这个填你的主开发产品名称
PROJECT_MAIN_BACKEND = 这个填你的主产品后端仓库名
PROJECT_MAIN_ADMIN = 这个填你的主产品管理端仓库名
PROJECT_MAIN_H5 = 这个填你的主产品 H5 仓库名
PROJECT_MAIN_PARTNER_ADMIN = 这个填你的主产品伙伴端或合伙人端仓库名

PROJECT_REF_A_NAME = 这个填你的第一个参考产品名称
PROJECT_REF_A_BACKEND = 这个填第一个参考产品后端仓库名
PROJECT_REF_A_ADMIN = 这个填第一个参考产品管理端仓库名

PROJECT_REF_B_NAME = 这个填你的第二个参考产品名称
PROJECT_REF_B_BACKEND = 这个填第二个参考产品后端仓库名
PROJECT_REF_B_ADMIN = 这个填第二个参考产品管理端仓库名
```

`rules/local-overrides.mdc` 已在 `.gitignore` 中忽略，可以直接写真实值，不会提交到开源仓库。

## License

MIT
