# Skill Doctor

Language: [中文](README.md) | English

**A quality inspector for Codex skills.**

It does not ask whether your documentation looks polished. It asks the practical question:

> Can this skill, workflow, prompt, or rule fragment help another Codex reliably get the intended result?

Many agent workflows fail not because they are too short, but because they lack goals, success criteria, boundaries, verification, and fallback paths. Skill Doctor is designed to find those gaps.

## What It Helps With

- Your skill looks complete, but it often does not trigger.
- Your workflow has many steps, but Codex still drifts.
- You want to turn a prompt into a reliable skill.
- A recurring correction from a user should become a stable mechanism.
- You want an honest GOLD / SILVER / BRONZE / FAIL rating for a skill.

## Quick Start

Copy the repository into your Codex skills directory:

```bash
cp -R skill-doctor ~/.codex/skills/skill-doctor
```

Or install it locally inside a project:

```bash
cp -R skill-doctor .agents/skills/skill-doctor
```

Example prompts:

```text
Use skill-doctor to evaluate this workflow
Check whether this skill is too complex
Rate this Codex skill
Turn this prompt into a more reliable skill
Find the missing loops in this workflow
```

## What It Checks

| Dimension | Question |
| --- | --- |
| Trigger | When should this activate? Will it under-trigger or misfire? |
| Goal | What final state must be reached, not just what actions should happen? |
| Inputs / outputs | What must be read first? What must be produced? |
| Success criteria | What evidence proves the task is complete? |
| Boundaries | What must not be touched? What requires confirmation? |
| Execution loop | How should the agent observe, adjust, retry, and stop? |
| Self-verification | How does the agent prove the result works? |
| Fallbacks | What happens when login, permissions, saving, or entry points fail? |
| Learning record | Which lessons should be written back to a skill, workflow, memory, or board? |
| Safety side effects | Could this cause publishing, deletion, payments, permission changes, or leaks? |

## Output Shape

Skill Doctor defaults to a short, actionable diagnosis:

```text
Conclusion:
Grade:

Main issues:
- ...

Keep:
- ...

Recommended changes:
- ...

Missing loops:
- Pre-check:
- Execution loop:
- Self-verification:
- Fallback:
- Learning record:

Engineering checks:
- Structural health:
- Trigger accuracy:
- Token efficiency:
- Behavior validation:
- Safety side effects:
```

## Quality Grades

```text
GOLD: goal, path, inputs, outputs, success criteria, boundaries, loop, validation, learning record, and engineering health are clear.
SILVER: mostly usable, but missing 1-2 key loops or engineering checks.
BRONZE: direction exists, but goal, boundary, trigger, or verification is clearly insufficient.
FAIL: reads like a memo or slogan; cannot reliably guide execution.
```

Grades must explain the evidence. No flattering ratings.

## Why It Matters

Skill Doctor turns “this skill feels weak” into an engineering diagnosis:

```text
Where is the trigger weak?
Is the goal explicit?
Can the agent cross a boundary by accident?
Does it know when to stop?
Can the result be verified?
Should this lesson be preserved?
```

It is especially useful for long-lived agent workflows. The more frequently a skill is used, the more risk it carries, or the more easily it can misfire, the more it should be inspected first.

## Files

```text
SKILL.md       # Chinese Codex Skill
SKILL.en.md    # English skill version
README.md      # Chinese README
README.en.md   # English README
LICENSE        # MIT
```

## Feedback

If Skill Doctor misses a trigger, gives an unstable rating, or overlooks an important loop in a real task, open a GitHub Issue with the smallest useful context:

```text
What was your goal?
What was the original skill / workflow?
What did Skill Doctor output?
What judgment did you expect?
```

The more concrete the case, the easier it is to turn it into the next rule.

## License

MIT
