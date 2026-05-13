---
name: governance
description: CLAUDE.md / rules 肥大化防止 (windows-learn)
paths:
  - "CLAUDE.md"
  - ".claude/**"
---

# governance — 第17条 肥大化防止 (A〜F)

## A. サイズ閾値（参考値・硬性基準ではない）

| 対象 | 剪定検討 | 構造見直し |
|---|---|---|
| `CLAUDE.md` 本体 | 概ね 50 行 / 5KB | 概ね 100 行 / 10KB |

公式 (Anthropic Best Practices) は数値閾値を持たない（"Keep it concise"）。本リポジトリは観察基準「Claude が指示を無視し始めた兆候の有無」を**数値より優先**する。

## B. 新項目ルーティング

| 種別 | 振り分け先 |
|---|---|
| 全タスク共通の規約 | `.claude/rules/`（常時 load） |
| 特定タスク時の手順 | `.claude/rules/`（path-scope）or `notes/topics/` |
| 1 回限り・過渡 | `.tmp/`（gitignore 推奨） |
| 学習上の知識 | `notes/topics/` |

`CLAUDE.md` 直接記入は「起動時手順」「ルール参照テーブル」「ルート構成」「親 CLAUDE.md 関係」に限る。

## C. 公式準拠

`.claude/` 直下に作る subdir は公式定義（`rules` / `skills` / `commands` / `agents`）のみ。独自 subdir（例: `docs/`, `tmp/`）は `.claude/` に作らない（プロジェクト直下に配置する）。

## D. 定期レビュー

四半期ごとに公式 Best Practices ([Write an effective CLAUDE.md](https://code.claude.com/docs/en/best-practices#write-an-effective-claude-md)) を WebFetch で取得し、ドリフトがあれば修正計画を `notes/topics/_governance-drift-YYYY-Q.md` に記録する。

## E. 自動検証（hooks / 自動化機構の不採用宣言）

本リポジトリは **個人公開学習リポジトリ** であり、以下を不採用とする:

- **project-level hooks** (`.claude/settings.json` の `hooks` フィールド): 不採用。user-level `~/.claude/settings.json` の hooks（`SessionStart` 等 5 hook 構成）で十分
- **`issues/` 3 段階フォルダ管理** (open / processing / closed): 不採用。学習上の宿題・未消化は `notes/topics/_open-questions.md` で代替（解決時に削除 or 章ノートへ昇格）
- **handoff ファイル** (`.tmp/handoffs/`): 不採用。日次ログ `notes/daily/YYYY-MM-DD.md` の「次回ピックアップ」セクションが同等機能を果たす
- **`docs-management.md`** (rules 7 ファイル目): 不採用。`docs/` 配下に 5 section 以上の構造を持たないため（`notes/README.md` 単体で完結）

将来コラボや CI が必要になれば、本項を解除し標準セットを補完する。

## F. 常時 load ファイル 5KB soft cap

`@import` および常時 load される `.claude/rules/meta.md` / `note-quality.md` / `verify-understanding.md` は **各 5KB soft cap**。超えたら条文を path-scope rules に逃がすか、long-form を `notes/topics/` に分離してリンク化。
