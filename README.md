# research-agent-hub

以 Codex 为总 Agent、GitHub 为统一上下文与任务中心，通过手动分发、PR 交付和验收管理跨平台科研 Agent 协作。

## 开始工作

1. 在设备上克隆或同步本仓库；存在未提交改动时先处理，不覆盖本地工作。
2. 让 Codex 读取 AGENTS.md、PROJECT_CONTEXT.md、RESEARCH_STATE.md 和 DECISIONS.md。
3. 告诉 Codex 当前目标，由它按照 TASK_TEMPLATE.md 建立任务文件。
4. 将任务说明、指定上下文及基准提交转发给另一平台 Agent。
5. 将 PR 链接带回 Codex，对照验收标准 review。
6. 合并产物后更新 RESEARCH_STATE.md；全部记录完成才关闭任务。

启动提示：请按 AGENTS.md 恢复项目状态，汇报当前任务、阻塞项和下一步，再执行已明确授权的工作。

## 文件入口

- PROJECT_CONTEXT.md：长期背景与边界。
- RESEARCH_STATE.md：当前进度和证据链接。
- DECISIONS.md：决策及理由。
- TASK_TEMPLATE.md、tasks/：统一任务说明。
- agents/：五类平台无关角色。
- skills/：手动引用的操作清单，不假定平台自动加载。
- outputs/：按任务编号保存产物。
- .github/：PR 模板（历史 Issue 模板及 labels 清单不再使用）。

第一版不包含自动平台 API/MCP 调度或常驻服务。GitHub 登录通过设备自身完成，凭证不放入仓库。
