# Sensor Map — Phase 1 IoT Coverage

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)  
**Document:** Sensor Registry & Tag Coverage v2.0  
**Status:** PLANNED — Phase 1 Foundation  
**Artifact Grade:** 🟡 Planning — tag patterns fully instantiated for all Phase 1 assets; historian paths and bad-tag thresholds confirmed at commissioning

---

## 1. Scope

This document is the authoritative sensor registry for Phase 1 instrumentation coverage across:

- Extrusion assets
- Injection moulding assets
- PET stretch blow moulding (SBM) assets
- Energy and utility assets

It defines historian-facing tag patterns, scan policies, edge protocol paths, gateway assignments, asset-to-zone-to-anchor traceability, and data quality SLAs.

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

### 2.3 Mandatory Mapping Fields (Gate 3 Requirement)

Every production tag in this registry must be traceable through the following fields before Gate 3 closure.
Tags missing any field are ineligible for historian acceptance sign-off.

| Field | Description | Source Document |
|-------|-------------|-----------------|
| `Asset ID` | Fully instantiated asset identifier (no `xx` patterns in production) | [digital-twin.md](./digital-twin.md) |
| `Zone` | Zone letter (A–H) where the asset is physically located | [bim/zone-boundaries.md](./bim/zone-boundaries.md) |
| `Anchor GUID` | Planning or as-built BIM GUID for the asset | [bim/asset-anchors.md](./bim/asset-anchors.md) |
| `Gateway` | IoT/OPC gateway device ID that reads this tag | Section 3 tables below |
| `Historian Path` | Full path in AVEVA PI or Honeywell Uniformance historian | Confirmed at commissioning |
| `Quality Owner` | Named role responsible for tag data quality | Section 4 below |

---

## 3. Sensor Registry

### 3.1 Extruder Assets — Tag Pattern Reference (per-asset schema)

> **Pattern applied to assets:** EXT-A1-01, EXT-A2-01, EXT-A2-02, EXT-A2-03, EXT-A3-01 — 5 extruder assets across UNIT-A1, UNIT-A2, UNIT-A3.  
> Replace `xx` with the specific asset qualifier (e.g., `A1`, `A2`, `A3`) when instantiating.

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

#### 3.1.1 Extruder Asset Instantiation Mapping

| Asset ID | Zone | Anchor GUID | Primary Gateways | Historian Base Path | Quality Owner | Tags / Asset |
|----------|------|-------------|-----------------|---------------------|---------------|-------------|
| EXT-A1-01 | A | `2ea10001-7b3c-4d00-8001-a10000000001` 🟡 | IOT-GW-A-THERMAL-01, IOT-GW-A-PROC-01, IOT-GW-A-MOTION-01, IOT-GW-A-POWER-01, IOT-GW-A-CBM-01, IOT-GW-A-UTIL-01 | `PI\\CCH-PLS\AREA-A\UNIT-A1\EXT-A1-01\` | Process Engineer (Extrusion) | 11 |
| EXT-A2-01 | A | `2ea10001-7b3c-4d00-8001-a20000000001` 🟡 | IOT-GW-A-THERMAL-01, IOT-GW-A-PROC-01, IOT-GW-A-MOTION-01, IOT-GW-A-POWER-01, IOT-GW-A-CBM-01, IOT-GW-A-UTIL-01 | `PI\\CCH-PLS\AREA-A\UNIT-A2\EXT-A2-01\` | Process Engineer (Extrusion) | 11 |
| EXT-A2-02 | A | `2ea10001-7b3c-4d00-8001-a20000000002` 🟡 | IOT-GW-A-THERMAL-01, IOT-GW-A-PROC-01, IOT-GW-A-MOTION-01, IOT-GW-A-POWER-01, IOT-GW-A-CBM-01, IOT-GW-A-UTIL-01 | `PI\\CCH-PLS\AREA-A\UNIT-A2\EXT-A2-02\` | Process Engineer (Extrusion) | 11 |
| EXT-A2-03 | A | `2ea10001-7b3c-4d00-8001-a20000000003` 🟡 | IOT-GW-A-THERMAL-01, IOT-GW-A-PROC-01, IOT-GW-A-MOTION-01, IOT-GW-A-POWER-01, IOT-GW-A-CBM-01, IOT-GW-A-UTIL-01 | `PI\\CCH-PLS\AREA-A\UNIT-A2\EXT-A2-03\` | Process Engineer (Extrusion) | 11 |
| EXT-A3-01 | A | `2ea10001-7b3c-4d00-8001-a30000000001` 🟡 | IOT-GW-A-THERMAL-01, IOT-GW-A-PROC-01, IOT-GW-A-MOTION-01, IOT-GW-A-POWER-01, IOT-GW-A-CBM-01, IOT-GW-A-UTIL-01 | `PI\\CCH-PLS\AREA-A\UNIT-A3\EXT-A3-01\` | Process Engineer (Extrusion) | 11 |

### 3.2 Injection Moulding Machine Assets — Tag Pattern Reference (per-asset schema)

> **Pattern applied to assets:** IM-B1-01, IM-B2-01, IM-B3-01, IM-B4-01 — 4 injection moulding machines across UNIT-B1 through UNIT-B4.  
> Replace `xx` with the specific asset qualifier (e.g., `B1`, `B2`, `B3`, `B4`) when instantiating.

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

#### 3.2.1 Injection Moulding Asset Instantiation Mapping

| Asset ID | Zone | Anchor GUID | Primary Gateways | Historian Base Path | Quality Owner | Tags / Asset |
|----------|------|-------------|-----------------|---------------------|---------------|-------------|
| IM-B1-01 | B | `2ea10001-7b3c-4d00-8001-b10000000002` 🟡 | IOT-GW-B-HYD-01, IOT-GW-B-THERMAL-01, IOT-GW-B-MOTION-01, IOT-GW-B-POWER-01, IOT-GW-B-UTIL-01, MES-OPCUA-BRIDGE-01 | `PI\\CCH-PLS\AREA-B\UNIT-B1\IM-B1-01\` | Process Engineer (Moulding) | 8 |
| IM-B2-01 | B | `2ea10001-7b3c-4d00-8001-b20000000001` 🟡 | IOT-GW-B-HYD-01, IOT-GW-B-THERMAL-01, IOT-GW-B-MOTION-01, IOT-GW-B-POWER-01, IOT-GW-B-UTIL-01, MES-OPCUA-BRIDGE-01 | `PI\\CCH-PLS\AREA-B\UNIT-B2\IM-B2-01\` | Process Engineer (Moulding) | 8 |
| IM-B3-01 | B | `2ea10001-7b3c-4d00-8001-b30000000001` 🟡 | IOT-GW-B-HYD-01, IOT-GW-B-THERMAL-01, IOT-GW-B-MOTION-01, IOT-GW-B-POWER-01, IOT-GW-B-UTIL-01, MES-OPCUA-BRIDGE-01 | `PI\\CCH-PLS\AREA-B\UNIT-B3\IM-B3-01\` | Process Engineer (Moulding) | 8 |
| IM-B4-01 | B | `2ea10001-7b3c-4d00-8001-b40000000001` 🟡 | IOT-GW-B-HYD-01, IOT-GW-B-THERMAL-01, IOT-GW-B-MOTION-01, IOT-GW-B-POWER-01, IOT-GW-B-UTIL-01, MES-OPCUA-BRIDGE-01 | `PI\\CCH-PLS\AREA-B\UNIT-B4\IM-B4-01\` | Process Engineer (Moulding) | 8 |

### 3.3 PET SBM Machine

> **Fully instantiated asset:** SBM-B1-01 (UNIT-B1, Zone B).

| Tag | Measurement | Sensor Type | Scan Rate | Physical Sensor Count | Protocol | Gateway Assignment | Historian |
|-----|-------------|-------------|-----------|----------------------|----------|--------------------|-----------|
| `SBM-B1-01_TI_OVEN_Z1` to `_Z8` | Oven zone temperature | Thermocouple | 1 s | 8 | 4–20 mA | `IOT-GW-B-PET-01` | ✅ |
| `SBM-B1-01_PI_BLOW` | Blow air pressure | Pressure transducer | 100 ms | 1 | 4–20 mA/HART | `IOT-GW-B-PET-01` | ✅ |
| `SBM-B1-01_SI_STRETCH` | Stretch rod position | Linear encoder | 100 ms | 1 | Encoder/Fieldbus | `IOT-GW-B-PET-01` | ✅ |
| `SBM-B1-01_CT_BOTTLE` | Bottles/hour (production rate) | Counter | Per minute | 1 logical counter | OPC UA | `MES-OPCUA-BRIDGE-01` | ✅ |
| `SBM-B1-01_PI_MOTOR` | Machine power consumption | Power analyser | 10 s | 1 | Modbus TCP | `IOT-GW-B-POWER-01` | ✅ |

#### 3.3.1 PET SBM Asset Instantiation Mapping

| Asset ID | Zone | Anchor GUID | Primary Gateways | Historian Base Path | Quality Owner | Tags / Asset |
|----------|------|-------------|-----------------|---------------------|---------------|-------------|
| SBM-B1-01 | B | `2ea10001-7b3c-4d00-8001-b10000000005` 🟡 | IOT-GW-B-PET-01, MES-OPCUA-BRIDGE-01, IOT-GW-B-POWER-01 | `PI\\CCH-PLS\AREA-B\UNIT-B1\SBM-B1-01\` | Process Engineer (Moulding) | 12 (8 oven zones + 4) |

### 3.4 Energy and Utilities

> **Fully instantiated tags** — specific asset IDs used throughout this section.

| Tag | Measurement | Sensor Type | Scan Rate | Physical Sensor Count | Protocol | Gateway Assignment | Historian |
|-----|-------------|-------------|-----------|----------------------|----------|--------------------|-----------|
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

#### 3.4.1 Energy and Utilities Asset Instantiation Mapping

| Asset ID | Zone | Anchor GUID | Primary Gateway | Historian Base Path | Quality Owner | Active Tags |
|----------|------|-------------|----------------|---------------------|---------------|-------------|
| SOLAR-E3-01 | E | `2ea10001-7b3c-4d00-8001-e30000000001` 🟡 | IOT-GW-E-ENERGY-01 | `PI\\CCH-PLS\AREA-E\UNIT-E3\SOLAR-E3-01\` | Facilities / Energy Manager | 2 |
| BESS-E3-01 | E | `2ea10001-7b3c-4d00-8001-e30000000003` 🟡 | IOT-GW-E-BESS-01 | `PI\\CCH-PLS\AREA-E\UNIT-E3\BESS-E3-01\` | Facilities / Energy Manager | 3 |
| BESS-E3-02 | E | `2ea10001-7b3c-4d00-8001-e30000000004` 🟡 | IOT-GW-E-BESS-01 | `PI\\CCH-PLS\AREA-E\UNIT-E3\BESS-E3-02\` | Facilities / Energy Manager | 3 |
| GEN-E3-01 | E | `2ea10001-7b3c-4d00-8001-e30000000005` 🟡 | IOT-GW-E-GEN-01 | `PI\\CCH-PLS\AREA-E\UNIT-E3\GEN-E3-01\` | Facilities / Energy Manager | 2 |
| COMP-E2-01 | E | `2ea10001-7b3c-4d00-8001-e20000000001` 🟡 | IOT-GW-E-UTIL-01 | `PI\\CCH-PLS\AREA-E\UNIT-E2\COMP-E2-01\` | Facilities / Energy Manager | 2 |
| COMP-E2-02 | E | `2ea10001-7b3c-4d00-8001-e20000000002` 🟡 | IOT-GW-E-UTIL-01 | `PI\\CCH-PLS\AREA-E\UNIT-E2\COMP-E2-02\` | Facilities / Energy Manager | 2 |
| CHILL-E1-01 | E | `2ea10001-7b3c-4d00-8001-e10000000001` 🟡 | IOT-GW-E-UTIL-01 | `PI\\CCH-PLS\AREA-E\UNIT-E1\CHILL-E1-01\` | Facilities / Energy Manager | 3 |

---

## 4. Sensor Coverage Summary (Phase 1)

| Asset Group | Critical Assets in Group | Assets with Required Sensor Set | Coverage % | Phase 1 Target |
|-------------|---------------------------|----------------------------------|------------|----------------|
| Extrusion (`AREA-A`) | 5 | 5 | 100% | ≥ 85% |
| Injection Moulding (`AREA-B`, IM units) | 4 | 4 | 100% | ≥ 85% |
| PET SBM (`AREA-B`, SBM unit) | 1 | 1 | 100% | ≥ 85% |
| Utilities & Energy (`AREA-E`) | 7 | 7 | 100% | ≥ 85% |
| **Overall** | **17** | **17** | **100%** | **≥ 85%** |

Coverage is measured against critical-asset minimum sensing packs required for historian integration and digital twin foundation readiness.

### 4.1 Tag Count Summary

| Asset Group | Instantiated Assets | Tags per Asset (typical) | Total Planned Tags |
|-------------|--------------------|--------------------------|--------------------|
| Extruder barrel sensors | 5 | 11 | 55 |
| Injection moulding sensors | 4 | 8 | 32 |
| PET SBM sensors | 1 | 12 | 12 |
| Energy and utilities | 7 | 2–3 | 17 |
| **Phase 1 total** | **17** | — | **~116** |

---

## 5. Data Quality SLAs and Acceptance Criteria

These SLAs apply to all tags in this registry and must be validated for 30 consecutive days before Gate 3 historian acceptance sign-off.

### 5.1 Completeness SLA

| Metric | Threshold | Measurement Method |
|--------|-----------|-------------------|
| Tag completeness (all tags reporting) | ≥ 99.0% per day | Historian null/gap count over rolling 24-hour window |
| Critical-asset tag completeness | ≥ 99.5% per day | Subset: injection pressure, barrel temps, melt temp, power |
| Bad-tag rate (stale / out-of-range / stuck) | < 0.5% per asset per day | Historian bad-quality flag count |

### 5.2 Freshness / Latency SLA

| Metric | Threshold | Measurement Method |
|--------|-----------|-------------------|
| Maximum historian lag (field → archive) | ≤ 10 s | Compare DCS timestamp to historian archive timestamp |
| OPC UA polling to historian persistence | ≤ 2 s for 1-s scan-rate tags | End-to-end latency probe at commissioning |
| IoT MQTT → edge gateway → historian | ≤ 5 s for 10-s scan-rate tags | Gateway log timestamp comparison |

### 5.3 Timestamp Synchronisation

| Requirement | Standard |
|-------------|---------|
| OT network NTP synchronisation | All DCS nodes, IoT gateways, and historian servers synchronised to NTP stratum ≤ 2 |
| Maximum clock skew between OT devices | ≤ 100 ms |
| Historian timestamp source | DCS or gateway timestamp (not historian server receipt time) |

### 5.4 Bad-Tag Threshold Definitions

A tag is classed as **bad** if any of the following conditions occur:

| Condition | Bad-Tag Class |
|-----------|--------------|
| Value unchanged for > 5× the configured scan rate (stuck sensor) | Stuck |
| Value outside the instrument's calibrated engineering range | Out-of-range |
| Communication failure (no value received within 3× scan rate) | Communication loss |
| Quality flag from OPC UA / DCS = BAD or UNCERTAIN | OPC quality failure |
| Value changes by > 3× the maximum expected engineering-unit step per scan cycle | Spike |

### 5.5 Acceptance Checks Before Simulation Use

Before any tag's data is included in a simulation dataset, the following checks must pass:

1. **30-day validated window**: tag has been in-service for ≥ 30 consecutive days with completeness ≥ 99%.
2. **Engineering range validation**: min/max observed values are within the instrument's calibrated range.
3. **Duplicate timestamp check**: no duplicate timestamps in the historian archive.
4. **Signed acceptance**: Quality Owner for the asset group has signed the data quality acceptance record in the commissioning handover pack.
5. **Cross-tag consistency**: where physical relationships exist (e.g., cooling water supply temp < return temp for active chiller), cross-tag consistency rules have been checked and documented.

---

## 6. Cross-Reference Matrix

| Need | Authoritative Document |
|------|------------------------|
| DCS/SCADA and historian architecture | [docs/digital-twin.md](./digital-twin.md) |
| Spatial location of tagged assets/sensors | [docs/bim/asset-anchors.md](./bim/asset-anchors.md) |
| Zone geometry and clearances | [docs/bim/zone-boundaries.md](./bim/zone-boundaries.md) |
| Simulation input dataset requirements | [docs/simulation-readiness.md](./simulation-readiness.md) |
| Gate 3 readiness tracking | [docs/gap-closure-report.md](./gap-closure-report.md) |

---

## 7. Revision History

| Revision | Date | Author | Changes |
|----------|------|--------|---------|
| 1.0 | 2026-05-13 | Smart Factory Core Team | Initial design-phase tag patterns and coverage summary |
| 2.0 | 2026-05-13 | Smart Factory Core Team | Added mandatory mapping fields (Section 2.3); expanded all `xx` patterns to named asset instantiation mapping tables (Sections 3.x.1); updated coverage summary for all 17 assets; added tag count summary; added Data Quality SLAs and Acceptance Criteria (Section 5); updated cross-reference matrix |

---

*This registry is maintained under Coo-Kah-Doks standards and updated when new assets are commissioned or tag dictionaries change.*
