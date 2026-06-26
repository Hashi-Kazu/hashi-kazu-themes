# Project Overview

## 概要

Ado の楽曲をイメージした VS Code 向けダークカラーテーマ集。ビルド不要・JSON のみの拡張機能。

## 構成

```text
themes/                 # カラーテーマ本体（*-color-theme.json）
package.json            # 拡張マニフェスト（contributes.themes に各テーマを登録）
.github/workflows/      # publish.yml = main push で自動公開
```

- ソースコード・ビルド・テストはない。
- `themes/*.json` と `package.json` が主な管理対象。
- 発行者は `Hashi-Kazu`。

## テーマを追加するとき

1. `themes/<name>-color-theme.json` を作成する。
2. `package.json` の `contributes.themes` に `label` / `uiTheme` / `path` を追記する。
3. `package.json` の `version` をマイナーアップする。

## 注意事項

- `*.vsix` は `.gitignore` で除外。コミットしない。
- 改行は LF 固定（`.gitattributes`）。
