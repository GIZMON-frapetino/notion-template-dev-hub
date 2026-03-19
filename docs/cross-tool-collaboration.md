# Cross Tool Collaboration Guide

## Goal

GENSPARK / Antigravity / Cursor / Notion を併用しつつ、品質と履歴を GitHub で一元管理する。

## Single source of truth

- 正本: `notion-template-dev-hub`（GitHub）
- 作業コピー: `sources/`
- 公開先: Notion Marketplace / Notion Sites

## Tool roles

- GENSPARK: 詳細設計、競合調査、戦略の下書き
- Antigravity: 既存資産の参照と素材管理
- Cursor: 実装、整形、差分レビュー、構造管理
- Notion: 実運用、デモ、配布

## Sync cycle

1. 外部ツールで更新
2. 対応する `sources/<tool>/` に要点を保存
3. テンプレ本体（`templates/`, `agents/`）へ反映
4. `sync/changelog.md` に同期記録を追記
5. コミット

## Commit convention (recommended)

- `feat:` 新規テンプレ/機能追加
- `fix:` 内容修正
- `docs:` 説明文/ガイド更新
- `chore:` 構造・運用メンテ

## Conflict prevention

- 1テーマ1ブランチ
- 同時編集時は `sync/working-lock.md` で作業対象を宣言
- 先に `sync/changelog.md` を更新してから本文編集
