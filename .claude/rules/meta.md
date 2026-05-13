---
name: meta
description: 条番号インデックス・既知の制約・常時 load 5KB cap (windows-learn)
---

# meta — 条番号インデックス

| 条 | 内容 | 所在 |
|---|---|---|
| 第1条 | lazy load 宣言運用 | meta.md |
| 第3条 | 章サマリ・topic ノート構造 | note-quality.md |
| 第5条 | ReactOS 引用は SHA 付き permalink + 最小限 | note-quality.md |
| 第7条 | 章完了受入基準 | verify-understanding.md |
| 第9条 | 日次ログ最低要件 | verify-understanding.md |
| 第11条 | 日次 → 週次 → 章完了 更新フロー | study-flow.md |
| 第13条 | 計画ズレ検知 | study-flow.md |
| 第15条 | 章サマリ・topic 完成時の別エージェントレビュー | review.md |
| 第17条 | 肥大化防止 (A〜F) | governance.md |
| 第19条 | ノート命名・配置 | note-quality.md |
| 第21条 | 公開リポジトリ規律 | note-quality.md |

## 第1条 — lazy load 宣言運用

タスク開始時、該当する条のみを宣言してから着手する。全条一括宣言は不要（宣言が長文化すると Claude 自身が宣言を無視する原因になる）。条の所在は上表で引く。

## 既知の制約

- Claude Code の `paths:` frontmatter による path-scope rules auto-load は **Read 時のみ発火、Write/Create 時には不発火** という既知 bug がある（[claude-code Issue #23478](https://github.com/anthropics/claude-code/issues/23478)）。本リポジトリでは `@import` 一次防御 + 第1条手動宣言を二次防御とする。

## 常時 load 5KB soft cap (第17条 F)

本ファイル / `note-quality.md` / `verify-understanding.md` は各 **5KB を超えない**。超えたら条文を path-scope rules に逃がす。
