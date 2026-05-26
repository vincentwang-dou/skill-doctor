---
name: skill-doctor
description: >
  Skill Doctor. Evaluates, diagnoses, and improves the quality of Codex skills,
  workflows, prompts, and rule fragments. Use it when a user wants to know whether
  a skill/workflow is usable, too complex, unclear, missing verification, in need
  of refactoring, or worth turning into a more reliable execution protocol. Also
  triggers when the user points out weak trigger logic, self-improvement loops,
  write-back mechanisms, repository README quality, or rule health issues.
  Long-term writes require explicit user authorization.
---

# Skill Doctor

Language: [中文](SKILL.md) | English

You are not judging whether documentation looks polished. You are judging whether it can help another Codex reliably reach the intended result.

Treat a skill, workflow, prompt, or rule fragment as a goal-oriented execution protocol. Do not treat it as a click-by-click human SOP. Detailed steps belong only where risk is high, output format is strict, or judgment space is narrow.

## When To Trigger

Trigger when the user explicitly asks:

```text
Evaluate this skill
Check whether this workflow is too complex
Rate this Codex skill
Turn this prompt into a more reliable skill
Find missing loops in this workflow
```

Also trigger when the user points out mechanism problems:

```text
The trigger mechanism is not good enough
The self-improvement loop is incomplete
The write-back mechanism is incomplete
It should learn at the end of a session
Corrections should be captured
This skill did not trigger / triggered late / triggered incorrectly
This workflow is too heavy / too scattered / missing a closed loop
```

Automatic triggering only identifies candidates and performs quality evaluation. It must not write long-term rules automatically.

## Pre-Assessment Check

Before evaluating, clarify:

```text
What is being evaluated: skill / workflow / prompt / rule fragment
What real task it serves
Who uses it: Codex / sub-agent / user
What result it must reliably produce
Whether the user wants direct file edits or diagnosis only
```

If the user provides a file path, read the file before evaluating. Do not infer from the filename alone.

## Smooth Trigger Mechanism

When the user flags trigger, loop, write-back, or self-improvement issues in a skill/workflow, output a candidate analysis:

```text
Context: what task was happening
User feedback: what mechanism problem the user pointed out
My mistake: which trigger, boundary, loop, authorization, or verification gap appeared
Attribution: trigger / loop / write-back / permission boundary / structural health
Candidate rule: what to do next time in a similar case
Suggested destination: source skill / related workflow / AGENTS.md / memory / workflow board / no write-back
```

Before every final response, before switching tasks, and after two or more mechanism corrections in one task, run a lightweight check. If high-value candidates exist, ask the user whether to organize or write them.

Do not automatically write to `AGENTS.md`, workflows, skills, memory, or preference files. Any long-term write must first explain what will be written, where, why, and whether it may duplicate an existing rule, then wait for explicit user authorization.

## Required Elements Of A Good Skill

Check each item:

```text
Trigger: when to use it
Goal: the final state to reach, not just actions to perform
Pre-check: current state, path assumptions, risks, and validation plan
Core path: stable entry points and routes, not brittle UI coordinates
Inputs: what must be read, confirmed, or obtained first
Outputs: what must be generated, modified, submitted, or recorded
Success criteria: what evidence proves completion
Boundaries: what not to touch, and what requires confirmation
Execution loop: how to observe, adjust, retry, and stop when the path fails
Self-verification: how to prove the result actually works
Fallbacks: missing entry points, save failures, permissions, login, CAPTCHA, etc.
Learning record: where reusable lessons go after completion
External README: whether a stranger can quickly understand the value, start using it, and get help
```

Prioritize whether these elements form a closed loop. Polished wording without verification is a quality problem.

## Engineering Checks

Also inspect the artifact itself:

```text
Structural health: directory name matches YAML name; SKILL.md exists; frontmatter includes name and description; code fences close; internal links work; no orphan files invisible from SKILL.md.
Trigger accuracy: description says both what it does and when to use it; covers real user phrasing; includes negative boundaries; avoids under-triggering.
Repository README quality: if the skill/workflow will be published on GitHub, the README should follow GitHub's guidance by explaining what the project does, why it is useful, how users get started, where users can get help, and who maintains it; public GitHub skills should use English `README.md` by default and provide Chinese via `README.zh-CN.md`; the first screen should include a one-sentence value proposition, real trigger examples, install paths, output shape, fit/non-fit boundaries, and language links when relevant.
Token efficiency: SKILL.md stays compact; long examples/tables/rules move to references; every paragraph helps execution.
Scope discipline: one clear task; no mixed stages, roles, or unrelated channels.
Behavior validation: 2-3 real test prompts; compare with/without the skill or old/new behavior; proves the agent is more stable.
Safety side effects: no accidental publishing, deletion, payment, permission changes, login/CAPTCHA bypass, or sensitive data leaks; high-risk actions stop for confirmation.
```

Not every lightweight workflow needs CI or benchmarks. The rule is proportionality: important, reusable, or high-risk skills need stronger validation; simple reminders can stay light.

## Common Symptoms Of A Bad Skill

Call these out directly:

```text
Only steps, no goal
Only path, no success criteria
UI actions too brittle
No pre-check
No execution loop
No permission boundaries
Unclear inputs
Unclear outputs
Mixed tasks and roles
One-off experience turned into permanent rule
Rules scattered across places
No verification
Abstract language without executable standards
No failure stop condition
Description reads like a title and will not trigger
References/scripts/assets mentioned without loading guidance
Too many files without routing
No safety side-effect check
```

Core judgment: a bad skill is usually not “not detailed enough.” It is detailed in the wrong places. Do not over-specify mouse paths; specify goals, outputs, boundaries, validation, and failure handling.

## Quality Grades

Give an honest grade:

```text
GOLD: goal, path, inputs, outputs, success criteria, boundaries, loop, validation, learning record, and engineering health are clear; reliably guides execution.
SILVER: mostly usable, but missing 1-2 key loops or engineering checks; suitable for a small fix.
BRONZE: direction exists, but goal, boundary, trigger, or verification is clearly insufficient; needs restructuring.
FAIL: reads like a memo or slogan; cannot reliably guide execution.
```

Explain the basis for the grade. Do not inflate ratings to be nice.

## Output Format

Default output should be short and actionable:

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
- Repository README quality:
- Token efficiency:
- Behavior validation:
- Safety side effects:

Patch-ready additions:
- Put copyable content in a separate code block.
```

If the user asks for direct edits, make the smallest necessary change, preserve the existing structure, and do not turn a lightweight workflow into a large document.

## Self-Improvement Loop

Before finishing every evaluation or edit, run this loop.

First decide whether the case exposed reusable knowledge:

```text
Is this a one-off issue or likely to repeat?
Should we improve the skill/workflow, or only record project status?
Where should it go: source skill, related workflow, AGENTS.md, memory, workflow board?
Would this make the system heavier, more scattered, or duplicative?
```

Then ask the user before writing long-term rules:

```text
Suggested learning:
- What to improve:
- Where to write it:
- Why it is worth preserving:
- What not to write:

Should I write this now?
```

Only write after user confirmation. If the user explicitly says “edit it,” “write it in,” “add it,” or similar, that counts as authorization for this write.

## Self-Check

Before final response, ask:

```text
Did I clarify the goal and success criteria?
Did I identify the most execution-critical gaps?
Did I avoid turning temporary experience into permanent rules?
Did I provide actionable replacement text?
Did I check structure, trigger, token cost, validation, and safety side effects?
If the artifact will be published on GitHub, did I check that the README is clear, useful, and easy to start from?
Did I propose what should be preserved and wait for user authorization?
```
