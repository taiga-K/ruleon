# プラグインの追加

`plugins/` 配下に新しいプラグインを追加し、`.cursor-plugin/marketplace.json` に登録します。

## 1. プラグインディレクトリを作成する

新しいフォルダを作成します:

```text
plugins/my-new-plugin/
```

必須となるマニフェストファイルを追加します:

```text
plugins/my-new-plugin/.cursor-plugin/plugin.json
```

マニフェストの例:

```json
{
  "name": "my-new-plugin",
  "displayName": "My New Plugin",
  "version": "0.1.0",
  "description": "Describe what this plugin does",
  "author": {
    "name": "Your Org"
  },
  "logo": "assets/logo.svg"
}
```

## 2. プラグインコンポーネントを追加する

必要なコンポーネントのみを追加します:

- `rules/`: `.mdc` ファイル（YAML frontmatter 必須）
- `skills/<skill-name>/SKILL.md`（YAML frontmatter 必須）
- `agents/*.md`（YAML frontmatter 必須）
- `commands/*.(md|mdc|markdown|txt)`（frontmatter 推奨）
- `hooks/hooks.json` および `scripts/*`: 自動化フック
- `mcp.json`: MCP サーバー定義
- `assets/logo.svg`: マーケットプレイス表示用ロゴ

## 3. マーケットプレイスマニフェストに登録する

`.cursor-plugin/marketplace.json` を編集し、新しいエントリを追加します:

```json
{
  "name": "my-new-plugin",
  "source": "./plugins/my-new-plugin",
  "description": "Describe your plugin"
}
```

`source` は、リポジトリルートからプラグインフォルダへの相対パスです。

## 4. 検証する

```bash
node scripts/validate-template.mjs
```

コミットする前に、報告されたすべてのエラーを修正してください。

## 5. よくある落とし穴・注意点

- プラグインの `name` が kebab-case（英小文字とハイフン）になっていない。
- マーケットプレイスマニフェスト内の `source` パスが実際のフォルダ名と一致していない。
- プラグインフォルダ内に `.cursor-plugin/plugin.json` が存在しない。
- skills、agents、commands に必須の frontmatter キー（`name`, `description`）が抜けている。
- ルールファイルに frontmatter の `description` が抜けている。
- MCP サーバー定義のファイル名に `mcp.json` 以外を使用している。
- マニフェストファイル内の `logo`、`hooks`、`mcpServers` で指定した相対パスが切れている（存在しないパスを参照している）。
