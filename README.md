# 12V Half-Bridge LLC Battery Charger

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
