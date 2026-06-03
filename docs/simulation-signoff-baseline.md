# Simulation Sign-Off Baseline

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)  
**Document:** Simulation Sign-Off Baseline v1.0  
**Status:** READY FOR WORKSHOP — first baseline frozen for planning-stage sign-off  
**Related Contract:** [simulation-readiness.md](./simulation-readiness.md)

---

## 1. Purpose

This document freezes the first simulation planning baseline for Gate 3 preparation. It separates
what can be signed now from what must wait for live commissioning data.

The intent is to let Engineering, Smart Factory, and Operations sign off the structure, source
documents, and deferred data gaps without incorrectly claiming production-data readiness.

---

## 2. Baseline Boundary

| Use-Case | Baseline Decision | Reason |
| --- | --- | --- |
| SC-001 — Throughput and bottleneck analysis | Freeze planning baseline now | BIM geometry, asset metadata, recipe structure, and order-history requirements are defined |
| SC-002 — Energy scheduling optimisation | Freeze planning baseline now | Utility model boundary, tariff requirement, and telemetry needs are defined |
| SC-003 — Material flow and inventory simulation | Freeze planning baseline now | Supply-chain logic and material-flow boundaries are already documented |
| SC-004 — PdM what-if analysis | Freeze scope only; defer dataset freeze | Requires 60-day gearbox vibration and temperature baseline |

---

## 3. Frozen Inputs for Workshop Sign-Off

| Dataset Element | Source | Freeze Status |
| --- | --- | --- |
| Zone geometry for Zones A, B, C, E, and H | [bim/zone-boundaries.md](./bim/zone-boundaries.md) | Frozen at planning grade |
| Asset metadata for Area A and B critical assets | [digital-twin.md](./digital-twin.md), [bim/asset-anchors.md](./bim/asset-anchors.md) | Frozen at planning grade |
| Historian tag dictionary and base paths | [sensor-map.md](./sensor-map.md) | Frozen as commissioning target map |
| MES endpoints and recipe structures | [mes-integration.md](./mes-integration.md) | Frozen at design basis |
| Material flow rules and lead-time logic | [intragroup-supply-coordination.md](./intragroup-supply-coordination.md), [supply-chain.md](./supply-chain.md) | Frozen |
| Energy architecture assumptions | [energy-profile.md](./energy-profile.md), [automation-roadmap.md](./automation-roadmap.md) | Frozen |

---

## 4. Explicitly Deferred Inputs

| Deferred Item | Trigger to Unfreeze |
| --- | --- |
| 30-day historian windows for SC-001 and SC-002 | MES / historian commissioning live and validated |
| 50+ completed production orders per active line | Phase 1 lines in production service |
| QC reject and yield history | QC lab and MES quality integration live |
| 60-day gearbox baseline for SC-004 | Extruder gearbox sensors in service and historian completeness accepted |

---

## 5. Workshop Sign-Off Checklist

| Sign-Off Owner | Decision Required |
| --- | --- |
| Engineering Lead | Confirm process boundaries and asset set are sufficient for first models |
| Smart Factory Lead | Confirm source systems, data paths, and deferred-data assumptions |
| Operations Lead | Confirm operational scenarios and review cadence |

- [ ] SC-001 boundary approved.
- [ ] SC-002 boundary approved.
- [ ] SC-003 boundary approved.
- [ ] SC-004 deferred-data conditions acknowledged.
- [ ] Deferred live-data dependencies accepted as blockers, not scope gaps.

---

## 6. First Trial-Run Entry Criteria

The first simulation trial run may only start when all of the following are true:

1. Relevant live historian and MES windows have met the thresholds in
   [simulation-readiness.md](./simulation-readiness.md).
2. Asset IDs, zone references, and historian paths match the
   [bim-sensor-traceability-matrix.md](./bim-sensor-traceability-matrix.md).
3. Dataset extraction and freeze evidence is recorded in the
   [gate3-evidence-dashboard.md](./gate3-evidence-dashboard.md).

---

## 7. Baseline Outcome

This baseline lets the programme move forward on governance, scope, and data-preparation design
without incorrectly treating planning-grade inputs as live operational validation.

---

*This document should be reviewed together with the simulation readiness package and the
commissioning data acceptance checklist.*
