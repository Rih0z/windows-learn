---
name: review
description: 章サマリ・topic ノート完成時の別エージェントレビュー (windows-learn)
paths:
  - "notes/part1/**.md"
  - "notes/part2/**.md"
  - "notes/topics/**.md"
---

# review

## 第15条 — 章サマリ・topic 完成時の別エージェントレビュー

`notes/part1|part2/chNN-<slug>.md` および `notes/topics/<slug>.md` を完成と認定する前に、別エージェントへレビューを依頼する。

### 評価基準

`verify-understanding.md` 第7条チェックリスト + 以下の追加項目:

1. ReactOS 引用が **SHA 付き permalink** で固定されているか（master ではないこと）
2. ReactOS 引用が最小限か（大量コピペになっていないか）
3. NEC 業務情報・社内パス・社内ツール名が混入していないか（公開リポジトリ）
4. 書籍と実装の差分・気付き欄が空でないか

### 合否

- 合格: 全項目 Y
- 不合格: 修正して再レビュー。**3 回 FAIL** で章完了を見送り、`notes/topics/_open-questions.md` に未消化として記録

### レビュア渡し物

diff + 評価基準のみ。学習意図・会話履歴は渡さない。
