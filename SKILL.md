---
name: long-running-work
description: 长时间自动化工作的最佳实践。适用于 cron jobs、sub-agent 任务、多步骤复杂任务。当需要执行长时间运行的任务、委派子代理、或进行复杂工作时加载此 skill。
---

# Long-Running Work - 长时间工作最佳实践

## 核心原则

### 1. 开始前 - 明确目标

- **读取项目文档**: PROJECT.md + PLAN.md
- **定义验收标准**: 什么是"完成"？
- **规划步骤**: 分解为小步骤，每步可验证
- **设置检查点**: 复杂任务使用 checkpoint 模式

### 2. 执行中 - 保持状态

- **定期保存**: 每完成关键步骤，保存进度
- **验证结果**: 每步完成后立即验证，不要等到最后
- **记录日志**: 关键决策和发现写入 Diaries/YYYY-MM-DD.md
- **处理错误**: API 限流 (429) → 等待后重试；超时 → 增加超时时间

### 3. 执行后 - 清理和汇报

- **验证最终结果**: 不要假设成功，要实际检查
- **更新文档**: 
  - PROJECT.md - 项目状态
  - PLAN.md - Checkpoint 完成情况
  - MEMORY.md - 重要经验教训
- **发送汇报**: Telegram 简明扼要

## 子代理管理 (sub-agent)

当需要委派任务时：

### 任务描述模板

```
## 任务目标
[具体要完成什么]

## 验收标准
1. [可验证的标准1]
2. [可验证的标准2]

## 执行步骤
1. [步骤1]
2. [步骤2]

## 注意事项
- [特殊要求或限制]
```

### 结果审查

- 检查 git diff
- 验证测试结果
- 确认文档已更新
- 如有问题，让子代理修复直到满意

## 检查点模式示例

```bash
# 每个关键步骤后保存
python3 checkpoint_manager.py save fetch "done"
python3 checkpoint_manager.py save analyze "done"
python3 checkpoint_manager.py save html "done"
python3 checkpoint_manager.py save deploy "done"

# 任务完成后清除
python3 checkpoint_manager.py clear
```

## 常见错误处理

| 错误 | 处理方式 |
|------|----------|
| API 429 | 等待 30s，重试最多 3 次 |
| 超时 | 增加 timeoutSeconds |
| 验证失败 | 修复后重新部署，再次验证 |
| 推送失败 | 检查 Telegram 配置 |

## 验证清单

完成任何任务后，必须验证：

- [ ] 代码/部署实际工作（不只是"认为"工作）
- [ ] 相关文档已更新
- [ ] Git 已提交
- [ ] Telegram 已发送汇报
- [ ] 日记已写入
