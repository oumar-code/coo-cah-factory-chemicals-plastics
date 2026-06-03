# Commissioning Data Acceptance Checklist

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)  
**Document:** Commissioning Data Acceptance Checklist v1.0  
**Status:** READY FOR COMMISSIONING PREP  

---

## 1. Purpose

This checklist defines the evidence needed before historian, MES, and simulation datasets can be
treated as accepted for Gate 3 closure work.

It converts the SLAs and dataset thresholds already defined in `sensor-map.md` and
`simulation-readiness.md` into a commissioning handover checklist.

---

## 2. Historian Infrastructure Readiness

- [ ] Historian server commissioned and reachable from approved OT segments.
- [ ] NTP synchronisation confirmed across DCS, gateways, historian, and MES servers.
- [ ] Gateway inventory approved and mapped to each critical asset group.
- [ ] Read-only extraction path for simulation and AI consumers validated.

---

## 3. Tag Acceptance Checks

| Check | Threshold | Evidence |
| --- | --- | --- |
| Tag completeness | `>= 99.0%` per day | Historian completeness report |
| Critical tag completeness | `>= 99.5%` per day | Critical-tag subset report |
| Bad-tag rate | `< 0.5%` per asset per day | Quality flag or bad-tag report |
| Historian lag | `<= 10 s` | End-to-end timestamp comparison |
| OPC UA bridge persistence | `<= 2 s` for 1-second tags | Commissioning probe record |
| MQTT to historian latency | `<= 5 s` for 10-second tags | Gateway log comparison |
| Duplicate timestamps | Zero duplicates in frozen dataset | Dataset validation report |

---

## 4. MES Dataset Acceptance Checks

| Check | Minimum | Evidence |
| --- | --- | --- |
| Completed production orders for active start-up lines | `>= 50` per line | MES extract summary |
| OEE population window | `>= 30 days` | MES OEE report |
| Batch material traceability | `100%` linkage for included orders | Traceability audit |
| Recipe exports | All active Phase 1 recipes exported and versioned | Recipe export log |
| Shift and downtime reporting | Minimum 30 shift reports | MES reporting archive |

---

## 5. Simulation Freeze Readiness

- [ ] Required BIM geometry set extracted and versioned.
- [ ] Required asset metadata extracted and versioned.
- [ ] Historian tag dictionary aligned to approved asset and zone references.
- [ ] Dataset extraction timestamp recorded.
- [ ] Deferred live-data gaps logged where required windows are not yet available.

---

## 6. Sign-Off Routing

| Area | Primary Sign-Off | Co-Sign |
| --- | --- | --- |
| Historian and gateway quality | Smart Factory Lead | Process Engineer |
| MES order and recipe data | MES Lead | Operations Lead |
| Simulation dataset freeze | Process Engineer | Smart Factory Lead |
| Utility and energy data | Facilities / Energy Manager | Smart Factory Lead |

---

## 7. Handover Rule

No dataset may be marked "accepted for simulation or AI validation" unless all applicable checks in
Sections 2 through 6 are complete and the evidence is logged in the
[gate3-evidence-dashboard.md](./gate3-evidence-dashboard.md).

---

*This checklist is the commissioning acceptance companion to the planning-stage readiness
documents.*
