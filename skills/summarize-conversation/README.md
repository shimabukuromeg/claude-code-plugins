# summarize-conversation

Claude との会話内容をマークダウンファイルにまとめて保存する Claude Code プラグインです。

## Overview

このプラグインは、調査や議論の結果を日本語のマークダウンファイルとして保存します。ファイル名は調査内容を反映した日本語名で自動生成されます。

## Installation

```
/plugin marketplace add shimabukuromeg/claude-code-plugins
/plugin install summarize-conversation@shimabukuromeg/claude-code-plugins
```

## Usage

会話の途中や終了時に、以下のようなフレーズでスキルが発動します。

### Trigger Examples

- 「調査した結果をまとめて」
- 「マークダウンで整理して」
- 「調査内容を保存して」
- 「会話をまとめて」
- 「レポートを作成して」

## Features

- 会話内容の自動要約
- `_docs` ディレクトリへの自動保存（ディレクトリがなければ作成）
- 日本語ファイル名の自動生成（例: `_docs/React Server Components の調査.md`）
- 構造化されたマークダウンフォーマット
- コードスニペットの適切な整形
- 参考リンクの収集
- 次のステップ（TODO）の抽出

## Output

生成されるマークダウンファイルには以下が含まれます:

- 概要（調査の背景・目的）
- 調査内容（セクション分け）
- 結論・まとめ
- 参考リンク
- 次のステップ（該当する場合）

## Plugin Structure

```
summarize-conversation/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── summarize-conversation/
│       └── SKILL.md
└── README.md
```

## License

MIT
