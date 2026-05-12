# LEARNING-PLAN.md — 1 年で『Windows Internals』Part 1 + Part 2 読破計画

## ゴール

- **対象**: Windows Internals 7th edition Part 1 (2017) + Part 2 (2022)
- **アプローチ**: 書籍 ↔ ReactOS 実装 ↔ WinDbg/Sysinternals 観測 の 3 点読み
- **時間**: 平日 60 分 / 土日オフ
- **開始**: 2026-05-11 (Mon)
- **完了予定**: 2027-05-09 (Sun) — 52 週

総工数見積: 5 日 × 60 分 × 52 週 = 約 260 時間（祝祭日・抜けで実質 220 時間）

## 全体進捗（達成したら ✅ にチェック）

- [ ] **W1**: Setup（環境・ReactOS clone・WinDbg）
- [ ] **W2–W3**: Part1 Ch1 Concepts and Tools
- [ ] **W4–W5**: Part1 Ch2 System Architecture
- [ ] **W6–W9**: Part1 Ch3 Processes and Jobs
- [ ] **W10–W13**: Part1 Ch4 Threads
- [ ] **W14–W19**: Part1 Ch5 Memory Management ★ 最重量
- [ ] **W20–W24**: Part1 Ch6 I/O System
- [ ] **W25–W28**: Part1 Ch7 Security
- [ ] **W29–W31**: Part1 Ch8 Storage Management
- [ ] **W32**: Part 1 中間レビュー（章横断振り返り・観測ノート整理）
- [ ] **W33–W37**: Part2 Ch8 System Mechanisms
- [ ] **W38–W40**: Part2 Ch9 Management Mechanisms
- [ ] **W41–W44**: Part2 Ch10 Virtualization (Hyper-V)
- [ ] **W45–W47**: Part2 Ch11 Cache Manager
- [ ] **W48–W49**: Part2 Ch12 Diagnostics and Tracing
- [ ] **W50**: Part2 残章（Startup/Shutdown 等。実 TOC で調整）
- [ ] **W51–W52**: 最終レビュー（Part 1+2 全体）

> 章タイトル・章数は 7th ed の TOC を実 PDF で確認しつつ修正可。Part 2 は版や刷によって構成差があるため W33 開始時に再確認する。

## 週次ペース基準

- **平均ページ消化**: 1 週 ≈ 25–30 ページ（書籍）。ReactOS 照合と WinDbg 観測で実所要は 1 ページ あたり 8–10 分
- **章あたりノート数の目安**: 3–7 トピックノート + 該当週の日次ログ
- **週次レビュー**: 金曜の枠を使う（30 分は当日範囲読書、30 分で `notes/_WEEKLY-REVIEW-TEMPLATE.md` を埋める）

## 章ごとサブゴール

### Part 1

#### Ch1 Concepts and Tools (W2–W3)
- [ ] Windows API / Services / Processes / Threads 用語
- [ ] User mode vs kernel mode の境界、syscall の流れ
- [ ] Sysinternals 主要ツール起動確認（Process Explorer, ProcMon, WinObj, RAMMap, VMMap）
- [ ] ReactOS: リポジトリ構造、`ntoskrnl/` 内訳を把握
- [ ] WinDbg: kd セッション起動、`!process 0 0` で全プロセス一覧

#### Ch2 System Architecture (W4–W5)
- [ ] Executive / Kernel / HAL / Subsystems の責務分離
- [ ] Critical system files: ntoskrnl.exe, hal.dll, win32k.sys, ntdll.dll
- [ ] ReactOS: `ntoskrnl/`, `hal/`, `subsystems/win32/` の対応関係
- [ ] EPROCESS / KPROCESS / ETHREAD / KTHREAD の関係概観

#### Ch3 Processes and Jobs (W6–W9)
- [ ] Process 作成フロー (CreateProcess → NtCreateUserProcess → PspCreateProcess)
- [ ] EPROCESS フィールド読解 (`dt nt!_EPROCESS`)
- [ ] Job objects, silos, AppContainer の概念
- [ ] ReactOS `ntoskrnl/ps/process.c` の `PspCreateProcess` 実装読解
- [ ] Protected Process / PPL の保護階層
- [ ] 観測: Process Explorer の Protection カラム、`!process` でフラグ確認

#### Ch4 Threads (W10–W13)
- [ ] Thread 構造体 (ETHREAD/KTHREAD)、TEB
- [ ] ディスパッチャ、スケジューリング (priority, quantum, ideal processor)
- [ ] ReactOS `ntoskrnl/ke/thrdschd.c`, `ntoskrnl/ps/thread.c`
- [ ] User-mode scheduling, fibers, UMS
- [ ] 観測: `!thread`, ProcExp Threads タブ, CPU 使用パターン

#### Ch5 Memory Management ★最重量 (W14–W19)
- [ ] 仮想アドレス空間レイアウト (x64)
- [ ] PFN database, VAD tree, working set
- [ ] ページフォルト処理 (`MmAccessFault`)
- [ ] Section objects, mapped files, copy-on-write
- [ ] ReactOS `ntoskrnl/mm/` 全体 (ARM3 含む)
- [ ] 観測: RAMMap, VMMap, `!vm`, `!pfn`

#### Ch6 I/O System (W20–W24)
- [ ] IRP の生涯、IO_STACK_LOCATION
- [ ] Driver stack, filter drivers, PnP, Power Management
- [ ] ReactOS `ntoskrnl/io/iomgr/`
- [ ] WDM vs KMDF
- [ ] 観測: WinObj で \Driver \Device、ProcMon でファイル/レジストリ I/O

#### Ch7 Security (W25–W28)
- [ ] SID, ACL, ACE, Access Token, SRM
- [ ] Logon flow, LSASS, authentication packages
- [ ] ReactOS `ntoskrnl/se/`, `lsass`
- [ ] AppContainer, integrity levels, UAC
- [ ] 観測: ProcExp Security タブ, `!token`, whoami /all

#### Ch8 Storage Management (W29–W31)
- [ ] Disk drivers, partitions, volumes, dynamic disks
- [ ] Volume Manager, VSS
- [ ] Storage Spaces, ReFS の位置付け
- [ ] ReactOS のストレージドライバ概観

### Part 2

> Part 2 開始時 (W33) に実 TOC を確認し、以下を必要に応じて再配分する

#### Ch8 System Mechanisms (W33–W37)
- [ ] Trap dispatching, interrupts, DPCs, APCs
- [ ] System service dispatching
- [ ] Object Manager の internals
- [ ] Synchronization primitives (KEVENT, KMUTEX, ERESOURCE, pushlocks)
- [ ] ReactOS `ntoskrnl/ob/`, `ntoskrnl/ke/`

#### Ch9 Management Mechanisms (W38–W40)
- [ ] Registry internals (HIVE, KCB)
- [ ] Services, WMI, ETW

#### Ch10 Virtualization Technologies (W41–W44)
- [ ] Hyper-V architecture (root partition / child partitions)
- [ ] VTL, VSM, Credential Guard
- [ ] HVCI

#### Ch11 Cache Manager (W45–W47)
- [ ] Virtual block cache, write-back, lazy writer
- [ ] ReactOS `ntoskrnl/cc/`

#### Ch12 Diagnostics and Tracing (W48–W49)
- [ ] ETW deep dive, DTrace on Windows
- [ ] Crash dump, WER, livekd

### 最終レビュー (W51–W52)

- [ ] Part 1+2 全体マインドマップ作成
- [ ] 未消化の宿題リスト棚卸し
- [ ] 「もう一度読みたい節」TOP10 を `notes/topics/` に整理

## 進捗の記録フロー

```
平日 60 分
 ├─ 50 分: 読書 + ReactOS 照合 + WinDbg 観測
 ├─ 10 分: notes/daily/YYYY-MM-DD.md に当日ログ（_TEMPLATE.md ベース）
 └─ ノート完成 / 章サブゴール達成時 → 該当チェックボックスを ✅ 化

金曜 60 分（読書 30 / 振り返り 30）
 └─ notes/_WEEKLY-REVIEW-TEMPLATE.md ベースで週次ノート作成
    notes/daily/YYYY-MM-DD-weekly.md に保存

章完了時
 ├─ 章サマリノートを notes/part{1,2}/chNN-<slug>.md として完成させる
 ├─ notes/README.md の章インデックスにリンク追記
 └─ 本ファイルの該当チェックボックスを ✅

月末（土日のいずれか、任意）
 └─ 計画ズレ点検。2 週以上遅れたら本ファイルの週割を後ろ倒し
```

## 計画調整ルール

- **2 週連続で日次ログが書けなかったら**: ペースが過大。章を 1 つ飛ばすか、当該章の深掘りトピックを削る
- **1 週遅れたら**: 翌週リカバリ可能
- **章サブゴールが多すぎると感じたら**: ★ 主要トピックだけ完了し他は飛ばす。完璧主義回避

## 参考

- ReactOS: https://github.com/reactos/reactos
- Sysinternals: https://learn.microsoft.com/en-us/sysinternals/
- WinDbg cheatsheet（自分用ノート）: `notes/topics/windbg-cheatsheet.md`（まだ未作成）
