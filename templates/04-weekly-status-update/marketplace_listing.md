# 04_週報自動生成 - Marketplace Listing Draft

## タイトル案

- 週報自動生成テンプレート（Notion Agent対応）
- Tasks/Projects連携 週次ステータス自動レポート

## Short description

金曜17時に、タスク進捗を自動集計して週報ドラフトを作成。  
確認して共有するだけで、週報作成の手間を大幅に削減できます。

## Long description

このテンプレートは、`Tasks DB` と `Projects DB` の情報をもとに、週次レポートを自動生成するための Notion テンプレートです。  
`Weekly Reports DB` に `下書き` として生成されるため、内容確認後に安全に共有できます。

### できること

- 対象期間の完了タスク数を自動集計
- KPI/成果、課題、次週優先事項を要約
- 週報フォーマットを統一し、チーム共有を高速化

### できないこと

- 指定外DBの自動参照
- 根拠のない数値推定
- 既存週報の自動上書き

### セット内容

- `db_structure.md`（DB定義）
- `agent_instructions.md`（コピペ運用可能）
- `setup_guide.md`（導入手順）

### 推奨ユーザー

- 毎週の進捗共有を定例化したいチーム
- 週報作成に毎回30分以上かかっている個人/PM

### セキュリティと運用

- 最小権限（対象DB限定）
- 下書き生成 -> 人の確認 -> 共有 の承認フロー
- 誤作成時のロールバック手順あり

### クレジット配慮

- 対象期間のみを集計
- 実行頻度は週1回を推奨
- 不要フィールドを取得しない低燃費設計

## 検索タグ案

- Weekly Report
- Team Productivity
- Project Management
- Notion AI
- Japanese Workflow
