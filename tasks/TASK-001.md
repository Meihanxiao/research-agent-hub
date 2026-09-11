# TASK-001：检查仓库协作流程

- ID: TASK-001
- Type: review
- Goal: 检查规则与模板能否支持一次可追溯的跨平台任务闭环。
- Context: AGENTS.md、PROJECT_CONTEXT.md、RESEARCH_STATE.md、DECISIONS.md、agents/review.md、skills/acceptance.md
- Inputs: Codex总Agent实现说明.md、README.md、TASK_TEMPLATE.md、skills/handoff.md、skills/report.md、.github/ISSUE_TEMPLATE/task.md、.github/pull_request_template.md
- Constraints: 仅新增 outputs/TASK-001/ 下文件；不修改被审查文件；无法确认的内容明确标为待验证。
- Required Output: outputs/TASK-001/review.md 和 outputs/TASK-001/report.md
- Acceptance Criteria:
  - [ ] 对照原始说明逐项检查九个任务字段、五类角色、手动分发及状态回写。
  - [ ] 每个发现有文件位置、问题描述和具体建议；无问题也列出检查证据。
  - [ ] 检查无仓库权限、上下文不足、验收不通过三种情形的处理流程。
  - [ ] 报告区分文件审查和真实运行验证，不虚构 GitHub 操作。
- Deliver To: https://github.com/Meihanxiao/research-agent-hub；基准分支待确认；Issue 待创建；outputs/TASK-001/

## 交接记录

- 执行方：待用户指定
- 任务分支：task/TASK-001-workflow-review
- 基准提交：发布后填写；未填写前不分发
- PR：待提交
