# TASK-001：可直接转发的执行说明

请作为 review 子 Agent，审查 research-agent-hub 的任务协议与协作流程。

- 仓库：https://github.com/Meihanxiao/research-agent-hub
- 基准提交：229ba2dbbfaae87783d58bc5863e3dc26c5b3f4a
- 任务定义：tasks/TASK-001.md；本交接说明补齐该任务的精确基准。
- 分支：从上述基准创建 task/TASK-001-workflow-review。
- 最新决定：用户已取消 Issue，不要求创建 Issue 或 labels。保留任务文件、手动路由、PR 与验收。
- 只允许新增 outputs/TASK-001/review.md 和 outputs/TASK-001/report.md。
- 完成后向 main 提交 PR，在说明中关联 TASK-001 和任务文件；不要自动合并或改写项目总体状态。
- 若不能创建 PR，请交付这两个完整 Markdown 文件或补丁，由用户带回总 Agent 代交。
- 不得把文件审查描述为已实际运行跨平台闭环；无需访问任务之外的文件。

以下附上基准版本所需上下文。无法访问 GitHub 时可直接据此审查；提交到仓库仍需由有权限的一方执行。

## 文件：AGENTS.md

~~~~markdown
# Agent 工作规则

## 启动

先检查本地改动，再同步仓库；不覆盖未提交内容。读取 PROJECT_CONTEXT.md、RESEARCH_STATE.md、DECISIONS.md 及当前任务。遵守适用的上级规则。

## 总 Agent

- 按 TASK_TEMPLATE.md 拆分任务，集中分配唯一 ID；创建任务文件，用 Type 字段标明类型，无需 Issue 或 labels。
- 任务文件是任务要求的唯一来源；变更时记录原因并通知执行方。
- 分发前填入任务文件路径、基准分支和提交，明确角色、上下文与允许路径。
- 第一版由用户手动转发到其他平台；不自动调用外部 Agent。
- 根据 skills/acceptance.md 验收 PR，按仓库规则合并并更新状态。
- 不将草稿、模拟操作或尚未运行的检查记作完成。

## 子 Agent

- 只读取任务指定上下文和适用规则；不足时提出具体补充需求。
- 在独立任务分支执行，只修改允许路径；不擅自扩大范围。
- 提交产物和 skills/report.md 格式的报告，关联任务 ID 和任务文件；无权限时交付文件或补丁供用户代交。
- 不关闭任务或改写项目总体状态，最终验收由总 Agent 完成。

## 持久状态

任务文件保存要求及执行记录；PR 保存变更与验收；RESEARCH_STATE.md 汇总进展和证据。关键决策写入 DECISIONS.md。凭证不得写入仓库。

Agent 可替换；GitHub 中的上下文、任务和产物不可替换。

~~~~

## 文件：PROJECT_CONTEXT.md

~~~~markdown
# 项目上下文

- 项目：research-agent-hub
- 仓库：https://github.com/Meihanxiao/research-agent-hub
- 目标：Codex 拆解与验收任务，其他平台 Agent 执行；GitHub 保存可跨设备恢复的记录。
- 范围：文献、代码、审查、演示、OpenFOAM 五类角色；先手动路由。
- 当前研究主题、数据来源、OpenFOAM 版本及算力：待用户提供，不自行假设。
- 第一里程碑：任务文件 → 外部 Agent → PR → Codex review → 合并 → 状态更新。
- 原则：Agent 可替换；GitHub 中的上下文、任务和产物不可替换。

~~~~

## 文件：RESEARCH_STATE.md

~~~~markdown
# 当前状态

- 阶段：已按用户要求取消 Issue 环节；TASK-001 待手动分发。
- 仓库：https://github.com/Meihanxiao/research-agent-hub
- 已完成：远端关联、基础文件上传、任务文件驱动的流程、PR 模板与验收清单。
- 当前流程：任务文件 → 用户手动转发 → 子 Agent 交付 PR → Codex review → 合并 → 状态更新。
- 下一步：将 tasks/TASK-001-HANDOFF.md 转发给其他平台 Agent；收到结果后返回本任务验收。
- 尚未验证：子 Agent 实际交付、PR 写入权限、review、闭环与跨设备恢复。
- 外部依赖：用户选择执行平台并转发任务；无 PR 写入能力时带回文件或补丁供代交。
- Issue 权限不再是阻塞项；不创建 Issue 或类型 labels。

| ID | 状态 | 任务文件 | PR | 产物 |
| --- | --- | --- | --- | --- |
| TASK-001 | 待手动分发 | tasks/TASK-001.md | 待提交 | 待生成 |

状态采用：待分发、执行中、待验收、需修改、已完成、阻塞。由总 Agent 根据实际证据更新，不将计划记作完成。

~~~~

## 文件：DECISIONS.md

~~~~markdown
# 决策记录

| 日期 | 决策 | 理由 |
| --- | --- | --- |
| 2026-09-11 | GitHub 为唯一事实来源 | 支持跨设备和更换执行 Agent |
| 2026-09-11 | 第一版手动转发任务 | 先验证任务协议与验收闭环 |
| 2026-09-11 | 使用 research-agent-hub 仓库 | 用户已提供目标仓库 |
| 2026-09-11 | 首个任务审查协作流程 | 不依赖科研数据或专业运行环境 |

| 2026-09-11 | 用户取消 Issue 环节，任务文件作为任务要求及执行记录来源；保留 PR 验收 | 不再依赖插件 Issues 写入权限；Type 字段替代 labels |

~~~~

## 文件：tasks/TASK-001.md

~~~~markdown
# TASK-001：检查仓库协作流程

- ID: TASK-001
- Type: review
- Goal: 检查规则与模板能否支持一次可追溯的跨平台任务闭环。
- Context: AGENTS.md、PROJECT_CONTEXT.md、RESEARCH_STATE.md、DECISIONS.md、agents/review.md、skills/acceptance.md
- Inputs: Codex总Agent实现说明.md、README.md、TASK_TEMPLATE.md、skills/handoff.md、skills/report.md、.github/pull_request_template.md
- Constraints: 仅新增 outputs/TASK-001/ 下文件；不修改被审查文件；无法确认的内容明确标为待验证。
- Required Output: outputs/TASK-001/review.md 和 outputs/TASK-001/report.md
- Acceptance Criteria:
  - [ ] 结合 DECISIONS.md 中取消 Issue 的最新决定，对照原始说明逐项检查九个任务字段、五类角色、手动分发及状态回写。
  - [ ] 每个发现有文件位置、问题描述和具体建议；无问题也列出检查证据。
  - [ ] 检查无仓库权限、上下文不足、验收不通过三种情形的处理流程。
  - [ ] 报告区分文件审查和真实运行验证，不虚构 GitHub 操作。
- Deliver To: https://github.com/Meihanxiao/research-agent-hub；基准分支 main；任务文件 tasks/TASK-001.md；outputs/TASK-001/

## 交接记录

- 执行方：待用户指定
- 任务分支：task/TASK-001-workflow-review
- 基准提交：采用本次移除 Issue 流程的提交，精确 SHA 见 tasks/TASK-001-HANDOFF.md（交接说明在后续提交写入）
- PR：待提交

~~~~

## 文件：agents/review.md

~~~~markdown
# review 角色

对照要求逐项检查，报告文件位置、影响与修复建议；不越权修改被审查内容。

- 输入：完整任务、指定上下文、基准提交及所需数据。
- 输出：任务指定产物和 skills/report.md 所列执行报告。
- 仅在任务分支修改允许路径；信息不足时报告缺口。
- 按 skills/handoff.md 交接，通过 PR 或文件/补丁提交。
- 不负责最终验收，不绑定特定平台。

~~~~

## 文件：agents/literature.md

~~~~markdown
# literature 角色

核对来源、提炼研究问题与证据，区分原文结论和推断；输出可追溯引用。

- 输入：完整任务、指定上下文、基准提交及所需数据。
- 输出：任务指定产物和 skills/report.md 所列执行报告。
- 仅在任务分支修改允许路径；信息不足时报告缺口。
- 按 skills/handoff.md 交接，通过 PR 或文件/补丁提交。
- 不负责最终验收，不绑定特定平台。

~~~~

## 文件：agents/coding.md

~~~~markdown
# coding 角色

按指定环境实现变更，提供运行方法与必要测试结果；不得声称未运行的测试通过。

- 输入：完整任务、指定上下文、基准提交及所需数据。
- 输出：任务指定产物和 skills/report.md 所列执行报告。
- 仅在任务分支修改允许路径；信息不足时报告缺口。
- 按 skills/handoff.md 交接，通过 PR 或文件/补丁提交。
- 不负责最终验收，不绑定特定平台。

~~~~

## 文件：agents/presentation.md

~~~~markdown
# presentation 角色

根据指定受众组织内容，按任务格式交付可编辑演示产物，核验图表和引用。

- 输入：完整任务、指定上下文、基准提交及所需数据。
- 输出：任务指定产物和 skills/report.md 所列执行报告。
- 仅在任务分支修改允许路径；信息不足时报告缺口。
- 按 skills/handoff.md 交接，通过 PR 或文件/补丁提交。
- 不负责最终验收，不绑定特定平台。

~~~~

## 文件：agents/openfoam.md

~~~~markdown
# openfoam 角色

先核对指定版本、求解器与边界条件；记录网格、收敛和守恒检查及运行配置。

- 输入：完整任务、指定上下文、基准提交及所需数据。
- 输出：任务指定产物和 skills/report.md 所列执行报告。
- 仅在任务分支修改允许路径；信息不足时报告缺口。
- 按 skills/handoff.md 交接，通过 PR 或文件/补丁提交。
- 不负责最终验收，不绑定特定平台。

~~~~

## 文件：skills/acceptance.md

~~~~markdown
# 验收清单

1. 确认 PR 对应任务、基准和允许修改的范围。
2. 逐条检查 Acceptance Criteria，实际打开产物并执行必要验证。
3. 在 review 记录每项结论及证据；不通过时明确修改项，修订后复核。
4. 按仓库权限和合并规则合并；仅有 review 不算合并。
5. 更新 RESEARCH_STATE.md 的结果、产物、PR 和下一步，必要时更新 DECISIONS.md。
6. 状态更新进入主分支后将任务标为完成；记录合并与状态更新的真实证据。
7. 若同一账号不能正式批准自身 PR，保留书面验收记录；不冒充另一审查账号。

~~~~

## 文件：skills/handoff.md

~~~~markdown
# 手动交接清单

1. 总 Agent 创建唯一任务 ID；核对任务模板所有字段。
2. 将完整要求写入 tasks/<ID>.md；执行进度与补充说明回写该文件。
3. 固定基准提交，选定角色，提供任务及明确列出的上下文。
4. 用户转发；私有仓库不可读时提供所需文件，不仅提供链接。
5. 执行方如需额外上下文，先说明缺口，不自行扩大范围。
6. 无 GitHub 写入能力时交付文件或补丁和报告，由用户代交 PR。

~~~~

## 文件：skills/report.md

~~~~markdown
# 执行报告模板

- 任务 ID：
- 基准提交：
- 完成内容：
- 产物路径：
- 验收条目及对应证据：
- 实际运行的验证及结果：
- 未运行的验证及原因：
- 限制、阻塞与所需补充：
- PR 链接或代提交说明：

不得把未执行的验证写为通过。

~~~~

## 文件：TASK_TEMPLATE.md

~~~~markdown
# <ID>：<标题>

- ID: TASK-NNN
- Type: literature | coding | review | presentation | openfoam（选择一项）
- Goal: 单一可验证目标
- Context: 指定文件、章节、角色说明、基准提交
- Inputs: 输入路径或链接；无则写“无”
- Constraints: 允许修改的路径、依赖、工具和资源限制
- Required Output: 文件格式、命名、路径及执行报告
- Acceptance Criteria:
  - [ ] 可逐项验证的标准
- Deliver To: 仓库 URL、基准分支、任务文件路径、产物路径

## 交接记录

- 执行方：待指定
- 任务分支：task/<ID>-<简短名称>
- 基准提交：分发前填写真实提交
- PR：待提交
- 阻塞或补充上下文：无

~~~~

## 文件：README.md

~~~~markdown
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

~~~~

## 文件：Codex总Agent实现说明.md

~~~~markdown
> 历史需求说明：用户已取消 Issue 环节。当前执行以 AGENTS.md、TASK_TEMPLATE.md 和 DECISIONS.md 为准；下方保留原始需求供追溯，不作为 Issue 强制要求。

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

~~~~

## 文件：.github/pull_request_template.md

~~~~markdown
## 对应任务

任务 ID：
任务文件链接：
基准提交：

## 交付

产物路径：
完成内容：

## 验证

- [ ] 逐项列出验收标准与实际证据
- [ ] 改动在允许范围内
- [ ] 已说明未运行验证、限制和阻塞

## 总 Agent 验收

review 结论：
状态更新：合并产物后回写 RESEARCH_STATE.md，完成后将任务状态标为完成。

~~~~
