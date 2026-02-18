# Long-Running Work Skill - Plan

## 目标

创建一个 skill，帮助在长时间自动化工作中保持良好的工作流和工作习惯。

## Skill 概述

- **名称**: `long-running-work`
- **用途**: 长期自动化任务（cron jobs、sub-agents）中的最佳工作实践
- **触发场景**: 当执行需要长时间运行的任务、需要委派子代理、或者进行复杂的多步骤工作时

## 需要包含的内容

### 1. 工作前规范
- [ ] 检查项目状态（PROJECT.md, PLAN.md）
- [ ] 确认任务目标和验收标准
- [ ] 规划步骤和检查点

### 2. 执行中规范
- [ ] 定期保存进度（checkpoint）
- [ ] 验证每个步骤的结果
- [ ] 记录关键决策到日记

### 3. 执行后规范
- [ ] 验证最终结果
- [ ] 更新相关文档（MEMORY.md, PROJECT.md, PLAN.md）
- [ ] 汇报完成状态

### 4. 子代理管理
- [ ] 明确的任务描述
- [ ] 验收标准定义
- [ ] 结果审查流程

### 5. 特殊情况处理
- [ ] API 限流处理
- [ ] 超时处理
- [ ] 错误恢复

## 参考文件

- `~/.openclaw/workspace/AGENTS.md` - 工作规则
- `~/.openclaw/workspace/IDLE.md` - 空闲工作指南
- `~/.openclaw/workspace/HEARTBEAT.md` - 心跳工作流

## 执行步骤

1. 创建 SKILL.md
2. 创建 references/ 目录（可选）
3. 测试 skill 触发
4. 更新 HEARTBEAT.md 引用此 skill
