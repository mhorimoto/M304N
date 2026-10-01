# uecsOS Hardware Controller Node (M304N)

## 概要 (Overview)
本リポジトリは，Teensy 4.1をコアとしたスマート農業向けUECS（Ubiquitous Environment Control System）環境制御ノード「M304」のハードウェア回路図およびプリント基板（PCB）設計データです．
M304はセンサ入力を持たないアクチュエータ制御特化型のノードであり，Luaスクリプトエンジンを搭載した非ブロッキングな組込みOS「uecsOS」を実行し，ポンプや電磁弁等のハードウェア制御を自律的かつ堅牢に処理することを目的として設計されています．

## 主なハードウェア仕様 (Hardware Specifications)
*   **メインMCU**: Teensy 4.1 (NXP i.MX RT1062, 600MHz)
*   **ファームウェア**: uecsOS (C/C++コア + 永続Lua VMによるスケジューラ)
*   **ネットワーク**: NativeEthernetによるUECSプロトコル通信
*   **拡張制御インターフェース (USB Host)**:
    *   USBハブ経由でのFT232H MPSSEモジュール複数台接続に対応
    *   物理接続トポロジ（ポート位置）に依存したフェイルセーフなリレールーティング（誤動作防止設計）
*   **ストレージ**: マイクロSDカード（MTPおよび設定ファイル管理用）

## 開発環境 (Development Environment)
設計には以下のオープンソースツールを利用しています．

*   **KiCad**: Version 10
*   **プラグイン**: KiCad-Multi-PCB (複数基板の連携設計用)
*   **3Dモデリング**: FreeCAD (エンクロージャやM3スペーサとの干渉確認等に使用)

## リポジトリ構成 (Directory Structure)
```text
.
├── DOCS
│   └── components_FT232H_sch.png
├── LIB
│   ├── M304N.bak
│   ├── M304N.kicad_sym
│   ├── TEENSY41.kicad_mod
│   ├── TEENSY_4.1.dcm
│   ├── TEENSY_4.1.lib
│   ├── TEENSY_4.1.mod
│   ├── TEENSY_4.1.stp
│   └── TEENSY_4_1.kicad_sym
├── LICENSE
├── M304N-backups
│   └── M304N-2026-10-01_184415.zip
├── M304N.kicad_pcb
├── M304N.kicad_prl
├── M304N.kicad_pro
├── M304N.kicad_sch
├── README.md
├── display_unit.kicad_sch
├── fp-lib-table
├── relay_unit.kicad_sch
└── sym-lib-table
```

## 使用・変更上の注意 (Notes on Modification)
*   FT232Hモジュール等のUSBトポロジ制御を行うため，基板上のUSBホストポート（D+/D-）配線はインピーダンスコントロールに配慮して設計・改変してください．

## ライセンス (License)
本リポジトリのハードウェア設計データは [MIT License](LICENSE) の下で公開されています．
商用・非商用問わず，ライセンス表記を行うことで自由に利用・改変・再配布が可能です．
