# AIKitchen

SW Contest Programme

知味厨房：整桌菜单设计与协同烹饪调度 Android 应用。

当前状态：协作资料和目录已初始化，尚无可运行APP、后端或调度实现。示例数据仅用于接口和程序测试，不是实际菜谱指导。

## 四个人先读什么

1. `PROJECT_CONTEXT.md`：共同目标、范围和角色。
2. `docs/API_CONTRACT.md`：模块怎样连接。
3. `docs/DATA_SCHEMA.md`：数据含义和单位。
4. `docs/TEAM_WORKFLOW.md`：提交、复核、合并和每日联调。
5. `docs/AI_TASK_PROMPTS.md`：分别给自己的AI使用的任务提示。
6. `docs/TASK_BOARD.md`：认领当天任务并更新实际进展。

最终计划书保存在 `docs/reference/知味厨房最终计划书.docx`，保留原文件内容。

## 今天怎么开始

- 每人接受仓库邀请并克隆同一个仓库。
- 更新到这次初始化提交，再让自己的AI阅读公共文件。
- 在自己的模块分支工作，每次提交一个可检查的小任务。
- 每日复核、合并后共同运行一个样例。按计划目标于11月30日封版，12月1日展示初版。

建议路线为 Flutter Android + FastAPI/Python + OR-Tools + 单实例SQLite演示；启动会确认后固定，当前没有安装任何依赖。

## 目录

`mobile/` 手机端；`server/api/` 接口；`server/db/` 数据；`server/planner/` 调度；`server/ai/` 模型；`data/` 共享样例；`tests/` 测试；`docs/` 共同约定。

不要把API密钥、本地数据库、成品照片原件和生成目录提交到仓库。配置参照 `.env.example`，在各自电脑上建立 `.env`。
