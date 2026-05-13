# CLAUDE.md — windows-learn

> 『Windows Internals』Part 1 / Part 2 を ReactOS 実装と突き合わせて読む個人公開学習リポジトリ。NEC 業務ではない。

## 起動時手順

1. 該当タスクの条文を `.claude/rules/meta.md` の条番号インデックスから lazy load 宣言（第1条）
2. 関連 docs（`LEARNING-PLAN.md` / `notes/README.md` / 該当ノート）を最初に Read し「完全パス + 1 文要約 + タスク関連性」を出力、タスク末尾でも再掲
3. session 開始（新規 chat / `/clear` 直後）: chat paste 引継ぎがなければ `notes/daily/` の最新ファイル + `LEARNING-PLAN.md` 進捗から再開
4. 章サマリ・topic ノートを完成と認定する前に別エージェントレビュー（第15条）

## ルール一覧

`@import` で常時 load:

@.claude/rules/note-quality.md
@.claude/rules/verify-understanding.md

| タスク種別 | rules | 含む条 |
|-----------|-------|-------|
| ノート作成・編集 | `note-quality.md` (常時) | 第3, 5, 19, 21 |
| 章完了・日次記録 | `verify-understanding.md` (常時) | 第7, 9 |
| 学習進捗管理 | `study-flow.md` (path-scope) | 第11, 13 |
| 章サマリ完成レビュー | `review.md` (path-scope) | 第15 |
| `CLAUDE.md` / `.claude/` 編集 | `governance.md` (path-scope) | 第17 (A〜F) |

## ルート構成

- `LEARNING-PLAN.md` 52 週学習計画
- `README.md` プロジェクト紹介（公開向け）
- `notes/` 学習ノート（詳細 `notes/README.md`）
- `.claude/rules/` Claude 用規約（条文）
- `.pdf/` `.oss/` ローカル専用（gitignore: 書籍 PDF / ReactOS clone）

## 親 CLAUDE.md との関係

`~/CLAUDE.md` の NEC ブランド・NEC IP・`nec-pptx` 等 NEC 業務関連指示は **本リポジトリでは適用外**。応答スタイル（romaji 入力 → 日本語応答）等の一般ルールのみ継承。

---
*40 行 / 1.92 KB*
