# Notion Template Dev Hub

Notion Template / Custom Agent の設計、制作、販売、運用を GitHub で継続管理するためのハブです。

## What this repository solves

- 設計資料の分散を防ぐ
- Cursor/Claude での制作を同じ流れで再開できる
- Notion への出力と GitHub の正本管理を分離できる
- GitHub Pages で進捗や方針を共有できる

## Structure

- `docs/` GitHub Pages 向けドキュメント
- `context/` 会話再開用コンテキスト
- `templates/` テンプレート生成用の型
- `agents/` エージェント仕様とプロンプト
- `sources/` ツール別の作業コピー管理（GENSPARK / Antigravity / Cursor / Notion）
- `sync/` 同期ログと受け渡しメモ

## Resume from last conversation

次回の会話開始時は `context/resume-prompt.md` をそのまま貼り付けてください。

## Canonical source rule

- GitHub（このリポジトリ）を正本とする
- Notion は配布/表示先、設計の正本にしない
- 外部ツールで更新したら `sources/` と `sync/` を経由して正本へ反映する

## Suggested workflow

1. GENSPARK で詳細設計
2. `context/current-status.md` に要点を反映
3. `templates/` の型に落とし込む
4. Claude/Cursor で本文生成
5. `sources/` に受け渡し内容を保存
6. `sync/` に同期ログを記録
7. `docs/` と販売情報を更新
8. GitHub へコミット

## GitHub setup

```bash
git init
git add .
git commit -m "chore: initialize notion template dev hub"
git branch -M main
git remote add origin <your-repo-url>
git push -u origin main
```

GitHub Pages は repository settings で `GitHub Actions` を有効にすると `docs/` が公開されます。
