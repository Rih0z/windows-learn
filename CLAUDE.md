# CLAUDE.md — windows-learn

> Windows Internals (Part 1 / Part 2) を ReactOS の実装と突き合わせながら**毎日少しずつ**理解する個人学習リポジトリ。コードを書くより読む・対応付ける・観測することが主成果物。

## このリポジトリの目的

- 書籍『Windows Internals』が概念で語る NT カーネルの仕組みを、NT 互換 OSS の [ReactOS](https://github.com/reactos/reactos) の実コードで読み解き、WinDbg / Sysinternals で実 Windows の挙動も観測する
- 1 日 1 トピック小さく。完璧主義より継続
- 成果物はノート（`notes/` 配下）。書籍 PDF やソースクローンはリポジトリに入れない

## ノートを書くときの規約（YOU MUST）

各トピックノートは以下 6 セクションで統一する:

1. **書籍の要点** — 概念・データ構造・挙動を 3〜5 個の箇条書き
2. **登場する構造体・関数** — `EPROCESS` / `PspCreateProcess` 等を列挙
3. **ReactOS 実装対応** — `ntoskrnl/ps/...` 等のパスと該当関数・抜粋。GitHub permalink を貼る（master ではなく commit SHA で）
4. **書籍と実装の差分・気付き** — ReactOS が簡略化している点、Windows 固有で未実装な点
5. **WinDbg / Sysinternals での観測** — 実 Windows でのコマンドと結果
6. **疑問・宿題** — 翌日以降に持ち越すもの

配置: Part 1/2 章ノートは `notes/part1|part2/chNN-<slug>.md`、横断テーマは `notes/topics/<slug>.md`、日次は `notes/daily/YYYY-MM-DD.md`。ノートを追加・更新したら `notes/README.md` のインデックスにも 1 行追記する。

## YOU MUST NOT

- 書籍 PDF（`.pdf/`）をコミットしない（著作権 + サイズ。gitignore 済）
- ReactOS クローン等の OSS ソースを `.oss/` 以外に置かない（gitignore 済の場所のみ）
- 公開リポジトリなので、NEC 業務情報・社内資料を含めない
- ReactOS のコードを大量コピペしない。引用は必要最小限 + permalink で対応

## 主要パス

- 書籍 PDF: `.pdf/windows-internals1.pdf` / `.pdf/windows-internals2.pdf`（ローカルのみ）
- ReactOS ローカル clone（任意）: `.oss/reactos/`
- ノート索引: `notes/README.md`

## ReactOS 主要ディレクトリ早見

- `ntoskrnl/ps/` Process/Thread ／ `ntoskrnl/mm/` Memory ／ `ntoskrnl/ob/` Object Manager
- `ntoskrnl/io/` I/O ／ `ntoskrnl/ke/` Kernel core ／ `ntoskrnl/ex/` Executive
- `ntoskrnl/se/` Security ／ `ntoskrnl/cc/` Cache ／ `ntoskrnl/fsrtl/` FS Runtime
- `hal/` HAL ／ `sdk/include/ndk/` NT Native API 宣言 ／ `dll/ntdll/` ntdll

## 応答スタイル

- ユーザーは romaji で入力 → 漢字仮名混じり日本語で応答（mixed Ja/En 可）
- 概念だけでなく「ReactOS のこのファイルのこの関数」まで踏み込む。深く理解することが目的
- 1 ノート完成より、毎日小さく前進することを優先

## 親 CLAUDE.md の継承

`~/CLAUDE.md`（NEC 全体ルール）の規約も適用される。ただし本リポジトリは NEC 業務ではなく個人学習 / 公開リポジトリなので、NEC ブランド・NEC IP 関連の指示は対象外。
