# BIM and Sensor Traceability Matrix

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)  
**Document:** BIM and Sensor Traceability Matrix v1.0  
**Status:** ACTIVE — cross-document consistency baseline  

---

## 1. Purpose

This matrix is the cross-check artifact for GAP-006, GAP-007, GAP-008, and GAP-012. It ensures
that the critical assets used in BIM, digital twin, sensor, and simulation documents resolve to a
single consistent chain of references.

---

## 2. Critical Asset Traceability

| Asset ID | Zone | Zone GUID Ref | Anchor GUID | Historian Base Path | Primary Gateway / Bridge | Primary Simulation Use |
| --- | --- | --- | --- | --- | --- | --- |
| EXT-A1-01 | A | `1fa0cc01-5afe-4b00-a001-0000000000a1` | `2ea10001-7b3c-4d00-8001-a10000000001` | `PI\\CCH-PLS\AREA-A\UNIT-A1\EXT-A1-01\` | `IOT-GW-A-THERMAL-01` + area A gateways | SC-001, SC-004 |
| EXT-A2-01 | A | `1fa0cc01-5afe-4b00-a001-0000000000a1` | `2ea10001-7b3c-4d00-8001-a20000000001` | `PI\\CCH-PLS\AREA-A\UNIT-A2\EXT-A2-01\` | area A gateways | SC-001 |
| EXT-A2-02 | A | `1fa0cc01-5afe-4b00-a001-0000000000a1` | `2ea10001-7b3c-4d00-8001-a20000000002` | `PI\\CCH-PLS\AREA-A\UNIT-A2\EXT-A2-02\` | area A gateways | SC-001 |
| EXT-A2-03 | A | `1fa0cc01-5afe-4b00-a001-0000000000a1` | `2ea10001-7b3c-4d00-8001-a20000000003` | `PI\\CCH-PLS\AREA-A\UNIT-A2\EXT-A2-03\` | area A gateways | SC-001 |
| EXT-A3-01 | A | `1fa0cc01-5afe-4b00-a001-0000000000a1` | `2ea10001-7b3c-4d00-8001-a30000000001` | `PI\\CCH-PLS\AREA-A\UNIT-A3\EXT-A3-01\` | area A gateways | SC-003 |
| IM-B1-01 | B | `1fa0cc02-5afe-4b00-a001-0000000000b1` | `2ea10001-7b3c-4d00-8001-b10000000002` | `PI\\CCH-PLS\AREA-B\UNIT-B1\IM-B1-01\` | `MES-OPCUA-BRIDGE-01` + area B gateways | SC-001 |
| SBM-B1-01 | B | `1fa0cc02-5afe-4b00-a001-0000000000b1` | `2ea10001-7b3c-4d00-8001-b10000000005` | `PI\\CCH-PLS\AREA-B\UNIT-B1\SBM-B1-01\` | `MES-OPCUA-BRIDGE-01` + `IOT-GW-B-PET-01` | SC-001 |
| CHILL-E1-01 | E | `1fa0cc05-5afe-4b00-a001-0000000000e1` | `2ea10001-7b3c-4d00-8001-e10000000001` | `PI\\CCH-PLS\AREA-E\UNIT-E1\CHILL-E1-01\` | `IOT-GW-E-UTIL-01` | SC-002 |
| COMP-E2-01 | E | `1fa0cc05-5afe-4b00-a001-0000000000e1` | `2ea10001-7b3c-4d00-8001-e20000000001` | `PI\\CCH-PLS\AREA-E\UNIT-E2\COMP-E2-01\` | `IOT-GW-E-UTIL-01` | SC-002 |
| SOLAR-E3-01 | E | `1fa0cc05-5afe-4b00-a001-0000000000e1` | `2ea10001-7b3c-4d00-8001-e30000000001` | `PI\\CCH-PLS\AREA-E\UNIT-E3\SOLAR-E3-01\` | `IOT-GW-E-ENERGY-01` | SC-002 |
| BESS-E3-01 | E | `1fa0cc05-5afe-4b00-a001-0000000000e1` | `2ea10001-7b3c-4d00-8001-e30000000003` | `PI\\CCH-PLS\AREA-E\UNIT-E3\BESS-E3-01\` | `IOT-GW-E-BESS-01` | SC-002 |
| GEN-E3-01 | E | `1fa0cc05-5afe-4b00-a001-0000000000e1` | `2ea10001-7b3c-4d00-8001-e30000000005` | `PI\\CCH-PLS\AREA-E\UNIT-E3\GEN-E3-01\` | `IOT-GW-E-GEN-01` | SC-002 |

---

## 3. Zone Consistency Rules

| Rule | Control |
| --- | --- |
| Zone reference must exist in BIM zone register | Validate against `bim/zone-boundaries.md` before updates |
| Anchor GUID must exist in asset anchor register | Validate against `bim/asset-anchors.md` before updates |
| Historian base path must exist in sensor mapping tables | Validate against `sensor-map.md` before commissioning handover |
| Simulation use-case assignment must exist in simulation baseline or contract | Validate against `simulation-signoff-baseline.md` and `simulation-readiness.md` |

---

## 4. Traceability Exception Register

| Exception | Impact | Required Action |
| --- | --- | --- |
| `GRID-E3-01_PI_IMPORT` is a logical utility meter tag and is not yet represented as a spatial BIM anchor | Does not block planning baseline, but blocks full spatial completeness if left unresolved | Assign commissioning pack ownership under UNIT-E3 and add physical meter anchor if required at detailed design |

---

## 5. Review Outcome

At this stage, the critical simulation-facing assets align across the current planning-grade BIM,
digital twin, and sensor documents. Remaining work is commissioning evidence, not document
structure.

---

*Use this matrix as the working cross-check before any Gate 3 document is updated from planning
grade to commissioning grade.*
