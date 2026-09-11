# Codex 总 Agent 实现说明

请按以下需求实现可运行的最小版本，优先完成一次任务闭环。

## 1. 项目目标与边界

- Codex 作为总 Agent，负责规划、分发和验收；其他平台 Agent 执行子任务。
- GitHub 作为 control plane（协调中心）和 single source of truth（唯一事实来源），保存上下文、任务、状态和产物。
- 支持在本设备或其他设备继续工作：先同步仓库并读取状态，不依赖某个聊天窗口的记忆。
- 第一版采用手动路由：Codex 生成任务说明，由用户转发给指定平台 Agent；不实现自动 API、MCP 或 multi-agent 聊天。

## 2. MVP 架构

```text
Codex 总 Agent
  → GitHub Issues / Repo / PR
  → 用户手动转发任务给子 Agent
  → 子 Agent 执行并回写 PR / 结果
  → Codex 验收
  → 更新仓库状态
```

## 3. 最小仓库结构与职责

```text
AGENTS.md
PROJECT_CONTEXT.md
RESEARCH_STATE.md
DECISIONS.md
TASK_TEMPLATE.md
agents/
skills/
tasks/
outputs/
```

| 路径 | 职责 |
| --- | --- |
| `AGENTS.md` | 总 Agent 与子 Agent 的工作规则、执行流程、权限边界及验收要求。 |
| `PROJECT_CONTEXT.md` | 项目目标、研究背景、范围、约束和术语；保存稳定上下文。 |
| `RESEARCH_STATE.md` | 当前进展、任务 ID、Issue/PR 链接、阻塞项和下一步；每次验收后更新。 |
| `DECISIONS.md` | 记录关键决策、日期、理由及关联任务。 |
| `TASK_TEMPLATE.md` | 保存统一任务模板，供任务文件和 Issue 正文复用。 |
| `agents/` | 按任务类型定义角色、输入要求、输出要求和适用平台；角色不绑定单一产品。 |
| `skills/` | 保存可复用操作流程与检查清单；任务按需引用。 |
| `tasks/` | 每个任务保存为 `<ID>.md`，记录完整任务说明及 Issue/PR 引用。 |
| `outputs/` | 保存可交付产物，按任务 ID 分目录；大型产物保存持久链接及说明。 |

## 4. 统一 Task Schema

在 `TASK_TEMPLATE.md` 中提供以下模板，所有任务字段必须填写：

```markdown
# <ID>：<简短标题>

- ID: 唯一标识，例如 TASK-001
- Type: literature | coding | review | presentation | openfoam
- Goal: 单一、明确且可验证的目标
- Context: 必读文件路径、具体章节及必要背景
- Inputs: 输入文件、数据或链接
- Constraints: 范围、允许修改的路径、工具及时间等限制
- Required Output: 产物类型、文件名和存放路径
- Acceptance Criteria:
  - 可逐项检查的完成条件
- Deliver To: 目标仓库、基准分支、Issue 链接和产物路径
```

以 Issue 的打开/关闭状态及关联 PR 表示执行进度；任务要求变更时，同步 Issue 正文与 `tasks/<ID>.md`，避免冲突版本。

## 5. Codex 总 Agent 工作流程

1. 同步仓库，读取 `AGENTS.md`、项目上下文、当前状态和相关决策。
2. 将目标拆成边界清晰、可独立验收的任务；标明依赖关系。
3. 根据模板创建任务文件和 GitHub Issue，分配唯一 ID 与类型 label。
4. 根据 `agents/` 选择角色，输出可直接转发的任务说明，包含 Issue 链接和指定上下文。
5. 收到 PR 后，对照 Acceptance Criteria 检查产物并完成 review；未通过时提出具体修改项。
6. 验收通过后按仓库权限与合并规则合并 PR、关闭 Issue，更新 `RESEARCH_STATE.md`；涉及关键决策时更新 `DECISIONS.md`。

## 6. 子 Agent 协议

1. 读取适用的仓库规则及任务指定上下文；需要补充信息时在报告中明确提出，不擅自扩展任务。
2. 在独立任务分支执行，只修改任务允许的路径。
3. 按 Required Output 生成 artifact，执行必要验证。
4. 提交关联 Issue 的 PR，报告完成内容、产物路径、验证结果、限制与待解决问题。
5. 无 GitHub 写入能力时，交付文件或补丁及报告，由用户代为提交 PR；闭环仍必须经过 PR 验收。
6. 不自行宣布整项研究完成；任务最终验收由 Codex 总 Agent 执行。

## 7. GitHub labels

创建任务类型 labels：`literature`、`coding`、`review`、`presentation`、`openfoam`。每个 Issue 至少设置一个类型 label。

## 8. 实施交付与 MVP 验收

- 创建上述目录、关键文件、任务模板和五类角色说明；内容须可直接使用。
- 配置任务类型 labels，并准备一个规模小、能实际执行的示例任务。
- 完成一次真实闭环：**Codex 创建 Issue → 用户转发 → 另一个 Agent 执行 → 提交 PR → Codex review → 合并并更新 RESEARCH_STATE**。
- 验收证据必须包含 Issue、PR、review 记录、产物路径及状态更新提交；不能以模拟记录代替。
- 在另一设备或新会话同步仓库后，应能从 `RESEARCH_STATE.md` 找到当前进度、相关产物与下一步。
- 若缺少仓库地址、权限或子 Agent 交付，先完成本地可执行文件，再明确列出闭环尚缺的实际步骤。

## 9. 核心原则

**Agent 可替换；GitHub 中的上下文、任务和产物不可替换。** 所有影响后续执行的信息必须回写仓库或关联 Issue/PR，不得只保留在聊天记录中。
