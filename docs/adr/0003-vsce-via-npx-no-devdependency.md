# ADR-0003: vsce を devDependency に含めず npx で実行

## ステータス
採用

## 確信度
中（`package.json` に `devDependencies` が存在せず `node_modules/` も持たないことから推測。明示的なコメントや議論の痕跡はなし）

## コンテキスト
JSON 専用構成（ADR-0001）のためローカルに npm パッケージが不要。
しかし CI で `vsce publish` を実行するには `@vscode/vsce` が必要になる。
`devDependencies` に追加すると `package-lock.json` が生まれ、依存更新の維持コストが発生する。

## 決定
CI の publish ステップで `npx @vscode/vsce publish` を実行し、`@vscode/vsce` を `devDependencies` に追加しない。

## 理由
ローカル開発で `node_modules` が不要な JSON 専用リポジトリにおいて、vsce 1 パッケージのためだけに `package-lock.json` を管理するのは過剰である。
`npx` を使えば CI 実行時に最新の `@vscode/vsce` が都度インストールされ、バージョン固定のメンテナンスが不要になる。

## 捨てた選択肢
- **`devDependencies` に `@vscode/vsce` を追加** → `package-lock.json` の維持・定期更新が必要になり、JSON のみの軽量リポジトリの趣旨と合わない。
- （その他の選択肢については調査時点で痕跡なし）

## 影響範囲
- `.github/workflows/publish.yml` の publish ステップ：`npx @vscode/vsce publish` の形式を維持すること。
- `node_modules/` および `package-lock.json` はリポジトリに存在しない設計。誤って追加しないよう注意。
