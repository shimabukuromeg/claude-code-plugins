# claude-code-plugins

A collection of personal Claude Code utilities and custom skills.

## Overview

This repository contains a Claude Code plugin marketplace that provides custom skills to enhance your Claude Code workflow. The plugins are designed to help with common development tasks like dependency update reviews.

## Installation

### From Claude Code (Recommended)

You can install plugins directly from Claude Code using the plugin management system:

1. Add this repository as a marketplace:
   ```
   /plugin marketplace add shimabukuromeg/claude-code-plugins
   ```

2. Install the plugins:
   ```
   /plugin install renovate-check@shimabukuromeg/claude-code-plugins
   ```

3. Restart Claude Code to activate the plugins.

### Manual Installation

Alternatively, you can clone this repository and use it as a local marketplace:

```bash
git clone https://github.com/shimabukuromeg/claude-code-plugins.git
```

Then in Claude Code:
```
/plugin marketplace add ./claude-code-plugins
```

## Available Plugins

| Plugin | Description |
|--------|-------------|
| [renovate-check](skills/renovate-check/) | Renovate PR の依存関係更新を詳細にチェックし、日本語でレポートを作成する |
| [summarize-conversation](skills/summarize-conversation/) | 会話の内容をマークダウンファイルにまとめて保存する |

See each plugin's README for detailed usage and features.

## Plugin Structure

This repository is organized as a plugin marketplace containing multiple plugins:

```
.claude-plugin/
└── marketplace.json    # Marketplace metadata

skills/
├── renovate-check/           # renovate-check plugin
│   ├── .claude-plugin/
│   │   └── plugin.json
│   ├── skills/
│   │   └── renovate-check/
│   │       └── SKILL.md
│   └── README.md
└── summarize-conversation/   # summarize-conversation plugin
    ├── .claude-plugin/
    │   └── plugin.json
    ├── skills/
    │   └── summarize-conversation/
    │       └── SKILL.md
    └── README.md

commands/               # Custom commands (placeholder)
agents/                 # Custom agents (placeholder)
```

## Contributing

Feel free to fork this repository and add your own custom commands, agents, or skills.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
