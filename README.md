# Skill Doctor

Skill Doctor（Skill 体检师）是一个 Codex Skill，用来评估和改进另一个 skill、workflow、prompt 或规则片段。

它不评价文档写得漂不漂亮，而是判断：**这个东西能不能让另一个 Codex 稳定拿到结果。**

## 适合什么时候用

- 检查一个 Codex skill 是否好用
- 判断 workflow 是否太复杂、太散、目标不清
- 找出执行前判断、成功标准、失败兜底、验证环节的缺口
- 把一次性经验改成更稳定的 skill / workflow
- 给已有 skill 做 GOLD / SILVER / BRONZE / FAIL 评级

## 它会检查什么

- 触发条件是否准确
- 目标是否清楚
- 输入和产出是否明确
- 成功标准是否可验证
- 约束边界是否能防止越权
- 失败时是否知道该怎么停下
- 是否存在安全副作用
- 文件结构和 frontmatter 是否健康
- 是否过度复杂、职责混乱、token 成本过高

## 安装

把项目复制到 Codex skills 目录：

```bash
cp -R skill-doctor ~/.codex/skills/skill-doctor
```

或放到项目本地：

```bash
cp -R skill-doctor .agents/skills/skill-doctor
```

## 使用示例

```text
用 skill-doctor 评估这个 workflow
检查这个 skill 是否太复杂
给这个 Codex skill 做质量评级
帮我把这个 prompt 改成更稳定的 skill
看看这个工作流缺少哪些闭环
```

## 质量等级

```text
GOLD：目标、路径、输入、产出、成功标准、约束、loop、验证、沉淀和工程化健康都清楚。
SILVER：主体可用，但缺少 1-2 个关键闭环或工程化检查项。
BRONZE：方向存在，但目标、边界、触发或验证明显不足。
FAIL：像备忘录或口号，不能稳定指导执行。
```

## 项目文件

```text
SKILL.md   # Codex Skill 主文件
README.md  # 人类可读说明
```

## License

MIT
