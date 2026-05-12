# CLAUDE.md — windows-learn

公開 GitHub リポジトリ。『Windows Internals』を ReactOS 実装と突き合わせて読む個人学習用。NEC 業務ではない。

## YOU MUST NOT

- 書籍 PDF（`.pdf/`）をコミットしない（著作権 + gitignore 済）
- ReactOS 等 OSS clone を `.oss/` 以外に置かない（`.oss/` のみ gitignore 済）
- NEC 業務情報・社内資料・顧客名・社内パスを含めない（public repo）
- ReactOS コードを大量コピペしない。最小引用 + permalink で対応
- ReactOS への参照は master ブランチではなく commit SHA の GitHub permalink を貼る（コードが変わるとリンク内容が変わるため）

## 規約

- ノート構造・6 セクションテンプレ・ReactOS 主要ディレクトリ早見は [notes/README.md](notes/README.md) を正本とする（CLAUDE.md には書かない）
- ノート配置: `notes/part1|part2/chNN-<slug>.md` ／ 横断テーマ `notes/topics/<slug>.md` ／ 日次ログ `notes/daily/YYYY-MM-DD.md`
- ノート追加・更新時は `notes/README.md` のインデックスに 1 行追記する
- `.pdf/` `.oss/` 以外に大容量・OSS clone・秘匿性のあるディレクトリを追加する場合は **先に `.gitignore` を更新してから** 配置する

## 親 CLAUDE.md との関係

`~/CLAUDE.md` の NEC ブランド・NEC IP・`nec-pptx` / `nec-conform` 等の NEC 関連指示は **本リポジトリでは適用外**。応答スタイル（romaji 入力 → 日本語応答）等の一般ルールのみ継承する。
