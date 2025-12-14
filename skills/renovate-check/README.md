# renovate-check

Renovate が作成した依存関係更新 PR を包括的に分析し、日本語でレポートを作成する Claude Code プラグインです。

## Overview

このプラグインは、Renovate が作成した PR を自動的に分析し、Breaking Changes の検出、リポジトリ内での利用箇所の特定、依存関係の互換性チェックなどを行います。

## Installation

```
/plugin marketplace add shimabukuromeg/claude-code-plugins
/plugin install renovate-check@shimabukuromeg/claude-code-plugins
```

## Usage

Renovate PR の URL を渡すか、依存関係更新の PR をレビューする際に自動的にスキルが発動します。

### Trigger Examples

- 「この Renovate PR をチェックして」
- 「https://github.com/owner/repo/pull/123 の内容を確認して」
- 「依存関係の更新 PR をレビューして」

## Features

- Renovate PR の自動分析
- セマンティックバージョニングに基づくリスク評価（Major/Minor/Patch）
- Breaking Changes の検出と影響分析
- リポジトリ内での利用箇所の特定
- 依存関係の互換性チェック
- 日本語でのレポート生成
- PR へのコメント自動投稿

## Output

レポートには以下の内容が含まれます:

- 基本情報（パッケージ名、バージョン変更、変更種別）
- 変更内容サマリー
- Breaking Changes の有無と詳細
- 利用箇所の一覧
- 依存関係の互換性
- 環境要件の変更
- ツール互換性
- リスク評価と推奨アクション
- 参考リンク

## Requirements

- `gh` CLI（GitHub CLI）
- `jq`（JSON 処理）

## Plugin Structure

```
renovate-check/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── renovate-check/
│       └── SKILL.md
└── README.md
```

## License

MIT
