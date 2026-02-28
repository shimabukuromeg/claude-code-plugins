# n8n-business-automation

n8n ワークフローによるビジネスプロセス自動化の構築・テストを支援する Claude Code プラグインです。

## Overview

このプラグインは、n8n のコアノード（Webhook、HTTP Request、Set、Function、If）を使ったワークフローの作成、データフローの接続、テスト、デプロイをサポートします。

## Installation

```
/plugin marketplace add shimabukuromeg/claude-code-plugins
/plugin install n8n-business-automation@shimabukuromeg/claude-code-plugins
```

## Usage

n8n ワークフローの作成やテストに関する質問をすると自動的にスキルが発動します。

### Trigger Examples

- 「n8n で注文処理の自動化ワークフローを作って」
- 「Webhook トリガーから HTTP リクエストへのフローを設定して」
- 「条件分岐のあるワークフローを構築して」
- 「ワークフローのテスト方法を教えて」

## Features

- Webhook / Schedule トリガーの設定
- HTTP Request ノードによる外部 API 連携
- If / Switch ノードによる条件分岐
- Set ノードによるデータ変換
- テスト URL と本番 URL の使い分けガイド
- ワークフローの本番デプロイ手順
- 実行ステータスの監視

## Plugin Structure

```
n8n-business-automation/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── n8n-business-automation/
│       └── SKILL.md
└── README.md
```

## License

MIT
