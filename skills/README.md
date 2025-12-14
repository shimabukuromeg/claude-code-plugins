# Skills

This directory contains custom skills for Claude Code.

## Available Skills

### renovate-check

Renovate が作成した依存関係更新 PR を包括的に分析し、日本語でレポートを作成する。

See [renovate-check/README.md](renovate-check/README.md) for details.

## How to Add a Skill

Create a new directory with the following structure:

```
skills/
└── your-skill/
    ├── .claude-plugin/
    │   └── plugin.json
    ├── skills/
    │   └── your-skill/
    │       └── SKILL.md
    └── README.md
```
