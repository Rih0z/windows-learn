---
name: note-quality
description: ノート記述規約 (windows-learn)
---

# note-quality

## 第3条 — 章サマリ・topic ノート構造

`notes/part1|part2/chNN-<slug>.md` および `notes/topics/<slug>.md` は **6 セクション** で統一する:

1. 書籍の要点（3〜5 個）
2. 登場する構造体・関数
3. ReactOS 実装対応（commit SHA permalink）
4. 書籍と実装の差分・気付き
5. WinDbg / Sysinternals 観測
6. 疑問・宿題

詳細・例は `notes/README.md` を参照。

## 第5条 — ReactOS 引用

- ReactOS コードへのリンクは **master ブランチではなく commit SHA の GitHub permalink** で固定する（コードが変わるとリンク内容が変わるため）
- 引用は最小限（数行 + 該当行リンク）。大量コピペ禁止

## 第19条 — ノート命名・配置

| 種別 | パス |
|---|---|
| 章サマリ | `notes/part1\|part2/chNN-<slug>.md`（NN は 2 桁ゼロ詰め） |
| 横断テーマ | `notes/topics/<slug>.md` |
| 日次ログ | `notes/daily/YYYY-MM-DD.md`（同日複数は `-2`, `-3` を付加） |
| 週次レビュー | `notes/daily/YYYY-MM-DD-weekly.md` |

新規追加時は `notes/README.md` の章インデックスに 1 行追記する。

## 第21条 — 公開リポジトリ規律

NEC 業務情報・社内資料・顧客名・社内パス・社内ツール名を含めない。
