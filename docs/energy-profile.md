# Energy Profile

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)
**Document:** Energy Profile & Power Systems Design v1.0
**Status:** PLANNED — Phase 1 Design Basis
**Master Repo Reference:** [Coo-Kah-Doks / docs / energy-strategy.md](https://github.com/oumar-code/Coo-Kah-Doks)

---

## 1. Executive Summary

| Parameter | Starting Config (Phase 1 Initial) | Full Scale (Phase 1 Ramp) |
|-----------|-----------------------------------|---------------------------|
| Peak electrical load | ~280 kW | ~1,100 kW |
| Solar PV installed | 200 kWp | 800 kWp |
| BESS capacity | 250 kWh LFP | 900 kWh LFP |
| Grid connection | 500 kVA transformer | 1,500 kVA transformer |
| Diesel backup | 500 kVA genset | 1,000 kVA genset |
| Target solar self-sufficiency | ≥ 60% (initial) | ≥ 70% (full scale) |
| Target energy cost reduction | 35% vs grid-only | 55% vs grid-only |

---

## 2. Production Load Analysis

### 2.1 Equipment Power Loads

| Equipment | Rated Power (kW) | Load Factor | Running Load (kW) | Qty | Total (kW) |
|-----------|-----------------|-------------|-------------------|-----|------------|
| Blown film extrusion line (mono) | 110 | 0.80 | 88 | 1 | 88 |
| Blown film extrusion line (3-layer) | 220 | 0.80 | 176 | 1 | 176 |
| PET preform injection machine | 120 | 0.70 | 84 | 1 | 84 |
| Stretch blow moulding machine | 55 | 0.75 | 41 | 1 | 41 |
| Injection moulding machine (120T) | 75 | 0.65 | 49 | 2 | 98 |
| Injection moulding machine (280T) | 150 | 0.65 | 98 | 1 | 98 |
| Injection moulding machine (500T) | 280 | 0.65 | 182 | 1 | 182 |
| HDPE pipe extrusion line | 135 | 0.80 | 108 | 1 | 108 |
| PET crystalliser + dryer | 45 | 0.90 | 41 | 1 | 41 |
| Granule dryers (×4) | 15 | 0.80 | 12 | 4 | 48 |
| Chilled water system | 130 | 0.85 | 111 | 1 | 111 |
| Compressed air system | 75 | 0.75 | 56 | 2 | 112 |
| QC lab + office | 30 | 0.60 | 18 | 1 | 18 |
| Lighting (factory floor) | 40 | 0.90 | 36 | 1 | 36 |
| Ancillaries (conveyors, regrind, etc.) | 60 | 0.70 | 42 | 1 | 42 |
| **TOTAL (full scale)** | — | — | — | — | **~1,283 kW** |

> **Design peak load (with 15% diversity factor): ~1,100 kW**

### 2.2 Phase 1 Initial Load (CCH-PLS-003 + CCH-PLS-004 lines only)

| Equipment | Running Load (kW) |
|-----------|-------------------|
| Blown film line (mono-layer) | 88 |
| PET preform injection + SBM | 125 |
| PET dryer + granule dryers | 65 |
| Chilled water (partial load) | 55 |
| Compressed air (1 compressor) | 56 |
| QC lab, lighting, ancillaries | 50 |
| **Phase 1 Initial Peak** | **~439 kW** |

> **Phase 1 Start design load: ~280 kW base, ~440 kW peak**

---

## 3. Solar PV System Design

### 3.1 Starting Configuration — 200 kWp

| Parameter | Value |
|-----------|-------|
| PV technology | Monocrystalline PERC, 550 Wp per panel |
| Panel count | 364 panels |
| Installed capacity | 200 kWp |
| Array area required | ~1,100 m² (rooftop + canopy) |
| Inverter type | String inverters (3× 67 kW) — SMA Tripower / Huawei SUN2000 |
| Annual yield (Lagos — 5.5 peak sun hrs/day) | ~400,000 kWh/year |
| DC:AC ratio | 1.15 |
| System losses | ~18% (temp de-rating, wiring, inverter, soiling) |
| Net P50 yield | ~328,000 kWh/year |

### 3.2 Full-Scale Configuration — 800 kWp

| Parameter | Value |
|-----------|-------|
| PV technology | Monocrystalline PERC / TOPCon, 550–600 Wp |
| Panel count | ~1,450 panels |
| Installed capacity | 800 kWp |
| Array area required | ~4,200 m² (rooftop + ground-mounted shade canopy) |
| Inverter type | Central inverters + string inverters (hybrid) |
| Annual yield | ~1,600,000 kWh/year (P50 net ~1,312,000 kWh) |
| Factory annual consumption (full scale, 2-shift) | ~1,870,000 kWh/year |
| Solar fraction | ~70% |

### 3.3 Lagos Solar Resource Data

| Month | Peak Sun Hours/Day | GHI (kWh/m²/day) |
|-------|-------------------|-------------------|
| Jan | 5.4 | 5.4 |
| Feb | 5.8 | 5.8 |
| Mar | 5.6 | 5.6 |
| Apr | 5.2 | 5.2 |
| May | 4.8 | 4.8 |
| Jun | 4.0 | 4.0 |
| Jul | 3.8 | 3.8 |
| Aug | 3.9 | 3.9 |
| Sep | 4.5 | 4.5 |
| Oct | 5.1 | 5.1 |
| Nov | 5.5 | 5.5 |
| Dec | 5.6 | 5.6 |
| **Annual Average** | **4.93** | **4.93** |

> Note: Lagos/Agbara is at ~6.4°N, 3.2°E. June–August is the rainy season — solar yield is reduced by cloud cover. BESS cycling is critical during this period.

---

## 4. Battery Energy Storage System (BESS)

### 4.1 Design Rationale

The BESS serves three primary functions:
1. **Peak shaving** — Avoid grid demand peaks (peak tariff hours 18:00–22:00)
2. **Solar buffering** — Store excess midday solar for afternoon/evening production
3. **Bridging on grid outages** — 15–30 minutes bridge time while ATS starts generator

### 4.2 Starting BESS — 250 kWh LFP

| Parameter | Value |
|-----------|-------|
| Chemistry | Lithium Iron Phosphate (LFP) — preferred for industrial/tropical environments |
| Usable capacity | 250 kWh (90% DoD) |
| Peak power output | 250 kW (1C) |
| Cycle life | ≥ 4,000 cycles at 80% DoD (≥ 10 years expected life) |
| Round-trip efficiency | ≥ 92% |
| Operating temperature range | 0–45 °C (HVAC maintained BESS room) |
| Cell format | Prismatic, LiFePO₄ |
| BMS | Cell-level monitoring, SoC/SoH/temperature, CAN bus |
| Safety | UL 9540 / IEC 62619 compliant, FM200 fire suppression in BESS room |

### 4.3 Full-Scale BESS — 900 kWh LFP

| Parameter | Value |
|-----------|-------|
| Usable capacity | 900 kWh |
| Peak power output | 900 kW (1C) |
| Bridge time at 440 kW load | ~2.0 hours continuous |
| Bridge time at 280 kW base load | ~3.2 hours |
| Solar self-sufficiency contribution | +15–20% beyond solar alone |

---

## 5. Grid Connection

### 5.1 Utility Connection

| Parameter | Value |
|-----------|-------|
| Supply authority | Ikeja Electric (IE) or Eko Electric — Agbara Industrial Estate |
| Tariff class | Industrial D2 tariff (Nigeria MYTO tariff framework) |
| Connection voltage | 33 kV incoming → step-down to 415 V |
| Transformer | 500 kVA (starting) → 1,500 kVA (full scale) — oil-filled ONAN |
| Metering | Smart meter, ToU (Time of Use) capability |
| Demand charge | Per NERC/MYTO applicable industrial rate |
| Power quality monitoring | PQ analyser at PCC (THD, PF, voltage) |

### 5.2 Grid Reliability Context (Nigeria)
Nigeria's national grid (NESI) has historically low reliability (SAIDI often 8,000–16,000 min/year in industrial zones). The solar + BESS + generator hybrid strategy is therefore **not optional** — it is essential for production continuity.

| Scenario | Coverage |
|----------|----------|
| Normal daytime operation | Solar PV (primary) + Grid (supplement) |
| Night / low-solar | BESS (primary) + Grid (supplement) |
| Grid outage < 30 min | BESS alone |
| Grid outage 30 min – 8 hr | Generator + BESS |
| Extended grid outage > 8 hr | Generator primary + solar supplement (daytime) |

---

## 6. Energy Management System (EMS)

### 6.1 EMS Architecture

```mermaid
graph TD
    SOLAR["Solar PV Array\n200 kWp → 800 kWp"] --> INV["String/Central Inverters"]
    BESS["LFP BESS\n250 kWh → 900 kWh"] --> PCS["Power Conversion System"]
    GRID["Grid Supply\n33 kV / 415 V"] --> XFMR["Distribution Transformer"]
    GENSET["Diesel Generator\n500 kVA"] --> ATS["Automatic Transfer Switch (ATS)"]

    INV --> BUSBARS["Main LV Busbars (415 V)"]
    PCS --> BUSBARS
    XFMR --> BUSBARS
    ATS --> BUSBARS

    BUSBARS --> PROD["Production Equipment\nMDPs & Distribution"]
    BUSBARS --> UTIL["Utilities\n(Chiller, Compressors)"]
    BUSBARS --> CTRL["Control Room & IT/OT\n(UPS protected)"]

    EMS["Energy Management System\n(EMS / SCADA Energy Module)"] -->|Setpoints & Dispatch| INV
    EMS -->|Charge/Discharge Control| PCS
    EMS -->|Monitoring| GRID
    EMS -->|Auto-start signal| ATS
    EMS -->|Sub-metering data| PROD
    EMS -->|Sub-metering data| UTIL

    MES["MES / AI Platform"] -->|Energy scheduling AI\n(Phase 2)| EMS
```

### 6.2 EMS Functions

| Function | Phase 1 | Phase 2 (AI) |
|----------|---------|--------------|
| Real-time generation/consumption monitoring | ✅ | ✅ |
| BESS charge/discharge scheduling | Manual setpoints | AI-optimised |
| Peak demand management | Threshold-based | AI predictive |
| Solar forecasting | None | AI ML model (irradiance + weather data) |
| Energy cost optimisation (ToU) | Rule-based | AI linear programming |
| Production schedule energy matching | Manual | AI integrated with MES |
| Reporting: energy intensity per kg product | ✅ | ✅ + AI benchmarking |

---

## 7. Energy Performance Targets

| KPI | Target | Measurement |
|-----|--------|-------------|
| Energy intensity — blown film (CCH-PLS-003) | ≤ 0.55 kWh/kg film | Monthly average |
| Energy intensity — PET bottles (CCH-PLS-004) | ≤ 0.80 kWh/kg PET | Monthly average |
| Solar self-sufficiency | ≥ 70% (full scale) | Annual |
| BESS utilisation (daily cycle) | ≥ 1 full cycle/day | Daily |
| Power factor | ≥ 0.95 | Continuous |
| Total energy cost (vs grid-only baseline) | -55% (full scale) | Annual |
| CO₂ avoided (full scale solar) | ~650 tonnes CO₂/year | Annual (vs NERC grid emission factor 0.48 kgCO₂/kWh) |

---

## 8. ISO 50001:2018 Energy Management System

This factory is committed to achieving **ISO 50001:2018** certification. The EMS documented here
forms the technical backbone of the energy management system.

| ISO 50001 Element | Implementation |
|-------------------|---------------|
| Energy policy | Group policy from Coo-Kah-Doks — adopted |
| Significant energy uses (SEUs) | Extruders, injection machines, chilled water system |
| Energy baseline (EnB) | Establish at first 90 days of production |
| Energy performance indicators (EnPIs) | kWh/kg per product SKU |
| Energy targets and action plans | See KPIs above |
| Internal energy audits | Quarterly |
| Management review | Annual |

---

*Document maintained under Coo-Kah-Doks group standards — update as equipment is commissioned and metered data becomes available.*
