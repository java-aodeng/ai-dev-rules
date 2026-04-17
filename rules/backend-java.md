# Backend Java Rules

## Scope

- 适用于 Java 后端服务的 Controller、AppService、Core Service、Repository 和 XML 映射。
- 目标是把 HTTP 契约、领域规则、持久层和返回组装分开，避免把业务和查询逻辑混在一起。

## Layering

- Controller：接收、校验、调用、返回。
- AppService：用例编排、响应组装。
- Core Service：业务规则、状态变更。
- Repository：仅数据访问。
- 依赖方向：`apps -> core -> commons`，禁止反向依赖。
- Controller 不直接访问 Repository，也不承载业务规则。

## HTTP Contract

- Controller 对外契约只使用 apps 层 `*Req/*Resp`。
- 禁止 Controller 直接暴露 core DTO 或 entity。
- 分页 / 筛选优先使用 `@Validated XxxReq req`。
- `@PathVariable("id")` 必须显式命名。
- 方法名用“动作 + 资源”，同一应用内保持语义唯一。
- 禁止新增 Swagger 注解，保留 SpringDoc。
- 改接口后，检查 `GET /v3/api-docs`，确保没有 `arg0`，`operationId` 也不要出现编号后缀。

## AppService Mapping

- AppService 负责用例编排和响应组装，不写 SQL。
- `buildQuery()` 用来把 Req 转成 core 查询对象。
- `toResp()`、`toPageItemResp()` 这类方法只做数据映射，不写领域规则。
- 如果只是列表或分页查询，不要再额外包一层重复的 Core Service 方法。

## Persistence

- 统一使用 MyBatis + MyBatis-Plus。
- 禁止使用 JPA / Hibernate。
- 多条件、排序、联表、统计、分页查询优先写 XML。
- 分页统一使用 `Page<T>`，首参固定为 `Page<T> page`。
- 更新优先定向 SQL，避免整对象回写。
- 业务主键使用雪花 ID。
- 复杂查询参数统一使用 `@Param("param")`。
- Repository 中不要用 `selectPage(page, Wrappers.lambdaQuery()...)` 这种把条件塞进代码里的写法。
- XML 中使用 `param.xxx` 时要有空判断，避免 NPE。

## Admin Pagination Pattern

- 管理端列表的 Req、Resp 放在 apps 层。
- core 只提供查询对象和 Repository / XML 映射用 DTO。
- AppService 通过 Req 的查询构造对象后再调用 Repository。
- `Page<T> page = new Page<>(query.getCurrent(), query.getPageSize())` 后再调用 `pageByQuery(page, query)`。
- 将 `result.getRecords()` 映射为 apps 层 `*PageItemResp` 后再封装分页返回。
- 如果只是分页查询，不额外包一层重复的 Service 方法。
- core DTO 名称不要和 apps 层 `*Resp` 重名。

## Naming

- 新建对外契约类型使用 `Req` / `Resp` 后缀。
- 禁止弱语义命名，如 `Data`、`Result`、`Res`。
- 新增对外契约不使用 `Vo` 风格。
- 类名中的 DTO 缩写统一写作 `Dto`。
- 分页列表命名优先 `pageByQuery`；仅在单一维度分页时用 `selectByXxxPage`。
- 联表行视图可使用 `pageByQueryWithDetails` 这类清晰命名。

## Style

- 4 空格缩进。
- 禁止 wildcard import。
- 方法尽量不超过 150 行。
- Java 注入仅使用 `@Resource` 字段注入。
- `@Resource` 单独一行，写在字段上方。
- 禁止 `@Autowired`、`@Inject`、`@RequiredArgsConstructor` 作为默认注入方式。
- 注释只保留复杂逻辑或坑点说明。
- 能一行写完的代码优先一行写完，超过行宽再换行。
- 第三方接口的请求和返回日志，默认合并为同一条日志，减少噪音。

## Review Checklist

- Controller 的入参和出参是否只用 apps 层 Req / Resp。
- 是否有 core DTO / entity 直接暴露到 HTTP 层。
- 新增查询是否优先落在 XML，而不是在 Java 里拼条件。
- 是否存在整对象回写，可以改成定向 SQL。
- DTO 命名是否与 apps 层 Resp 冲突。
- 如果改动较大，收尾时提醒执行 `mvn checkstyle:check -X`。