---
name: study-flow
description: 学習進捗管理フロー (windows-learn)
paths:
  - "notes/daily/**"
  - "notes/part*/**"
  - "notes/topics/**"
  - "LEARNING-PLAN.md"
---

# study-flow

## 第11条 — 日次 → 週次 → 章完了 更新フロー

| 区分 | 時間配分 | 出力 |
|---|---|---|
| 平日 1 セッション | 50 分（読書 + ReactOS 照合 + 観測）+ 10 分（ログ） | `notes/daily/YYYY-MM-DD.md` を `_TEMPLATE.md` ベースで作成 |
| 金曜 1 セッション | 30 分（範囲読み）+ 30 分（振り返り） | 上記 + `notes/daily/YYYY-MM-DD-weekly.md` を `_WEEKLY-REVIEW-TEMPLATE.md` ベースで作成 |
| 章完了 | — | `notes/part{1,2}/chNN-<slug>.md` 仕上げ → `notes/README.md` 章インデックス追記 → `LEARNING-PLAN.md` 該当チェックボックス ✅ |

## 第13条 — 計画ズレ検知

週次レビュー時、`LEARNING-PLAN.md` の現在週と実進捗が **±2 週以上** ズレたら、週割を後ろ倒し or 章サブゴール（非 ★ 項目）削減。完璧主義回避。
