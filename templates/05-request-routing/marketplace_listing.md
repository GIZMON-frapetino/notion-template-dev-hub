# 05_依頼受付->分類->担当割当 - Marketplace Listing Draft

## タイトル案

- 依頼受付を自動整理する Notion Task Router
- 問い合わせ分類と担当割当テンプレート（Notion Agent対応）

## Short description

受け付けた依頼を自動で分類し、優先度とSLAを設定、担当割当まで支援。  
窓口運用の属人化を減らし、対応漏れを防げます。

## Long description

このテンプレートは、`Requests DB` を中心に依頼受付フローを標準化するためのパッケージです。  
Task Router Agent と組み合わせることで、依頼の分類・優先度判定・SLA設定・担当割当を半自動化できます。

### できること

- 新規依頼のカテゴリ自動判定
- 優先度とSLA期限の設定
- 担当者割当の支援
- 返信テンプレート草案の自動生成

### できないこと

- 曖昧依頼の完全自動確定
- 既存レコードの削除・強制上書き
- 指定外DBへの自動更新

### セット内容

- `db_structure.md`
- `agent_instructions.md`
- `setup_guide.md`
- `marketplace_listing.md`

### 推奨ユーザー

- 問い合わせ対応が増えている小規模チーム
- タスク受付の整流化をしたいPM/運用担当

### セキュリティと運用

- 最小権限（Requests DB中心）
- 自動判定後は `未対応` で停止
- 人が確認して `対応中` へ進める安全フロー

### クレジット配慮

- 解析対象はタイトルと本文先頭を優先
- ルールDB判定を使って推論コストを削減
- 実行頻度を調整し高負荷運用を回避

## 検索タグ案

- Task Routing
- Service Desk
- Team Operations
- Notion AI
- Japanese Workflow
