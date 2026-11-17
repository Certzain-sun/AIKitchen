# 首版接口契约草案

版本0.1；尚未实现。由B维护，A、C、D在11月19日前共同确认。字段变化需一起更新样例与调用方。

## 统一约定

前缀 `/api/v1`；JSON；时间ISO 8601含时区，内部排程相对秒数；时长秒；金额整数分、币种CNY。登录方式由B确定并补写，不在请求正文信任用户ID；服务端根据认证确定所属用户。

成功响应包含 `data`、`request_id`；错误响应包含 `error.code`、`error.message`、`error.details`、`request_id`。支持字段缺失、条件不满足、旧版本冲突和模型失败等明确错误。

## 端点

| 方法与路径 | 输入 | 输出与负责人 |
|---|---|---|
| GET /health | 无 | 服务状态；B |
| POST /menus/propose | request_text、人数、预算、场合、resources、available_from、serve_at、已确认偏好 | D提议菜单，C检查可行性，B组织与保存；返回菜品、费用依据、缺失信息、校验状态 |
| POST /plans | 已确认菜品/任务、resources、available_from、serve_at | C排程，B持久化；plan_id、schedule_version、solver_status、tasks、issues |
| GET /sessions/{id} | 路径ID | 本人会话、当前版本、实际事件与计划；B |
| POST /sessions/{id}/events | event_id、expected_version、task_id、type、occurred_at、remaining_sec（如适用） | B去重和保存，C重排；新版本、实际状态、计划与变更原因 |

偏好、校准、反馈、照片等由B与手机端按P1任务补充独立端点，不各自猜测命名。

`expected_version`过期返回409；重复`event_id`不重复执行。事件只写入本人会话，需校验前置任务和资源状态。后台模型或求解失败时不覆盖上一份有效计划。

## 结果含义

`solver_status`保留OPTIMAL、FEASIBLE、INFEASIBLE、UNKNOWN、MODEL_INVALID。只对有解状态返回可执行计划；无解、超时、输入错误分别解释。无法证明的瓶颈标成诊断建议，不伪造求解证明。

示例 `data/demo_cases.json` 为手工测试数据，含已手工核对的可行安排；它不是已实现接口的返回结果，也不是求解器输出。

## 职责边界

B维护HTTP入口、认证、事务、通用存储及部署；C提供排程、做菜状态转换、剩余时长更新和重排模块；D提供需求理解、菜单、采购与预算解释、偏好及历史推荐业务模块。B负责接入模块，避免重复实现业务。A负责手机交互、计时展示及整体验收。偏好等P1接口由B、D与A共同确认字段，做菜事件由B、C与A共同确认语义。
