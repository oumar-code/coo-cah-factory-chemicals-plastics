# Coo-Cah Plastics & Polymers Factory — AI Platform Status

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Plastics & Polymers Factory | **Factory ID:** CCH-PLS
> **Document Version:** 1.0 | **Owner:** AI Platform Team / Smart Factory Core Team
> **Platform:** Coo-Cah AI-Connected Factory Platform (group standard)
> **Status:** Design complete — staging stub endpoints documented; production go-live pending commissioning

---

## 1. Overview

The Plastics & Polymers Factory AI Platform is the factory-specific instance of the
**Coo-Cah AI-Connected Factory Platform**. It consumes MES, historian, energy, and quality
data and returns predictions, anomaly alerts, and optimisation recommendations for extrusion,
PET moulding, utilities, and maintenance.

This document captures the current readiness state of each planned AI service, the intended endpoint specification, and the blockers that prevent production activation.

| Attribute | Value |
|-----------|-------|
| Platform | Coo-Cah AI-Connected Factory Platform |
| Deployment architecture | Shared group cloud inference + on-site edge inference node |
| API framework | FastAPI (Python 3.11); OpenAPI 3.0 |
| Telemetry ingest | MQTT / historian REST / MES REST |
| Historian source | AVEVA PI or Honeywell Uniformance — see [mes-integration.md](./mes-integration.md) |
| Authentication | OAuth 2.0 client credentials; JWT bearer tokens |
| Staging base URL | `https://ai-staging.cch-pls.internal/api/v1/` |
| Production base URL | `https://ai.cch-pls.coocah.ng/api/v1/` *(not yet live)* |
| Write-back boundary | Read-only in Phase 1/2; approved DCS loops only in Phase 3 |

---

## 2. Phase 1 / Phase 2 Service Status Dashboard

| Service ID | Service Name | Endpoint | Staging Status | Production Status | Primary Blocker |
|------------|--------------|----------|----------------|------------------|-----------------|
| AI-PLS-001 | Blown film thickness predictor | `/ai/blown-film-thickness` | Stub defined | Pending | Live extrusion historian feed |
| AI-PLS-002 | PET intrinsic viscosity predictor | `/ai/pet-iv-predict` | Stub defined | Pending | PET line commissioning and lab correlation |
| AI-PLS-004 | Extruder gearbox predictive maintenance | `/ai/pdm/extruder-gearbox` | Stub defined | Pending | Vibration data collection window |
| AI-PLS-005 | Chiller COP predictor | `/ai/utilities/chiller-cop` | Stub defined | Pending | Utilities commissioning |
| AI-PLS-006 | Energy scheduling optimiser | `/ai/energy-dispatch` | Stub defined | Pending | Solar/BESS telemetry and tariff profile |

**Legend:**

- **Stub defined** — endpoint contract and payload are ready for staging implementation
- **Pending** — production service not active because live data prerequisites are not yet available

---

## 3. Service Specifications

### AI-PLS-001 — Blown Film Thickness Predictor

**Purpose:** Predicts off-spec film thickness before the online gauge reports a drift severe enough to create scrap.

| Attribute | Value |
|-----------|-------|
| Model type | Gradient boosting / multivariate regression |
| Input data | Screw speed, die temperature zones, BUR, nip speed, air-ring flow, resin grade |
| Output | Predicted thickness (µm), deviation risk, recommended operator action |
| Trigger | Event-driven every 5 seconds from historian |
| Primary user | Extrusion supervisor / process engineer |

**API specification:**

```json
POST /ai/blown-film-thickness
{
  "asset_id": "EXT-A1-01",
  "timestamp_utc": "2026-05-13T12:00:00Z",
  "screw_speed_rpm": 58.0,
  "die_temp_c": [214, 216, 217, 218, 216, 215],
  "bubble_up_ratio": 2.8,
  "nip_speed_m_min": 18.4,
  "air_ring_pct": 72,
  "resin_grade": "LLDPE-C8"
}
```

```json
{
  "predicted_thickness_um": 48.6,
  "target_thickness_um": 50.0,
  "deviation_risk": "LOW",
  "recommended_action": null,
  "model_version": "v1.0.0"
}
```

### AI-PLS-002 — PET Intrinsic Viscosity Predictor

**Purpose:** Predicts intrinsic viscosity drift in PET preforms based on dryer and barrel conditions before QC release.

| Attribute | Value |
|-----------|-------|
| Model type | Supervised regression |
| Input data | Dryer temperature, dwell time, hopper dew point, barrel zones, hold time, cooling time |
| Output | Predicted IV (`dl/g`), release risk flag, suggested process correction |
| Trigger | Per production order and on-demand |
| Primary user | PET line engineer / QA lab |

### AI-PLS-004 — Extruder Gearbox Predictive Maintenance

**Purpose:** Detects early mechanical degradation on extruder drive trains and recommends maintenance before failure.

| Attribute | Value |
|-----------|-------|
| Model type | Time-series anomaly detection + failure classification |
| Input data | Vibration FFT, gearbox temperature, motor current, lubrication intervals |
| Output | Failure probability, lead-time class, maintenance recommendation |
| Trigger | Hourly batch scoring |
| Primary user | Maintenance planner |

### AI-PLS-005 — Chiller COP Predictor

**Purpose:** Tracks expected chiller efficiency and flags utility degradation that affects mould cooling and PET quality.

| Attribute | Value |
|-----------|-------|
| Model type | Regression / rule hybrid |
| Input data | Chiller load, ambient temperature, chilled-water supply/return, compressor current |
| Output | Predicted COP, deviation from expected COP, utility alert |
| Trigger | Every 15 minutes |
| Primary user | Utilities engineer |

### AI-PLS-006 — Energy Scheduling Optimiser

**Purpose:** Recommends solar/BESS dispatch against extrusion and moulding load forecasts.

| Attribute | Value |
|-----------|-------|
| Model type | Load forecast + optimisation solver |
| Input data | Production schedule, tariff windows, weather forecast, BESS SoC, load history |
| Output | Charge/discharge schedule, grid import forecast, self-sufficiency confidence |
| Trigger | Daily at 04:30 WAT and on demand |
| Primary user | Energy manager / factory manager |

**API specification:**

```json
GET /ai/energy-dispatch?forecast_date=2026-05-14&site=CCH-PLS
```

```json
{
  "forecast_date": "2026-05-14",
  "recommended_dispatch": [
    {"window": "08:00-11:00", "action": "charge_bess"},
    {"window": "16:00-21:00", "action": "discharge_bess"}
  ],
  "expected_grid_import_kwh": 2280,
  "self_sufficiency_confidence": 0.76,
  "model_version": "v1.0.0"
}
```

---

## 4. Environment Readiness

### 4.1 Current Staging Readiness

| Component | State | Notes |
|-----------|-------|-------|
| API contracts | Ready | Endpoint schemas defined in this document |
| Shared cloud inference environment | Available | Group AI platform cluster |
| MES / historian integration spec | Ready | See [mes-integration.md](./mes-integration.md) |
| Sensor design phase registry | Ready | See [sensor-map.md](./sensor-map.md) |
| Production training data | Not ready | Requires commissioned lines and validated quality outputs |

### 4.2 Production Dependencies

| Dependency | Status | Blocker |
|------------|--------|---------|
| On-site edge inference node | Pending | Control room/server room commissioning |
| Production historian feed | Pending | MES and OT integration not yet live |
| Solar/BESS telemetry | Pending | Utilities not commissioned |
| PET line quality feedback loop | Pending | PET line and QC lab correlation not yet live |
| Pentest close-out | Pending | Staging pentest execution still outstanding |

---

## 5. Security Controls

| Control | Implementation |
|---------|----------------|
| Authentication | OAuth 2.0 client credentials; JWT validation on all endpoints |
| Authorisation | Read-only for MES and reporting consumers in Phase 1/2 |
| Network segmentation | AI platform isolated from OT network; no direct SIS connectivity |
| Data in transit | TLS 1.3 mandatory |
| Data at rest | Encrypted storage for model artefacts and feature stores |
| Audit logging | Full request, token subject, and response code logging |
| Pentest | Governed by [pentest-scoping.md](./pentest-scoping.md) |

---

## 6. Production Go-Live Criteria

All of the following must be met before the platform is promoted from documented readiness to live factory use:

| Criterion | Verification Method |
|-----------|---------------------|
| Historian and MES feeds active for all Phase 1 lines | 24-hour live data capture review |
| Utilities telemetry stable for solar, BESS, and chillers | Trend review in historian |
| AI edge node commissioned in control room / MES room | Infrastructure handover certificate |
| Pentest High/Critical findings closed | Security close-out report |
| Model validation against QC and production data completed | AI model validation sign-off |
| Response latency and availability targets met | Load / health-check report |

---

## 7. Current Status Summary

The AI platform is **design-ready but not production-live**. The repository now contains the
service inventory, interfaces, and promotion criteria required for Gate 1. The remaining work
is primarily machine- and commissioning-dependent.

*For model alignment, refer to [automation-roadmap.md](./automation-roadmap.md) and [mes-integration.md](./mes-integration.md).*
*For security readiness, refer to [pentest-scoping.md](./pentest-scoping.md).*
