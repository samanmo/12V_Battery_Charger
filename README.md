# 12V Half-Bridge LLC Battery Charger | KiCad Designer

A high-efficiency **12V battery charger** designed for **240V AC mains input**, utilizing a Power Factor Correction (PFC) front-end and a Half-Bridge LLC resonant converter controlled by an STM32 microcontroller.

> **⚠️ HIGH VOLTAGE WARNING:** This design interfaces directly with 240V AC mains and generates lethal high-voltage DC buses. Do not build, test, or probe this hardware unless you are qualified to work with high-voltage power electronics and follow proper isolation procedures (e.g., using an isolation transformer and differential probes).

---

## Key Features & Architecture

Based on the hierarchical schematic blocks in this repository, the power stage and control architecture include:

* **AC Input & EMI Filtering (`emf_filter.kicad_sch`):** Mains input protection, inrush current limiting (NTC/PTC), varistors, and common/differential mode chokes.
* **Half-Bridge LLC Resonant Stage (`llc_power.kicad_sch`):** High-frequency resonant tank with custom transformer and isolated gate drivers (`UCC256404`).
* **Secondary Rectification & Output (`secondary_power.kicad_sch`, `output_filtering.kicad_sch`, `output_protection.kicad_sch`):** Secondary rectification, LC output filtering, and reverse polarity / over-voltage / over-current protection (`ACS720` current sensing).
* **Auxiliary & Bias Power (`auxiliary_power.kicad_sch`, `bias_power_supply.kicad_sch`):** Dedicated auxiliary supplies powering primary and secondary control ICs.
* **Digital Control & Monitoring (`STM32Controller.kicad_sch`, `temperature_sensing.kicad_sch`):** STM32-based PWM generation, charging profile control (CC/CV), and thermal monitoring.

---

## Repository Structure

```text
├── 2025_11_17_ver6.0.kicad_pro    # Main KiCad project file
├── 2025_11_17_ver6.0.kicad_sch    # Root hierarchical schematic
├── 2025_11_17_ver6.0.kicad_pcb    # Main PCB layout
├── *.kicad_sch                    # Hierarchical sub-schematics (PFC, LLC, STM32, etc.)
├── *.kicad_sym                    # Project-specific custom symbol libraries
├── *.pretty/                      # Project-specific custom footprint libraries
├── sym-lib-table & fp-lib-table   # Local library path mappings
├── BatteryCharger_pdf/            # Exported schematic/documentation PDFs
├── 2025_11_17_ver6.0.xlsx         # Bill of Materials (BOM)
└── Design Rules.txt               # PCB layout & clearance design rules
```

---

## Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/samanmo/12V_Battery_Charger.git
   ```
2. **Open in KiCad:**
   * Launch KiCad and open `2025_11_17_ver6.0.kicad_pro`.
   * All custom symbols (`.kicad_sym`) and footprints (`.pretty`) are stored locally inside the repository and mapped via `sym-lib-table` and `fp-lib-table`.

---

## Renders & Schematics
<!-- 
*(Tip: Export a 3D render from KiCad's 3D Viewer as `docs/pcb_3d.png` and uncomment the line below to display it here)*
-->
<!-- ![3D PCB Render](docs/pcb_3d.png) -->

* Full schematic PDFs are available in the [`BatteryCharger_pdf/`](./BatteryCharger_pdf) directory.

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](./LICENSE) file for details.


# 12V ハーフブリッジLLC バッテリーチャージャー
240V AC商用電源入力向けに設計された高効率な12Vバッテリーチャージャーです。力率改善（PFC）フロントエンドと、STM32マイクロコントローラによって制御されるハーフブリッジLLC共振コンバータを採用しています。
> **⚠️ 高電圧に関する警告:**  本設計は240V AC商用電源に直接接続され、致死的な高電圧DCバスを生成します。高電圧パワーエレクトロニクスを取り扱う資格を有し、適切な絶縁手順（絶縁トランスや差動プローブの使用など）を遵守できる場合を除き, 本ハードウェアの製作、テスト、またはプロービングを行わないでください。

---

## 主な特徴とアーキテクチャ
本リポジトリ内の階層型回路図ブロックに基づく、パワーステージおよび制御アーキテクチャの構成は以下の通りです：

* **AC入力およびEMIフィルタリング (emf_filter.kicad_sch)：** 商用電源入力保護、突入電流制限（NTC/PTC）、バリスタ、およびコモンモード／ノーマルモードチョークコイルを備えています。

* **ハーフブリッジLLC共振ステージ (llc_power.kicad_sch)：** カスタムトランスと絶縁型ゲートドライバ（UCC256404）を使用した高周波共振タンクです。

* **二次側整流および出力 (secondary_power.kicad_sch, output_filtering.kicad_sch, output_protection.kicad_sch)：** 二次側整流、LC出力フィルタリング、および逆接続・過電圧・過電流保護（ACS720電流センシング）を搭載しています。

* **補助電源およびバイアス電源 (auxiliary_power.kicad_sch, bias_power_supply.kicad_sch)：** 一次側および二次側の制御ICに電力を供給する専用の補助電源です。

* **デジタル制御および監視 (STM32Controller.kicad_sch, temperature_sensing.kicad_sch)：** STM32ベースのPWM生成、充電プロファイル制御（CC/CV）、および温度監視を行います。


## リポジトリ構成

```text
├── 2025_11_17_ver6.0.kicad_pro    # メインKiCadプロジェクトファイル
├── 2025_11_17_ver6.0.kicad_sch    # ルート階層回路図
├── 2025_11_17_ver6.0.kicad_pcb    # メインPCBレイアウト
├── *.kicad_sch                    # 階層サブ回路図（PFC、LLC、STM32など）
├── *.kicad_sym                    # プロジェクト固有のカスタムシンボルライブラリ
├── *.pretty/                      # プロジェクト固有のカスタムフットプリントライブラリ
├── sym-lib-table & fp-lib-table   # ローカルライブラリパスマッピング
├── BatteryCharger_pdf/            # エクスポートされた回路図・ドキュメントPDF
├── 2025_11_17_ver6.0.xlsx         # 部品表（BOM）
└── Design Rules.txt               # PCBレイアウトおよびクリアランス設計ルール

---

## はじめに
1. **リポジトリのクローン：**
```bash
	git clone https://github.com
```

2. **KiCadで開く：**
	* KiCadを起動し、2025_11_17_ver6.0.kicad_pro を開きます。
	* すべてのカスタムシンボル（.kicad_sym）およびフットプリント（.pretty）はリポジトリ内にローカル保存されており、sym-lib-table および fp-lib-table を介してマッピングされています。
---


## レンダリングと回路図
	* 完全な回路図PDFは BatteryCharger_pdf/ ディレクトリにあります。

---
## ライセンス (License)

このプロジェクトは [MITライセンス](LICENSE) の下で公開されています。





