# 05_依頼受付->分類->担当割当 - DB Structure

## Overview

新規依頼を受け付けて分類し、優先度とSLAに基づいて担当割当まで行う。

## Database: Requests DB

| プロパティ名 | 型 | 必須 | 説明 |
|---|---|---|---|
| 依頼タイトル | Title | Yes | 依頼の件名 |
| 依頼者 | Text | Yes | 氏名またはメール |
| 依頼元チャネル | Select | No | Email / Slack / Form / Other |
| カテゴリ | Select | Yes | バグ報告 / 機能要望 / 問い合わせ / 見積依頼 / その他 |
| 優先度 | Select | Yes | 緊急 / 高 / 中 / 低 |
| SLA期限 | Date | Yes | 優先度またはカテゴリから設定 |
| 担当者 | Person | No | 自動または手動割当 |
| ステータス | Status | Yes | 未対応 / 対応中 / 完了 / 却下 |
| 依頼内容 | Text | Yes | 詳細本文 |
| テンプレ返信 | Text | No | 返信草案 |
| 関連タスク | Relation -> Tasks DB | No | 実行タスクへの変換先 |
| 関連プロジェクト | Relation -> Projects DB | No | 関連案件 |
| 作成日時 | Created time | Yes | 自動 |
| 更新日時 | Last edited time | Yes | 自動 |

## Optional support DB

### Routing Rules DB（任意）
- カテゴリ、キーワード、優先度、割当先を定義
- エージェントの自動判定ルールとして参照

### SLA Rules DB（任意）
- カテゴリ別または優先度別の期限設定を管理

## View design

### 1) 受信トレイ
- フィルター: `ステータス=未対応`
- ソート: `作成日時` 降順

### 2) 高優先度
- フィルター: `優先度 in (緊急, 高)` AND `ステータス != 完了`
- ソート: `SLA期限` 昇順

### 3) 担当者別ボード
- グループ: `担当者`
- フィルター: `ステータス in (未対応, 対応中)`

### 4) 完了アーカイブ
- フィルター: `ステータス in (完了, 却下)`
- ソート: `更新日時` 降順

## Naming conventions

- 依頼タイトル: `[カテゴリ] 要約`
- タスク変換時: `REQ-{YYYYMMDD}-{連番}` を付与（任意）

## Credit-aware operation

- 初回分類はタイトルと本文先頭のみ参照
- ルール判定は `Routing Rules DB` の少数条件に限定
- 自動実行は高頻度にせず、バッチまたはイベント駆動で運用

## Rollback design

- 自動判定の結果は必ず `ステータス=未対応` で保存
- 担当割当は上書き前に履歴をメモ欄へ残す（またはActivity Log）
- 誤割当時は担当者と優先度を手動修正し再判定
