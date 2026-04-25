# Skills Collection

## Overview
Curated Claude Code skills collection. Each skill extends Claude with specialized domain knowledge.

## Structure
```
skills/
└── {skill-name}/
    ├── SKILL.md           — Core instructions (YAML frontmatter + Markdown)
    ├── references/        — Supporting documents loaded on demand
    └── examples/          — Model responses demonstrating the skill
```

## Rules
- Every skill must have a SKILL.md with YAML frontmatter containing `name` and `description`
- Skills should be concise — the context window is shared with everything else
- References and examples are loaded on demand, not always
- New skills require approval before merging
