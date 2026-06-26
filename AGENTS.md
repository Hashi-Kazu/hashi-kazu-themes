# hashi-kazu-themes

Ado songs inspired dark color themes for VS Code. Build-free, JSON-only extension.

## 必須ルール

- このリポジトリには `_agent-templates` のサブエージェント（`feature-dev` など）は適用しない。
- 変更対象は基本的に `themes/*.json` と `package.json`。
- テーマ変更時は `package.json` の `version` を必ず上げる。同じ version は Marketplace に再公開できない。
- テーマ追加時は `themes/<name>-color-theme.json` を作成し、`package.json` の `contributes.themes` に登録する。
- `*.vsix` はコミットしない。
- アーキテクチャ変更時は `docs/adr/` を確認・更新する。

## 必要時に読む詳細

- 技術スタック・構成確認時: `docs/ai/project-overview.md`
- リリース・公開判断時: `docs/ai/release-policy.md`
- アーキテクチャ判断時: `docs/adr/`

## よく使う確認

```bash
git status -sb
git diff --stat
```

## publisher 最短フロー

publisher は以下だけ行う:

1. `git status -sb`
2. `git diff --stat`
3. `package.json` の version が変更内容に合っていることを確認
4. 必要な変更だけ stage
5. commit
6. push

禁止:

- リポジトリ全体の再調査
- docs 全体の読み直し
- 不要なレビュー
- 存在しない build/test の実行
- `*.vsix` の stage

## 参照先

- 技術スタック・構成: `docs/ai/project-overview.md`
- リリース運用: `docs/ai/release-policy.md`
- ADR: `docs/adr/`
