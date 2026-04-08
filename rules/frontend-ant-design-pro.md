# Frontend Ant Design Pro Rules

## Generated APIs

- 接口与类型一律通过 `npm run openapi` 生成。
- 禁止手改生成物：
  - `services/ant-design-pro/*Controller.ts`
  - `typings.d.ts` 里的 API 类型
- 后端接口改动后，先同步生成，再改前端调用。

## Request Types

- 请求参数、表单提交值优先复用生成的 `API.xxxReq`。
- 字段一致时，表单提交直接透传 `values`。
- 不要再手写重复类型。

## Enums

- 枚举优先由后端接口下发。
- 只有后端没有对应枚举时，才允许前端兜底写死。

## Error Handling

- 用户触发的接口调用需要统一错误提示。
- 页面层如需定制化异常交互，再局部补充处理逻辑。
- 默认不重复写一层冗余 `catch`。

## Permissions

- 一个按钮或操作只绑定一个明确权限点。
- 禁止用多个权限做兜底放宽显示条件。

