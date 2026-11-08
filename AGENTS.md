# AGENTS.md

## 原则

新增或修改代码、测试及文档前逐项回答，若为否则需明确原因：

- 复用去重：是否已探索并复用已有内容？（DRY）
- 符合规范：是否遵循项目规范以及惯例？（Consistency）
- 场景驱动：是否对应具体的问题和场景？（YAGNI）
- 删除检验：删除它是否会留下明确缺口？（Deletion Test）
- 最小必要：是否已无其他更精简的方案？（KISS）

## 规则

- 提交信息若无项目规范惯例，默认 Conventional Commits。
- 决策方向与执行进度由 issue tracker 管理。仅在用户明确要求或调用相关 skill 时修改。
- 文档只描述当前状态，删除失效历史，ADR 除外。
- 文档只保留无法从代码轻易获得的信息。
- 测试只针对行为，不针对静态结构。

## 文档

文档结构若无项目规范惯例，默认如下：

- `README.md`：给使用者看的入口。仅在用户明确要求时修改。
- `docs/development.md`：环境搭建与开发指南。不声明具体依赖版本。
- `docs/module-guide.md`：模块职责与文件导航。优先使用 Markdown 表格形式。
- `docs/spec.md`：持久化行为规格。过长时按领域拆分至 `docs/spec/`，本文件留做链接跳转。
- `docs/external/`：依赖的外部系统的调查事实。其他调查事实默认存放至临时目录。

## Skills 与 Subagents

执行以下 skill 时：

- `/grilling`：探索完实现边界后先总结决策，即使用户要求执行也先总结。
- `/to-spec`：在用户明确指定时可以包含具体文件路径及代码片段。
- `/implement-spec`：
  - 优先在主代理中使用确定性命令合并，仅在出现语义冲突时调用合并子代理。
  - 保存子代理 handoff 路径，交付时用 worktree.discard。

调用子代理时：确定角色并分派前先 list capabilities。
