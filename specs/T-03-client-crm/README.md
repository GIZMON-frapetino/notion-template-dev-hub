# T-03 案件・クライアントCRM

フリーランス向けのクライアント〜商談〜案件〜コミュニケーション履歴を一気通貫管理する Notion テンプレート群の仕様です。

## ドキュメント

| ファイル | 内容 |
|---|---|
| [specification.md](./specification.md) | 製品概要・DBスキーマ・ビュー・リレーション・ワークフロー |
| [operations.md](./operations.md) | セットアップ・最小運用ルール・振り返り・AI活用・FAQ |
| [api-integration.md](./api-integration.md) | Notion API / MCP 向けプロパティ型・`pages.create` JSON・前処理・制約 |

## 関連（Notion 側）

- [T-03 運用方法](https://www.notion.so/T-03-ec9fcb031725824cb57681a8c0a77c1d)
- [T-03 API連携仕様書](https://www.notion.so/T-03-API-2b9ac2dff4364a21bcdff7e741e87c4b)

## 運用メモ

- **GitHub の `specification.md` / `operations.md` / `api-integration.md` を正本**とし、Notion 側は配布・レビュー用に同期する。
- Notion を更新したら `sync/changelog.md` に記録し、差分を GitHub に反映する。
