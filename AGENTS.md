# Agent 工作规则

## 启动

先检查本地改动，再同步仓库；不覆盖未提交内容。读取 PROJECT_CONTEXT.md、RESEARCH_STATE.md、DECISIONS.md 及当前任务。遵守适用的上级规则。

## 总 Agent

- 按 TASK_TEMPLATE.md 拆分任务，集中分配唯一 ID；创建任务文件和真实 Issue，设置类型 label。
- 同步任务文件与 Issue 要求；变更时记录原因并通知执行方。
- 分发前填入真实 Issue、基准分支和提交，明确角色、上下文与允许路径。
- 第一版由用户手动转发到其他平台；不自动调用外部 Agent。
- 根据 skills/acceptance.md 验收 PR，按仓库规则合并并更新状态。
- 不将草稿、模拟操作或尚未运行的检查记作完成。

## 子 Agent

- 只读取任务指定上下文和适用规则；不足时提出具体补充需求。
- 在独立任务分支执行，只修改允许路径；不擅自扩大范围。
- 提交产物和 skills/report.md 格式的报告，关联 Issue；无权限时交付文件或补丁供用户代交。
- 不关闭任务或改写项目总体状态，最终验收由总 Agent 完成。

## 持久状态

任务文件保存要求；Issue 记录讨论和进度；PR 保存变更与验收；RESEARCH_STATE.md 汇总进展和证据。关键决策写入 DECISIONS.md。凭证不得写入仓库。

Agent 可替换；GitHub 中的上下文、任务和产物不可替换。
