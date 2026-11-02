# teach-skills

A personal configuration of [Matt Pocock's `teach` skill](https://github.com/mattpocock/skills/tree/main/skills/productivity/teach) for Claude Code.

The original skill turns a directory into a stateful teaching workspace (mission, lessons, reference docs, learning records, glossary). This version keeps that structure and adds:

- **Curriculum intake** — goals, timeline, weekly time budget, prior experience, and source materials are collected before the first lesson, then turned into a written curriculum map.
- **Source material first** — the learner's books, papers, and docs are the primary authority; Claude's parametric knowledge is only used for orientation or clearly labeled gaps.
- **Large / multiple sources** — imports working copies into `source-materials/`, builds durable indexes in `source-index/` and cross-source concept notes in `source-notes/`, and retrieves only the sections each lesson needs, with citations.
- **Project-based learning loop** — lessons are milestones of a real project; Claude coaches with hints and feedback rather than handing over solutions.
- **Diagnostics and mastery gates** — a diagnostic before each new topic, continuous assessment, and no advancing past unresolved misconceptions.

## Install

```bash
git clone https://github.com/ketiyohannes/teach-skills.git
cp -R teach-skills/skills/teach ~/.claude/skills/
```

Then in Claude Code, run `/teach <what you want to learn>` from an empty (or existing) workspace directory.

## Files

```
skills/teach/
├── SKILL.md                     # main instructions
├── MISSION-FORMAT.md
├── RESOURCES-FORMAT.md
├── GLOSSARY-FORMAT.md
└── LEARNING-RECORD-FORMAT.md
```

## Credit

Based on [mattpocock/skills](https://github.com/mattpocock/skills) by Matt Pocock, MIT licensed. The original license is retained in [LICENSE](./LICENSE).
