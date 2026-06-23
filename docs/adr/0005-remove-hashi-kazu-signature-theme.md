# ADR-0005: Hashi-Kazu 署名テーマの削除

## ステータス
採用

## 確信度
高（本人より確認済み）

## コンテキスト
v1.1.0 でパブリッシャー名「Hashi-Kazu」を冠した個人署名テーマ（`themes/hashi-kazu-color-theme.json`）が追加された。
v1.1.1 でこのテーマは削除され、同時に拡張機能の displayName が "Hashi Kazu Themes" から "Hashi-Kazu テーマ"（日本語）に変更された。

## 決定
「Hashi-Kazu」テーマを拡張機能のテーマ一覧から除外し、パブリッシャー名はブランド表記（displayName）として残す。

## 理由
誤って追加したテーマであり、意図的な設計判断ではなく単純な操作ミスのため削除した。

## 捨てた選択肢
- **Hashi-Kazu テーマを継続提供** → v1.1.0 で一度採用されたが v1.1.1 で取り消されたため、何らかの判断が働いたと推定。
- （その他の選択肢については調査時点で痕跡なし）

## 影響範囲
- `themes/hashi-kazu-color-theme.json` はファイルとして残っているが `package.json` の `contributes.themes` から除外されている。
  再追加する場合は `package.json` にエントリを追記しバージョンを上げること。
