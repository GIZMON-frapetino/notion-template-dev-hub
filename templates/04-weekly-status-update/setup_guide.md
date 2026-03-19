# 04_週報自動生成 - Setup Guide

## 目的

毎週の進捗を自動集計して、共有可能な週報を短時間で作成する。

## Prerequisites

- Notion ワークスペース（対象DBが存在）
- `Tasks DB`, `Projects DB`, `Weekly Reports DB`
- Status Update Agent の作成権限

## Step 1: DB を準備

1. `Weekly Reports DB` を作成
2. `db_structure.md` のプロパティを追加
3. ビュー（今週/確認待ち/共有済み）を作成

## Step 2: Agent を作成

1. Agent 名を `Status Update Agent` に設定
2. `agent_instructions.md` を貼り付け
3. 参照先 DB を次の3つに限定:
   - `Tasks DB`
   - `Projects DB`
   - `Weekly Reports DB`

## Step 3: 実行トリガーを設定

- 推奨: 毎週金曜 17:00
- まずは手動実行でテストし、問題なければ定期実行へ移行

## Step 4: 初回テスト

1. 対象期間を指定して実行
2. `Weekly Reports DB` に下書きが生成されることを確認
3. 数値と要約内容をレビュー
4. 問題なければ `共有済み` に変更

## 安全運用ルール

- 書き込みは `Weekly Reports DB` の新規作成のみ
- 既存の週報を上書きしない
- 不明なデータは空欄で返し、推測で埋めない

## ロールバック手順

1. 誤作成レコードを特定
2. `ステータス=アーカイブ` へ変更、または削除
3. 原因（期間指定/フィルター設定）を修正して再実行

## FAQ

### Q1. 完了タスク数が多すぎる
- 対象期間フィルターと完了条件を見直す

### Q2. 要約が抽象的
- タスク名の命名とプロジェクト紐付けを改善する

### Q3. クレジット消費が気になる
- 参照項目を減らし、実行頻度を週1回に固定する
