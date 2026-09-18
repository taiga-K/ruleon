# ruleon

組織設計のルールデザイン思想に基づき、AI駆動開発のハーネスを自律的に進化させる実験的プラグイン。

このリポジトリは、公式の [Cursor plugin template](https://github.com/cursor/plugin-template) を基盤として取り込んだ Cursor プラグイン管理リポジトリです。見本プラグイン（`starter-simple`, `starter-advanced`）は削除済みで、マルチプラグイン構成を標準としています。

---

## はじめかた

1. `.cursor-plugin/marketplace.json`: マーケットプレイスの `name`、`owner`、および `metadata` を設定します。
2. `plugins/<plugin-name>/.cursor-plugin/plugin.json`: プラグインの `name`（英小文字の kebab-case）、`displayName`、`author`、`description`、`keywords`、`license`、`version` を設定します。
3. ルール（rules）、スキル（skills）、エージェント（agents）、コマンド（commands）、フック（hooks）、スクリプト（scripts）、ロゴ（logo）を追加します。

プラグインの新規追加手順については、[docs/add-a-plugin.md](docs/add-a-plugin.md) を参照してください。

## 単一プラグイン構成 vs マルチプラグイン構成

このテンプレートは、1つのリポジトリで複数のプラグインを管理する **マルチプラグイン構成** を標準としています。

**単一プラグイン構成**（1リポジトリ1プラグイン）にする場合は、プラグインフォルダの中身をリポジトリルートに移動し、ルートに `.cursor-plugin/plugin.json` を1つだけ配置した上で、`.cursor-plugin/marketplace.json` を削除してください。

## 提出前チェックリスト

- 各プラグインに有効な `.cursor-plugin/plugin.json` が存在する。
- プラグイン名が一意であり、英小文字の kebab-case になっている。
- `.cursor-plugin/marketplace.json` の各エントリが、実在するプラグインフォルダを参照している。
- ルール、スキル、エージェント、コマンドの各ファイルに必要な frontmatter メタデータがすべて記載されている。
- ロゴ画像がコミットされており、相対パスで参照されている。
- `node scripts/validate-template.mjs` の検証を通過している。
- Cursor チーム（Slack または `kniparko@anysphere.com`）への提出準備ができている。
