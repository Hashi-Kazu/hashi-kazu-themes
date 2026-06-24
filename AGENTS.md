# hashi-kazu-themes

Ado の楽曲をイメージした VS Code 向けダークカラーテーマ集。**ビルド不要・JSONのみ**の拡張機能。

## 構成

```
themes/                 # カラーテーマ本体（*-color-theme.json）
package.json            # 拡張マニフェスト（contributes.themes に各テーマを登録）
.github/workflows/      # publish.yml = main push で自動公開
```

- ソースコード・ビルド・テストは無い。`themes/*.json` と `package.json` がすべて。
- 発行者は **`Hashi-Kazu`**（マーケットプレイスの他拡張と共通）。

## 公開フロー（重要）

main へ push すると GitHub Actions（`.github/workflows/publish.yml`）が
`npx @vscode/vsce publish` で **VS Code Marketplace へ自動公開**する。

**作業のたびに必ず：**

1. `themes/*.json` または `package.json` を編集
2. **`package.json` の `version` を上げる**（必須。同じバージョンは再公開できず CI が失敗する）
   - テーマの色調整など軽微な変更 → パッチ（例 1.0.0 → 1.0.1）
   - テーマ追加など → マイナー（例 1.0.0 → 1.1.0）
3. `git push`（→ Actions が公開）

公開には Actions シークレット `VSCE_PAT`（Azure DevOps の PAT / Marketplace=Manage スコープ）を使用。

## テーマを追加するとき

1. `themes/<name>-color-theme.json` を作成
2. `package.json` の `contributes.themes` に1エントリ追記（`label` / `uiTheme` / `path`）
3. `version` をマイナーアップ → push

## アーキテクチャ判断

重要な設計判断は `docs/adr/` に記録されている。
新機能実装や既存コードの変更前に、関連するADRを確認すること。

## 注意

- `*.vsix`（ビルド成果物）は `.gitignore` で除外。コミットしない。
- 改行は LF 固定（`.gitattributes`）。
- このリポジトリには `_agent-templates` のサブエージェント（feature-dev 等）は**適用しない**。コード/テスト/仕様書を前提とするため、JSONテーマには不要。
