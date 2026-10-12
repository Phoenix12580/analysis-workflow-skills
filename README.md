# Analysis Workflow Skills

版本：0.1.0。中文分析协作规则与 Agent Skills 仓库。用于新项目初始化，并逐步收纳经验证的专题分析 Skill。不是自动分析流水线，不绑定特定数据、语言或算法。

## AI 从哪里开始

先读本文件，识别用户任务，再只读对应 Skill 及其明确要求的资源。不要递归读取整个仓库。用户目标项目与本规则仓库是两个不同位置，操作前必须辨认清楚。

| 任务 | 入口 | 状态 |
|---|---|---|
| 初始化分析项目、建立阶段计划、采用协作约定 | [project-init](skills/project-init/SKILL.md) | 初版；静态检查与行为测试须分别说明 |
| 查看通用协作规则 | [项目 AGENTS 模板](skills/project-init/assets/AGENTS.template.md) | 已整理本次确认的边界 |
| 增加某类分析 Skill | [贡献约定](CONTRIBUTING.md) | 按实际需求添加，不预建空 Skill |
| 验收初始化行为 | [验收场景](tests/acceptance.md) | 待在真实新会话测试 |

## 两种使用方式

### 直接从 GitHub 读取（先用这种即可）

上传后，向 AI 提供本仓库 README 的地址，以及目标项目位置、目标、数据来源和授权范围。建议指定 tag 或 commit，避免分支更新悄悄改变规则。

可直接说：

> 请读取【仓库地址和版本】的 README，按 project-init Skill 初始化【目标项目路径】。研究目标是【目标】，数据位于【路径或来源】。这次只初始化，先不要开始分析。先读取 Skill 及其要求的模板，再操作目标项目；已有文件先检查，不覆盖。

如果第一阶段已明确并获授权，可把最后一句改成“初始化后继续完成以下已确认的第一阶段：……”。没有明确继续授权时，初始化后停止。

GitHub 不会自动把 Skill 注入所有 AI。AI 必须有访问能力并实际读取入口、Skill 和所需资源；相对链接相对于同一仓库版本解析。无法访问时提供本地副本或文件附件，不声称已加载。私有仓库使用工具已有的安全认证，不将 token 写进对话或模板。

### 安装到支持 Agent Skills 的客户端

将整个 `skills/project-init/` 目录（包括 assets）复制到客户端支持的 Skill 路径，不要只复制 SKILL.md。Posit Assistant 可使用项目级 `.posit/assistant/skills/project-init/` 或用户级 `~/.posit/assistant/skills/project-init/`；也支持共享规范目录 `.agents/skills/` 和 `~/.agents/skills/`。其他客户端以其文档为准。安装、信任项目和权限授权是独立动作；本仓库不自动修改这些设置。

安装后仍需让客户端发现/加载 Skill，不能保证每个客户端自动触发。按客户端说明调用；若不支持安装，也可以显式要求 AI 读取本地 SKILL.md。

## 初始化后如何持续生效

Skill 将通用规则实例化为目标项目的 AGENTS.md，项目事实写入 README，阶段授权写入 PLAN。通用规则的唯一维护源是本仓库中的 AGENTS 模板；目标项目使用带来源记录的本地快照，可以有明确的项目例外，不自动追随仓库更新。

后续会话先读目标项目规则、README 当前入口和阶段计划/交接；只有当前任务需要专题方法时，才回本仓库读取匹配 Skill。无需每轮重新下载所有规则。升级规则时先比较差异、确认影响并保留旧版本，不强制覆盖项目现场。

## 仓库边界与发布

这里只存可复用说明、模板和将来明确需要的工具脚本。不存研究数据、患者信息、真实项目结果、凭据或本机专用路径。

本目录可以单独复制到你自己的 GitHub 仓库；不要把它的父级研究项目一起上传。当前没有自动执行 git init、commit、push 或安装操作。`.gitignore` 只是防误入辅助，上传前仍需检查待提交文件。许可证由仓库所有者决定，本初版未代选开源许可。

## 规范依据

[Agent Skills 规范](https://agentskills.io/specification.md)、[Skill 编写建议](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)、[Posit Assistant Skills](https://assistant.posit.co/docs/features/skills/)。
