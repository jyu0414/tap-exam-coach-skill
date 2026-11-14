# exam-drill

[日本語](README.md) | English

A Claude skill for certification exam prep. Tell it the exam and your test date, and it looks up the official outline and the real exam's question format, builds a week-by-week study plan, and drills you one question at a time in the same format as the real exam, with an explanation after each answer.

## Features

- **Setup**: researches the official outline, domain weights and the real question format from official sources: number of choices and their labels, multi-select, short answer, diagrams, and what the exam screen and the result report show. It then builds a weekly plan with a decision point, a to-do list and a per-subtopic question allocation.
- **Study mode**: asks one question at a time, covering every subtopic, and explains each answer. Multiple-choice questions are answered by tapping (AskUserQuestion in Claude Code); short-answer questions are typed.
- **Quick check**: about 20 questions, any time, to see whether you'd pass today. No plan needed.
- **Mock exam**: real question count, domain mix and time limit, scored together at the end. At the decision point it suggests whether to move the test date; you decide.
- **Review**: sorts wrong answers into three types, keeps a weak-point log, and brings them back through recall tests and re-drills.

Progress is saved as Markdown in `exam-drill-data/<exam>/`, so you can pick up where you left off even after the conversation ends.

## Example prompts

The skill works in Japanese and English. For example:

- "I want to pass CISSP in January. Make me a study plan."
- "Continue this week's CISSP questions."
- "Could I pass AWS SAA if I took it today? Give me a quick check."
- "I want to take a mock exam."

## Installation

- **Claude Code**: put `exam-drill/` in `~/.claude/skills/exam-drill/` (all projects) or in your project's `.claude/skills/exam-drill/`.
- **Claude.ai**: download `exam-drill.skill` from [Releases](../../releases) and upload it under Skills in Settings.

## Layout

```
exam-drill/
├── SKILL.md                 Triggers, overall flow, rules applied every time
├── references/
│   ├── setup.md             Exam and question-format research, plan, allocation
│   ├── question-rules.md    Per-question flow, answer UI, question-writing rules, pre-check
│   ├── formats.md           N-choice, multi-select, combination, short answer, diagrams, long scenarios
│   ├── quick-check.md       Quick check
│   ├── mock-mode.md         Mock exam
│   ├── review.md            Wrong-answer types, weak-point log, recall tests, re-drills
│   └── records.md           Record file formats
├── templates/               Templates for the record files
└── evals/                   Test cases (runnable with `claude plugin eval`)
```

The skill's instructions are written in Japanese.
