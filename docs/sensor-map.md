# Sensor Map — Phase 1 IoT Coverage

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)  
**Document:** Sensor Registry & Tag Coverage v1.0  
**Status:** PLANNED — Phase 1 Foundation

---

## 1. Scope

This document is the authoritative sensor registry for Phase 1 instrumentation coverage across:

- Extrusion assets
- Injection moulding assets
- PET stretch blow moulding (SBM) assets
- Energy and utility assets

It defines historian-facing tag patterns, scan policies, edge protocol paths, and gateway assignments.

For DCS/SCADA architecture and historian routing, see [docs/digital-twin.md](./digital-twin.md).  
For sensor physical location anchoring, see [docs/bim/asset-anchors.md](./bim/asset-anchors.md).

---

## 2. Tag Naming Convention and Scan-Rate Policy

### 2.1 Logical Naming Convention

Sensor tags follow the logical pattern:

`AREA-UNIT-ASSET_TYPE_POINT`

Examples:

- `A1-01-EXT_TI_Z1` (equivalent enterprise alias for `EXT-A1-01_TI_Z1`)
- `B1-01-IM_PI_INJ` (equivalent enterprise alias for `IM-B1-01_PI_INJ`)
- `E3-01-BESS_SOC` (equivalent enterprise alias for `BESS-E3-01_SOC`)

Implementation note: current operational tags in this repository are maintained in the asset-first style (e.g., `EXT-A1-01_TI_Z1`), which remains the historian source convention.

### 2.2 Scan-Rate Policy

- **100 ms**: fast-cycle machine dynamics (injection pressure, screw/stretcher position)
- **1 s**: core process control and power values
- **10 s**: equipment health, thermal and utility monitoring
- **1 min / per minute**: aggregated counters and slowly varying inventory/energy signals
- **Per cycle**: MES (Siemens Opcenter — confirmed per ADR-002 in Coo-Kah-Doks) cycle-resolved counters
- **High-frequency vibration**: 100 Hz edge capture, reduced to RMS at 1 s for historian persistence

---

## 3. Sensor Registry

### 3.1 Extruder Assets (per extruder unit)

| Tag Pattern | Measurement | Sensor Type | Scan Rate | Physical Sensor Count (per asset) | Protocol | Gateway Assignment | Historian |
|-------------|-------------|-------------|-----------|-----------------------------------|----------|--------------------|-----------|
| `EXT-xx-01_TI_Z1` to `_Z6` | Barrel temperature zone 1–6 | Type K thermocouple | 1 s | 6 | 4–20 mA/HART | `IOT-GW-A-THERMAL-01` | ✅ |
| `EXT-xx-01_TI_MELT` | Melt temperature (die adapter) | Melt thermocouple | 1 s | 1 | 4–20 mA | `IOT-GW-A-THERMAL-01` | ✅ |
| `EXT-xx-01_PI_HEAD` | Die head pressure | Melt pressure transducer | 1 s | 1 | 4–20 mA/HART | `IOT-GW-A-PROC-01` | ✅ |
| `EXT-xx-01_SI_SCREW` | Screw speed (RPM) | Encoder on gearbox output | 1 s | 1 | Pulse/Encoder | `IOT-GW-A-MOTION-01` | ✅ |
| `EXT-xx-01_II_MOTOR` | Motor current (A) | CT on drive panel | 1 s | 1 | Modbus TCP | `IOT-GW-A-POWER-01` | ✅ |
| `EXT-xx-01_PI_MOTOR` | Motor active power (kW) | Power analyser | 10 s | 1 | Modbus TCP | `IOT-GW-A-POWER-01` | ✅ |
| `EXT-xx-01_VIB_GB` | Gearbox vibration (3-axis) | MEMS accelerometer | 100 Hz → RMS 1 s | 1 tri-axial | MQTT/Edge | `IOT-GW-A-CBM-01` | ✅ |
| `EXT-xx-01_TI_GB` | Gearbox oil temperature | PT100 | 10 s | 1 | 4–20 mA | `IOT-GW-A-CBM-01` | ✅ |
| `EXT-xx-01_FI_COOL` | Cooling water flow rate | Electromagnetic flow meter | 10 s | 1 | Modbus RTU | `IOT-GW-A-UTIL-01` | ✅ |
| `EXT-xx-01_TI_COOL_S` | Cooling water supply temp | PT100 | 10 s | 1 | 4–20 mA | `IOT-GW-A-UTIL-01` | ✅ |
| `EXT-xx-01_TI_COOL_R` | Cooling water return temp | PT100 | 10 s | 1 | 4–20 mA | `IOT-GW-A-UTIL-01` | ✅ |

### 3.2 Injection Moulding Machine Assets

| Tag Pattern | Measurement | Sensor Type | Scan Rate | Physical Sensor Count (per asset) | Protocol | Gateway Assignment | Historian |
|-------------|-------------|-------------|-----------|-----------------------------------|----------|--------------------|-----------|
| `IM-xx-01_PI_INJ` | Injection pressure | Hydraulic pressure transducer | 100 ms | 1 | 4–20 mA/HART | `IOT-GW-B-HYD-01` | ✅ |
| `IM-xx-01_TI_BARREL` | Barrel temperature (zones) | Type J thermocouple | 1 s | 4–6 | 4–20 mA | `IOT-GW-B-THERMAL-01` | ✅ |
| `IM-xx-01_PI_CLAMP` | Clamp force | Tie-bar strain gauge | 1 s | 1 | Strain bridge/Fieldbus | `IOT-GW-B-MOTION-01` | ✅ |
| `IM-xx-01_SI_SCREW` | Screw position / speed | Linear encoder | 100 ms | 1 | Encoder/Fieldbus | `IOT-GW-B-MOTION-01` | ✅ |
| `IM-xx-01_PI_MOTOR` | Hydraulic pump power (kW) | Power analyser | 10 s | 1 | Modbus TCP | `IOT-GW-B-POWER-01` | ✅ |
| `IM-xx-01_CT_CYCLE` | Cycle time | Timer from MES (Siemens Opcenter — confirmed per ADR-002 in Coo-Kah-Doks) | Per cycle | 1 logical counter | OPC UA (MES bridge) | `MES-OPCUA-BRIDGE-01` | ✅ |
| `IM-xx-01_TI_MOULD_S` | Mould water supply temp | PT100 | 10 s | 1 | 4–20 mA | `IOT-GW-B-UTIL-01` | ✅ |
| `IM-xx-01_TI_MOULD_R` | Mould water return temp | PT100 | 10 s | 1 | 4–20 mA | `IOT-GW-B-UTIL-01` | ✅ |

### 3.3 PET SBM Machine

| Tag Pattern | Measurement | Sensor Type | Scan Rate | Physical Sensor Count (per asset) | Protocol | Gateway Assignment | Historian |
|-------------|-------------|-------------|-----------|-----------------------------------|----------|--------------------|-----------|
| `SBM-B1-01_TI_OVEN_Z1` to `_Z8` | Oven zone temperature | Thermocouple | 1 s | 8 | 4–20 mA | `IOT-GW-B-PET-01` | ✅ |
| `SBM-B1-01_PI_BLOW` | Blow air pressure | Pressure transducer | 100 ms | 1 | 4–20 mA/HART | `IOT-GW-B-PET-01` | ✅ |
| `SBM-B1-01_SI_STRETCH` | Stretch rod position | Linear encoder | 100 ms | 1 | Encoder/Fieldbus | `IOT-GW-B-PET-01` | ✅ |
| `SBM-B1-01_CT_BOTTLE` | Bottles/hour (production rate) | Counter | Per minute | 1 logical counter | OPC UA | `MES-OPCUA-BRIDGE-01` | ✅ |
| `SBM-B1-01_PI_MOTOR` | Machine power consumption | Power analyser | 10 s | 1 | Modbus TCP | `IOT-GW-B-POWER-01` | ✅ |

### 3.4 Energy and Utilities

| Tag | Measurement | Sensor Type | Scan Rate | Physical Sensor Count (per asset) | Protocol | Gateway Assignment | Historian |
|-----|-------------|-------------|-----------|-----------------------------------|----------|--------------------|-----------|
| `SOLAR-E3-01_PI_GEN` | Solar PV generation (kW) | Inverter Modbus | 1 s | 1 logical meter | Modbus TCP | `IOT-GW-E-ENERGY-01` | ✅ |
| `SOLAR-E3-01_EI_GEN` | Solar daily energy (kWh) | Inverter Modbus | 1 min | 1 logical meter | Modbus TCP | `IOT-GW-E-ENERGY-01` | ✅ |
| `BESS-E3-01_SOC` | BESS state of charge (%) | BMS CAN bus | 10 s | 1 logical metric | CAN bus | `IOT-GW-E-BESS-01` | ✅ |
| `BESS-E3-01_PI_CHRG` | BESS charge/discharge power (kW) | BMS CAN bus | 1 s | 1 logical metric | CAN bus | `IOT-GW-E-BESS-01` | ✅ |
| `BESS-E3-01_TI_CELL_MAX` | Max cell temperature (°C) | BMS CAN bus | 10 s | 1 logical metric | CAN bus | `IOT-GW-E-BESS-01` | ✅ |
| `GRID-E3-01_PI_IMPORT` | Grid import power (kW) | Smart meter Modbus | 1 s | 1 | Modbus TCP | `IOT-GW-E-ENERGY-01` | ✅ |
| `GEN-E3-01_PI_OUTPUT` | Generator output (kW) | Generator controller | 10 s | 1 | Modbus RTU | `IOT-GW-E-GEN-01` | ✅ |
| `GEN-E3-01_LI_FUEL` | Fuel level (L) | Ultrasonic level | 1 min | 1 | 4–20 mA | `IOT-GW-E-GEN-01` | ✅ |
| `COMP-E2-01_PI_MOTOR` | Compressor motor power (kW) | Power analyser | 10 s | 1 | Modbus TCP | `IOT-GW-E-UTIL-01` | ✅ |
| `COMP-E2-01_PI_OUTLET` | Discharge pressure (bar) | Pressure transducer | 10 s | 1 | 4–20 mA/HART | `IOT-GW-E-UTIL-01` | ✅ |
| `CHILL-E1-01_PI_MOTOR` | Chiller compressor power (kW) | Power analyser | 10 s | 1 | Modbus TCP | `IOT-GW-E-UTIL-01` | ✅ |
| `CHILL-E1-01_TI_EVAP_S` | Chilled water supply temp | PT100 | 10 s | 1 | 4–20 mA | `IOT-GW-E-UTIL-01` | ✅ |
| `CHILL-E1-01_TI_EVAP_R` | Chilled water return temp | PT100 | 10 s | 1 | 4–20 mA | `IOT-GW-E-UTIL-01` | ✅ |

---

## 4. Sensor Coverage Summary (Phase 1)

| Asset Group | Critical Assets in Group | Assets with Required Sensor Set | Coverage % | Phase 1 Target |
|-------------|---------------------------|----------------------------------|------------|----------------|
| Extrusion (`AREA-A`) | 3 | 3 | 100% | ≥ 85% |
| Injection Moulding (`AREA-B`, IM units) | 4 | 4 | 100% | ≥ 85% |
| PET SBM (`AREA-B`, SBM unit) | 1 | 1 | 100% | ≥ 85% |
| Utilities & Energy (`AREA-E`) | 4 | 4 | 100% | ≥ 85% |
| **Overall** | **12** | **12** | **100%** | **≥ 85%** |

Coverage is measured against critical-asset minimum sensing packs required for historian integration and digital twin foundation readiness.

---

## 5. Cross-Reference Matrix

| Need | Authoritative Document |
|------|------------------------|
| DCS/SCADA and historian architecture | [docs/digital-twin.md](./digital-twin.md) |
| Spatial location of tagged assets/sensors | [docs/bim/asset-anchors.md](./bim/asset-anchors.md) |
| Zone geometry and clearances | [docs/bim/zone-boundaries.md](./bim/zone-boundaries.md) |

---

*This registry is maintained under Coo-Kah-Doks standards and updated when new assets are commissioned or tag dictionaries change.*
