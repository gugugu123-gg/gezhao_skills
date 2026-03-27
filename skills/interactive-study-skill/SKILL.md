---
name: interactive-study-skill
description: Run a mastery-based one-on-one interactive learning workflow (Bloom 2 Sigma + Mastery Learning) for users who want to start or continue a study topic, generate sequenced lesson notes, evaluate understanding before progression, adapt depth using prior feedback, and produce a final integrated summary note. Use when users ask to learn a topic, continue an existing topic folder, design a study roadmap, generate lesson-by-lesson study notes, run comprehension checks/stress tests, or manage progress via 学习状态.md.
---

# Interactive Study Skill

## Workflow

1. Detect intent.
- Trigger when user asks to start learning or continue a topic.
- Ask first: learn a new topic or continue an existing one.

2. Resolve topic folder.
- For new topic: create topic folder and collect goal, baseline, and source materials.
- For existing topic: read `学习状态.md` and continue from the next pending item.
- Keep strict sequence: `01-主题.md`, `02-主题.md`, ...
- Never skip numbers, overwrite previous lessons, or generate multiple new lessons at once.
- Use `02b-补充.md` style only for targeted blind-spot remediation.

3. Run Step 0 purpose evaluation before teaching.
- Answer explicitly: "学这个对我有什么用？"
- Include:
  - capability gain,
  - link to user context/work,
  - one-line motivation anchor.

4. Run baseline diagnosis and roadmap.
- Assess user baseline.
- Identify key blind spots.
- Build a roadmap with blind-spot-first ordering.

5. Generate lesson content using first-principles scaffolding.
- For each core concept:
  - decompose inward to irreducible assumptions,
  - derive outward to practical applications,
  - use Socratic questions during explanation.
- Generate the lesson document immediately during/after the interaction, not deferred.

6. Enforce adaptive progression gate.
- Before generating lesson N, read feedback from lesson N-1.
- If feedback is missing, do not generate lesson N.
- Progress decision:
  - fully mastered: advance,
  - mostly mastered: correct then advance,
  - partially understood: add remediation lesson,
  - not understood: restart from more basic level.

7. Perform Feynman output after document generation.
- Add one-sentence anchor.
- Run checkpoint questions.
- Provide synchronized summary.

8. Complete topic and generate integrated note.
- When all items in `学习状态.md` are completed, generate `[主题名]整合笔记.md` in the topic root.

## Required Files and Format

- Progress file: `学习状态.md` in each topic folder.
- Use template from [references/learning-state-template.md](references/learning-state-template.md).
- Lesson files must include required tail sections from [references/lesson-template.md](references/lesson-template.md):
  - 学习反馈
  - 理解检测
  - 压力测试

## Tag and Metadata Policy

Before writing any new note, read tag dictionary in this order:
1. `D:\obsidian仓库\2\40-原则\属性与标签字典.md`
2. `D:\obsidian仓库\2\40-原则\属性与标签字典.md` (fallback: use same path and stop if unavailable)

Always write frontmatter with:
- `tags` (YAML list)
- `created` (`YYYY-MM-DD`)

Tag rules:
- Add exactly one functional tag from the dictionary policy.
- Add 1-2 topic tags only when useful for retrieval.
- Avoid new tags unless necessary; if required, update dictionary first.

## Operational Constraints

- Keep teaching style: Feynman simplicity + Socratic questioning + scaffolding + error-friendly guidance.
- Prefer user-provided materials; use `D:\电子书` as canonical ebook library path when searching references.
- If critical inputs are missing (goal, baseline, previous feedback), ask concise questions first and block progression until resolved.
