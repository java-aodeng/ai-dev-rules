# Backend Java Rules

## Layering

- Controller：接收、校验、调用、返回。
- AppService：用例编排、响应组装。
- Core Service：业务规则、状态变更。
- Repository：仅数据访问。
- 依赖方向：`apps -> core -> commons`，禁止反向依赖。

## HTTP Contract

- Controller 对外契约只使用 apps 层 `*Req/*Resp`。
- 禁止 Controller 直接暴露 core DTO 或 entity。
- 分页 / 筛选优先使用 `@Validated XxxReq req`。
- `@PathVariable("id")` 必须显式命名。
- 方法名用“动作 + 资源”，同一应用内保持语义唯一。
- 禁止新增 Swagger 注解，保留 SpringDoc。

## Persistence

- 统一使用 MyBatis + MyBatis-Plus。
- 禁止使用 JPA / Hibernate。
- 多条件、排序、联表、统计、分页查询优先写 XML。
- 分页统一使用 `Page<T>`。
- 更新优先定向 SQL，避免整对象回写。
- 业务主键使用雪花 ID。
- 复杂查询参数统一使用 `@Param("param")`。

## Naming

- 新建对外契约类型使用 `Req` / `Resp` 后缀。
- 禁止弱语义命名，如 `Data`、`Result`、`Res`。
- 新增对外契约不使用 `Vo` 风格。
- 类名中的 DTO 缩写统一写作 `Dto`。
- 管理端列表分页命名优先 `pageByQuery`，单一维度再用 `selectByXxxPage`。
- core DTO 名称不要和 apps 层 `*Resp` 重名。

## Style

- 4 空格缩进。
- 禁止 wildcard import。
- 方法尽量不超过 150 行。
- Java 注入仅使用 `@Resource` 字段注入。
- `@Resource` 单独一行，写在字段上方。
- 注释只保留复杂逻辑或坑点说明。
- 能一行写完的代码优先一行写完，超过行宽再换行。

## Admin Pagination Pattern

- 管理端列表的 Req、Resp 放在 apps 层。
- core 只提供查询对象和 Repository / XML 映射用 DTO。
- AppService 通过 Req 的查询构造对象后再调用 Repository。
- 如果只是分页查询，不额外包一层重复的 Service 方法。
- 查询对象统一通过 `buildQuery()` 组装。
- `Page<T> page = new Page<>(query.getCurrent(), query.getPageSize())` 后再调用 Repository。
- 若只是主键或极简单条件查询，才允许不放进 XML。