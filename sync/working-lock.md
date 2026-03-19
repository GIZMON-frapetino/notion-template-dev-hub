# Working Lock

同時編集の衝突を避けるため、今触っている対象を宣言します。

## Format

| Status | Owner | Tool | Target Path | ETA | Note |
|---|---|---|---|---|---|
| open | your-name | Cursor | templates/04-weekly-status-update | 2026-03-19 | 初期整備 |

## Rule

- 作業開始時に `open` を追加
- 完了時に `closed` へ更新
- 同一ターゲットでの並行編集は避ける
