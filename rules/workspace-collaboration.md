# Workspace Collaboration

## Main Project vs Reference Projects

- 当工作区里同时存在多个项目时，先明确一个主项目。
- 默认只在主项目内写文件，其他项目只做只读参考。
- 未经明确要求，不要把参考项目当成默认写入目标。

## Search Discipline

- 默认只看当前需求相关的文件或目录，不做整仓库递归扫描。
- 优先按文件路径精确读取，再顺着直接引用向外看一层。
- 搜索和遍历时默认排除 `.git`、`.idea`、`.vscode`、`node_modules`、`dist`、`target`、`build`、`.cache`。

## Dependency and Install Policy

- 所有“拉包 / 安装 / 下载依赖”命令都不主动执行，只给可直接复制的命令。
- 包括但不限于 `npm install`、`pnpm install`、`yarn install`、`mvn install`、`pip install`、`poetry install`、`go mod download`、`cargo fetch`、`docker pull`。
- 如果任务必须依赖下载，先停止并给出命令，不要绕过限制。
- 不要在仓库里随手创建本地依赖缓存目录。

## Validation and Tests

- 默认不主动新增或修改单元测试，除非用户明确要求。
- 需求开发阶段默认先完成改动，不做大而全检查。
- 后端单个模块改动较大时，收尾提醒执行 `mvn checkstyle:check -X`，但不要代执行。

## SQL and File Output

- 新增 SQL 统一追加到目标文件末尾，不插入到中间。
- `INSERT` / `UPDATE` / `DELETE` 这类简单语句优先写成单行。
- `CREATE TABLE` / `ALTER TABLE` 等复杂 DDL 按可读性正常换行。
- 无论简单 DML 还是复杂 DDL，都遵循“只在文件末尾追加”的原则。
- 输出时优先先给结论，再给细节。
- 改动汇报使用 `1. 2. 3.` 编号列表。
- 引用代码位置时使用 `文件:行号`。
- 单次输出默认不要太长，必要时分批说明。

## Path and Link Format

- 如果需要给出可点击路径，优先使用绝对路径并带行号。
- 不要返回会跳浏览器的路径形式。
- 如果工具链支持本地文件跳转，尽量让路径能直接打开到编辑器。