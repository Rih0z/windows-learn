# Notes — Windows Internals × ReactOS 実装読解

『Windows Internals』Part 1 / Part 2 が説明する概念を、**ReactOS のオープンソース実装** で対応コードを追いながら毎日少しずつ深く理解する。書籍は概念・データ構造・挙動を語るが Windows カーネル本体は非公開なので、NT 互換実装である ReactOS を「読める Windows」として参照する。

## 学習スタイル

- **頻度**: 1 日 1 トピック小さく。完璧主義より継続。
- **粒度**: 1 ノート = 書籍の 1 節 ～ 1 章。長くなるなら分割。
- **手順**:
  1. 書籍の該当節を読む
  2. 出てくる構造体・関数名で ReactOS リポジトリを検索
  3. 実コードを読んで「書籍が概念で語っていたものはこの関数のこの行」と対応付ける
  4. WinDbg / Sysinternals で実 Windows での挙動も確認
  5. ノートに「概念 ↔ 実装 ↔ 観測」の 3 点セットで残す

## ReactOS リポジトリ

- 本家: https://github.com/reactos/reactos
- 主要ディレクトリ:
  - `ntoskrnl/` — NT カーネル本体（Ps プロセス/Mm メモリ/Ob オブジェクトマネージャ/Io I/O 等）
    - `ntoskrnl/ps/` — Process / Thread
    - `ntoskrnl/mm/` — Memory Manager
    - `ntoskrnl/ob/` — Object Manager
    - `ntoskrnl/io/` — I/O Manager
    - `ntoskrnl/ke/` — Kernel core（ディスパッチ、同期、割込み）
    - `ntoskrnl/ex/` — Executive support（ハンドル、ワーカースレッド等）
    - `ntoskrnl/se/` — Security Reference Monitor
    - `ntoskrnl/cc/` — Cache Manager
    - `ntoskrnl/fsrtl/` — File System Runtime Library
  - `hal/` — Hardware Abstraction Layer
  - `sdk/include/ndk/` — NT Native API 宣言（書籍に出てくる構造体定義はここに多い）
  - `dll/ntdll/` — ntdll（ユーザ ↔ カーネル境界）
  - `subsystems/` — Win32 などサブシステム

ローカルにクローンする場合は `.oss/reactos/` 配下を推奨（`.oss/` は gitignore 済なので大容量の clone を含めても OK）。

## 構成

```
notes/
├── part1/                 Part 1 (System Architecture, Processes, Memory, I/O, Security 等)
├── part2/                 Part 2 (System Mechanisms, Virtualization, FS, Cache 等)
├── topics/                章を跨ぐ横断テーマ（同期プリミティブ、ETW、Object Manager 等）
└── daily/                 日次の短いログ（その日読んだ範囲・気付き）
```

## ノートのテンプレ

各トピックノートは以下のセクションで統一する:

1. **書籍の要点** — 概念・データ構造・挙動を 3〜5 個の箇条書きで
2. **登場する構造体・関数** — `EPROCESS` / `PspCreateProcess` 等を列挙
3. **ReactOS 実装対応** — リポジトリ内ファイルパスと該当関数 / 行へのリンク or 抜粋
4. **書籍と実装の差分・気付き** — ReactOS が簡略化している点、Windows 固有の機能で未実装な点
5. **WinDbg / Sysinternals での観測** — 実 Windows でのコマンドと結果
6. **疑問・宿題** — 翌日以降に持ち越すもの

## ツール

- **ReactOS ソース** — GitHub web 検索 or ローカル clone + grep
- **WinDbg / kd** — カーネルデバッグ・構造体ダンプ（`!process`, `!thread`, `dt nt!_EPROCESS` 等）
- **Sysinternals Suite** — Process Explorer / Process Monitor / RAMMap / VMMap / Handle / WinObj
- **PowerShell** — `Get-Process` / `Get-CimInstance` 等
- **ETW** — `wpr`, `xperf`, `PerfView`

## インデックス（追記していく）

### Part 1
- _（未着手）_

### Part 2
- _（未着手）_

### Topics
- _（未着手）_

### Daily Log
- _（未着手）_
