# Architecture Decision Records

このディレクトリには、本リポジトリのアーキテクチャ上の決定とその理由を記録する。
新機能の実装や既存コードの変更前に、関連するADRを確認すること。

## 一覧

| 番号 | タイトル | ステータス | 確信度 | 概要 |
|---|---|---|---|---|
| [0001](./0001-build-free-json-only.md) | ビルドレス・JSON専用構成 | 採用 | 高 | ソースコード・ビルドなし、themes/*.json と package.json のみで拡張機能を構成 |
| [0002](./0002-github-actions-auto-publish.md) | GitHub Actions による main push 時自動公開 | 採用 | 高 | main への push で自動的に VS Code Marketplace へ公開、パスフィルター付き |
| [0003](./0003-vsce-via-npx-no-devdependency.md) | vsce を devDependency に含めず npx で実行 | 採用 | 中 | JSON 専用リポジトリに不要な package-lock.json を持ち込まない |
| [0004](./0004-dark-themes-only.md) | ダークテーマのみの提供 | 採用 | 中 | Ado の楽曲イメージに合わせ vs-dark のみ、ライトバリアントなし |
| [0005](./0005-remove-hashi-kazu-signature-theme.md) | Hashi-Kazu 署名テーマの削除 | 採用 | 高 | v1.1.0 で誤って追加したため v1.1.1 で削除 |

## ステータスの意味

- **採用**: 現在有効な決定
- **廃止**: 後続のADRに置き換えられた決定（廃止されたADRも削除せず残す）
- **要確認**: 推測で書かれた理由が本人未確認の状態（確認後「採用」に更新する）

## 新しいADRを追加する場合

1. `docs/adr/` 内の既存ファイルを確認し、最大連番の次の番号を採番する
2. `docs/adr/0001-build-free-json-only.md` の形式（MADR形式）に従って作成する
3. 本ファイルの一覧表に1行追加する
