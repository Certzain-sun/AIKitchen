# AIKitchen

SW Contest Programme

知味厨房：整桌菜单设计与协同烹饪调度 Android 应用。

当前状态（2026-11-17）：协作资料已初始化，Flutter 安卓基础工程已创建，并已在 Android 16 模拟器上编译、安装和启动。页面仍为默认计数器示例；业务前端、后端、数据库和调度尚未实现。示例数据仅用于接口和程序测试，不是实际菜谱指导。

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
- 每日复核、合并后共同运行一个样例。开发日程从11月18日开始，12月1日上午封版，当日展示初版。

手机端已采用 Flutter Android；后端建议使用 FastAPI/Python + OR-Tools + 单实例 SQLite，尚待组员实现。每台电脑需自行安装开发环境。

## 目录

`mobile/` 手机端；`server/api/` 接口；`server/db/` 数据；`server/planner/` 调度；`server/ai/` 模型；`data/` 共享样例；`tests/` 测试；`docs/` 共同约定。

不要把API密钥、本地数据库、成品照片原件和生成目录提交到仓库。配置参照 `.env.example`，在各自电脑上建立 `.env`。

## 最新开发进度与明日入口

本机正式开发目录为 D:\GitCode\AIKitchen；旧中文目录仅保留作备份。组员也请克隆到纯英文路径。运行方法见 mobile/README.md；今天的完成项、限制及明日任务见 docs/PROGRESS_2026-11-17.md。

人员统一以 A、B、C、D 标识：A手机端与整体验收；B接口和存储；C调度和做菜状态；D模型、菜谱与个性化。B、C、D按每天一个主要交付物安排，A略多承担联调与展示。详见 docs/TASK_BOARD.md。
