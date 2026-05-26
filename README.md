# Skill Doctor

语言版本：中文 | [English](README.en.md)

**给 Codex Skill 做体检。**
它不问文档写得漂不漂亮，而是问一个更实用的问题：

> 这个 skill、workflow、prompt 或规则片段，能不能让另一个 Codex 稳定拿到结果？

很多 agent workflow 失败，不是因为写得太短，而是因为缺少目标、成功标准、边界、验证和失败兜底。Skill Doctor 就是用来找这些缺口的。

## 它适合解决什么问题

- 你的 skill 看起来完整，但经常不触发。
- workflow 写了很多步骤，但 Codex 执行时还是跑偏。
- prompt 想沉淀成 skill，但缺少输入、输出和成功标准。
- 一个规则已经反复被用户纠正，需要变成稳定机制。
- 你想知道某个 skill 到底是 GOLD、SILVER、BRONZE，还是其实不能用。

## 快速开始

把仓库复制到 Codex skills 目录：

```bash
cp -R skill-doctor ~/.codex/skills/skill-doctor
```

或者放到项目本地：

```bash
cp -R skill-doctor .agents/skills/skill-doctor
```

然后这样使用：

```text
用 skill-doctor 评估这个 workflow
检查这个 skill 是否太复杂
给这个 Codex skill 做质量评级
帮我把这个 prompt 改成更稳定的 skill
看看这个工作流缺少哪些闭环
```

## 它会检查什么

| 检查维度 | 它会问什么 |
| --- | --- |
| 触发 | 什么时候应该启用？会不会 under-trigger 或误触发？ |
| 目标 | 最终要达成什么状态，而不是做哪些动作？ |
| 输入 / 输出 | 执行前要读什么，完成后要产出什么？ |
| 成功标准 | 看到什么证据才算真的完成？ |
| 边界 | 哪些不能碰？哪些必须停下确认？ |
| 执行 loop | 路径失败时如何观察、调整、重试和停止？ |
| 自我验证 | 怎么证明结果真的生效？ |
| 失败兜底 | 登录、权限、保存失败、入口找不到时怎么办？ |
| 沉淀机制 | 哪些经验应该写回 skill、workflow、memory 或看板？ |
| README 发布页 | 陌生访问者能否快速理解价值、开始使用、获得帮助？ |
| 安全副作用 | 是否可能诱导发布、删除、付款、改权限或泄露敏感信息？ |

## 输出长什么样

Skill Doctor 默认给出短而可执行的诊断：

```text
结论：
等级：

主要问题：
- ...

应该保留：
- ...

建议修改：
- ...

缺失闭环：
- 执行前判断：
- 执行中 loop：
- 自我验证：
- 失败兜底：
- 沉淀机制：

工程化检查：
- 结构健康：
- 触发准确性：
- README 发布页健康：
- token 效率：
- 行为验证：
- 安全副作用：
```

## 质量等级

```text
GOLD：目标、路径、输入、产出、成功标准、约束、loop、验证、沉淀和工程化健康都清楚。
SILVER：主体可用，但缺少 1-2 个关键闭环或工程化检查项。
BRONZE：方向存在，但目标、边界、触发或验证明显不足。
FAIL：像备忘录或口号，不能稳定指导执行。
```

评级必须说明依据，不做安慰式打高分。

## 为什么它有用

Skill Doctor 把“这个 skill 感觉不太好”变成可操作的工程问题：

```text
触发哪里弱？
目标是否明确？
边界是否会越权？
失败时是否知道停在哪里？
结果是否可验证？
经验是否值得沉淀？
```

它尤其适合维护长期使用的 agent workflow：越常用、越高风险、越容易误触发，越应该先体检。

## 文件

```text
SKILL.md       # 中文 Codex Skill 主文件
SKILL.en.md    # English skill version
README.md      # 中文说明
README.en.md   # English README
LICENSE        # MIT
```

## 反馈与改进

如果你在真实任务里发现触发不准、评级不稳、或者某个闭环检查不够好，可以在 GitHub Issue 里留下具体上下文：

```text
你的目标是什么？
原 skill / workflow 是什么？
Skill Doctor 输出了什么？
你期望它怎么判断？
```

越具体的问题，越容易变成下一版规则。

## License

MIT
