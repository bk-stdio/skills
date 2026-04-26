# bk-stdio/skills

Claude Code skills collection. Each skill is a self-contained package that extends Claude Code with specialized knowledge, workflows, and tools.

## Available Skills

| Skill | Description |
|-------|-------------|
| **[reformed-theology](skills/reformed-theology/)** | Biblical theology, exegesis, apologetics, pastoral counsel, ethics, and worldview analysis rooted in the historic Reformed evangelical tradition. |
| **[report-generator](skills/report-generator/)** | Generate clean, professional PDF reports from any content. Notion-inspired design — works with any domain. |

## How to Use

### Install a Skill

Copy the skill folder to your Claude Code skills directory:

```bash
# Clone this repo
git clone https://github.com/bk-stdio/skills.git

# Copy a skill to Claude Code
cp -r skills/reformed-theology ~/.claude/skills/
```

Or reference it directly in your Claude Code configuration.

### Skill Format

Each skill follows the standard Claude Code skill format:

```
skill-name/
├── SKILL.md              # Required: YAML frontmatter + instructions
├── references/           # Optional: documentation loaded on demand
└── examples/             # Optional: model responses showing the skill in action
```

The `SKILL.md` file contains YAML frontmatter with `name` and `description` fields, followed by markdown instructions that Claude loads into context when the skill is activated.

## Contributing

This is a curated collection. All new skills require approval before being added.

## License

MIT
