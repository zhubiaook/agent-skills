# Agent Skills Configuration Guide

Skills are structured modules that extend the capabilities of AI coding assistants, containing specialized instructions (prompts), scripts, and resources.

## 📁 Directory Structure

Each Skill is a standalone folder with the following structure:

```text
skills/your-skill-name/
├── SKILL.md       # (Required) Core instruction file with YAML frontmatter
├── scripts/       # (Optional) Helper scripts or utilities
├── examples/      # (Optional) Reference examples
└── resources/     # (Optional) Templates or static assets

```

## 🔧 Configuration Paths

The following paths determine whether a Skill is active only for a specific project or globally across all projects.

### 1. Google Antigravity IDE

- **📂 Project Level:** `.agent/skills/`
- _Note:_ Create this folder in the project root.

- **👤 User Level (Global):** `~/.gemini/antigravity/global_skills/`
- _Note:_ Create in the user home directory; applies to all Antigravity projects.

### 2. Claude Code

- **📂 Project Level:** `.claude/skills/`
- _Note:_ Place Skill folders here; visible only to the current project.

- **👤 User Level (Global):** `~/.claude/skills/`
- _Note:_ Personal skill library available to all Claude Code sessions.

- _Reference:_ [Claude Code Skills Documentation](https://code.claude.com/docs/en/skills)

### 3. Cursor

- **📂 Project Level:** `.cursor/skills/`
- _Compatibility:_ Also supports `.claude/skills/`.
- _Note:_ Can be version-controlled with the project repository.

- **👤 User Level (Global):** `~/.cursor/skills/`
- _Compatibility:_ Also supports `~/.claude/skills/`.
- _Note:_ Personal skills available globally across all windows.

- _Reference:_ [Cursor Skills Documentation](https://cursor.com/docs/context/skills)

### 4. Codex

- **📂 Project Level:** `.codex/skills/`
- _Note:_ Supports version control; Codex searches recursively up to the repo root.

- **👤 User Level (Global):** `~/.codex/skills/`
- _Note:_ Can also be defined via the `$CODEX_HOME/skills` environment variable.

- _Reference:_ [Codex Skills Documentation](https://developers.openai.com/codex/skills/)

---

## 📝 Creation Workflow

1. **Create Directory**:
   Create a new folder in one of the configuration paths above: `mkdir skills/your-skill-name`
2. **Create Definition File (`SKILL.md`)**:
   The file must include YAML frontmatter.

```yaml
---
name: your-skill-name
description: Brief description of what this skill does
---

# Goal
A clear statement of the skill's purpose.

# Instructions
Detailed step-by-step instructions or prompt rules.

# Examples
Input and output examples.

```

## 🎯 Best Practices

- **Naming Convention**: Use lowercase with hyphens (e.g., `git-commit-helper`).
- **Single Responsibility**: Each Skill should focus on solving one specific problem.
- **Self-Contained**: Include full context in `SKILL.md` to minimize external dependencies.
- **Dependencies**: Explicitly state any required environment tools (e.g., Python, Node.js) in the documentation.

## 📚 Existing Skills Example

- **vocabulary**: English learning assistant. Provides simple definitions, everyday examples, and memory tips to help beginners understand words and phrases.

---

## 🤝 Contributing

1. Fork this repository.
2. Create a new Skill following the structure above.
3. Test it in your target IDE.
4. Submit a Pull Request.
