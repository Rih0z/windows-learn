# windows-learn

『Windows Internals』Part 1 / Part 2 を **ReactOS のオープンソース実装と突き合わせながら毎日少しずつ読み進める** 個人学習リポジトリ。

書籍が概念・データ構造・挙動として語る NT カーネルの仕組みを、NT 互換 OSS である [ReactOS](https://github.com/reactos/reactos) の実コードで対応付け、WinDbg / Sysinternals で実 Windows の挙動も観測する三点セットで理解を深める。

## 構成

- `notes/` — 学習ノート（Part 1 / Part 2 / Topics / Daily Log）。詳細は [notes/README.md](notes/README.md)
- `.pdf/` — 書籍 PDF 置き場（gitignore 対象。リポジトリには含まれない）
- `.oss/` — ReactOS クローン等のローカル検証用（gitignore 対象）

## 対象書籍

- Windows Internals, Part 1
- Windows Internals, Part 2

書籍 PDF はローカル `.pdf/` に配置しリポジトリには push しない。学習ノートのみを管理する。

## アプローチ

1. 書籍の該当節を読む
2. 出てくる構造体・関数名で ReactOS を検索し実コードを読む
3. WinDbg / Sysinternals で実 Windows の挙動を観測
4. ノートに「概念 ↔ 実装 ↔ 観測」の 3 点で残す
