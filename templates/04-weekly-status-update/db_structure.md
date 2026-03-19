# 04_週報自動生成 - DB Structure

## Overview

週次で `Tasks DB` と `Projects DB` を集計し、`Weekly Reports DB` に要約レコードを生成する。

## Database: Weekly Reports DB

| プロパティ名 | 型 | 必須 | 説明 |
|---|---|---|---|
| レポート名 | Title | Yes | 例: `2026-W12 週報` |
| 対象期間 | Date | Yes | 月曜から金曜 |
| ステータス | Status | Yes | `下書き` / `確認待ち` / `共有済み` |
| 完了タスク数 | Number | Yes | 対象期間内に完了した件数 |
| KPI/成果指標 | Text | Yes | 主要成果を要約 |
| 来週の優先事項 | Text | Yes | 次週の重点タスク |
| 学び・気づき | Text | No | 振り返り |
| リスク/課題 | Text | No | ブロッカー・懸念 |
| 関連プロジェクト | Relation -> Projects DB | No | 対象プロジェクト |
| 参照タスク | Relation -> Tasks DB | No | 根拠タスク |
| 作成者 | Person | No | レポート作成者 |
| 作成日時 | Created time | Yes | 自動 |

## View design

### 1) 今週レポート
- フィルター: `対象期間` が今週
- ソート: `作成日時` 降順

### 2) 確認待ち
- フィルター: `ステータス` = `確認待ち`

### 3) 共有済みアーカイブ
- フィルター: `ステータス` = `共有済み`
- ソート: `対象期間` 降順

## Naming conventions

- レポート名: `YYYY-Www 週報`
- KPI見出し: `成果`, `課題`, `次アクション`

## Credit-aware operation

- 集計対象は `対象期間` に限定（全件走査をしない）
- 取得フィールドを最小化（タイトル、ステータス、完了日、プロジェクトのみ）
- 実行頻度は週1回固定（推奨: 金曜17:00）

## Rollback design

- 自動生成レコードは `ステータス=下書き` で作成
- 承認前に公開共有しない
- 誤作成時は該当レコードを削除、または `アーカイブ` ステータスへ変更
