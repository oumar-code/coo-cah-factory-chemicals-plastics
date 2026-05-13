# BIM Asset Anchors

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)  
**Document:** Asset Spatial Anchor Register v2.0  
**Status:** PLANNED — Planning-Grade Baseline (🟡 P)  
**Artifact Grade:** 🟡 Planning — coordinates ±0.5 m; BIM GUIDs are planning-grade placeholders

---

## 1. Grid Reference System

- Building grid is based on the layout basis in [docs/floor-plan.md](../floor-plan.md)
- Grid columns: **A–G**
- Grid rows: **1–8**
- Nominal bay module reference: **12 m × 24 m planning grid**
- Coordinates are `(X, Y, Z)` meters measured from **NW site datum** (Z = floor level above site datum)

Grid labels are used for operational readability, while X/Y/Z values support BIM exchange.

### 1.1 GUID and Grading Policy

| Grade | Symbol | GUID Format | Coordinate Tolerance |
|-------|--------|-------------|----------------------|
| Planning | 🟡 P | `2ea1XXXX-7b3c-4d00-8001-{area}{seq}` — planning placeholder | ±0.5 m |
| Commissioning | 🟠 C | Replaced with equipment nameplate / delivery survey value | ±0.1 m |
| As-Built | 🟢 AB | Locked in architect IFC model; BIM GUID from authoring tool | ±10 mm |

- IFC object type: `IfcDistributionFlowElement` (process equipment); `IfcFlowTerminal` (sensors/meters)
- All planning-grade GUIDs are prefixed `2ea1` to distinguish from as-built GUIDs
- No asset may remain at planning grade after commissioning sign-off

### 1.2 Traceability Rules

1. Every `Asset ID` in this register must match an entry in [docs/digital-twin.md](../digital-twin.md) Section 2 (Process Asset Registry).
2. Every `Zone` value must match a zone letter (A–H) in [zone-boundaries.md](./zone-boundaries.md) Section 2.
3. Every `BIM GUID` must be unique across this register. Duplicate GUIDs are invalid.
4. When a planning GUID is replaced with an authoring-tool GUID, the old value must be recorded in the revision history of this document.
5. `digital-twin.md` is the authoritative source for Asset IDs; this document is the authoritative source for spatial coordinates and BIM GUIDs. Any discrepancy in Asset ID must be resolved in digital-twin.md first.

---

## 2. Anchor Register — Area A (Extrusion Hall)

| Asset ID | Digital Twin Ref | Zone | Zone IFC GUID (ref) | Bay Grid Ref | X (m) | Y (m) | Z (m) | XY Tolerance | BIM GUID | Grade | Commissioning Status |
|----------|-----------------|------|---------------------|--------------|-------|-------|-------|--------------|----------|-------|----------------------|
| EXT-A1-01 | [UNIT-A1](../digital-twin.md) | A | `1fa0cc01-…-a1` | B2 | 30 | 18 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a10000000001` | 🟡 P | Planned |
| DIE-A1-01 | [UNIT-A1](../digital-twin.md) | A | `1fa0cc01-…-a1` | B2 | 32 | 18 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a10000000002` | 🟡 P | Planned |
| AIR-A1-01 | [UNIT-A1](../digital-twin.md) | A | `1fa0cc01-…-a1` | B2 | 34 | 18 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a10000000003` | 🟡 P | Planned |
| NIP-A1-01 | [UNIT-A1](../digital-twin.md) | A | `1fa0cc01-…-a1` | B2 | 36 | 18 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a10000000004` | 🟡 P | Planned |
| WIND-A1-01 | [UNIT-A1](../digital-twin.md) | A | `1fa0cc01-…-a1` | C2 | 39 | 18 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a10000000005` | 🟡 P | Planned |
| WIND-A1-02 | [UNIT-A1](../digital-twin.md) | A | `1fa0cc01-…-a1` | C2 | 42 | 18 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a10000000006` | 🟡 P | Planned |
| EXT-A2-01 | [UNIT-A2](../digital-twin.md) | A | `1fa0cc01-…-a1` | C3 | 42 | 26 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a20000000001` | 🟡 P | Planned |
| EXT-A2-02 | [UNIT-A2](../digital-twin.md) | A | `1fa0cc01-…-a1` | D3 | 46 | 26 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a20000000002` | 🟡 P | Planned |
| EXT-A2-03 | [UNIT-A2](../digital-twin.md) | A | `1fa0cc01-…-a1` | D3 | 50 | 26 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a20000000003` | 🟡 P | Planned |
| DIE-A2-01 | [UNIT-A2](../digital-twin.md) | A | `1fa0cc01-…-a1` | D3 | 53 | 26 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a20000000004` | 🟡 P | Planned |
| EXT-A3-01 | [UNIT-A3](../digital-twin.md) | A | `1fa0cc01-…-a1` | B4 | 30 | 34 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a30000000001` | 🟡 P | Planned |
| DIE-A3-01 | [UNIT-A3](../digital-twin.md) | A | `1fa0cc01-…-a1` | B4 | 33 | 34 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a30000000002` | 🟡 P | Planned |
| CAL-A3-01 | [UNIT-A3](../digital-twin.md) | A | `1fa0cc01-…-a1` | C4 | 38 | 34 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a30000000003` | 🟡 P | Planned |
| COOL-A3-01 | [UNIT-A3](../digital-twin.md) | A | `1fa0cc01-…-a1` | C4 | 43 | 34 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a30000000004` | 🟡 P | Planned |
| HAUL-A3-01 | [UNIT-A3](../digital-twin.md) | A | `1fa0cc01-…-a1` | D4 | 49 | 34 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-a30000000005` | 🟡 P | Planned |

---

## 3. Anchor Register — Area B (Moulding Hall)

| Asset ID | Digital Twin Ref | Zone | Zone IFC GUID (ref) | Bay Grid Ref | X (m) | Y (m) | Z (m) | XY Tolerance | BIM GUID | Grade | Commissioning Status |
|----------|-----------------|------|---------------------|--------------|-------|-------|-------|--------------|----------|-------|----------------------|
| DRY-B1-01 | [UNIT-B1](../digital-twin.md) | B | `1fa0cc02-…-b1` | B5 | 30 | 46 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-b10000000001` | 🟡 P | Planned |
| IM-B1-01 | [UNIT-B1](../digital-twin.md) | B | `1fa0cc02-…-b1` | C5 | 36 | 46 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-b10000000002` | 🟡 P | Planned |
| COOL-B1-01 | [UNIT-B1](../digital-twin.md) | B | `1fa0cc02-…-b1` | C5 | 40 | 46 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-b10000000003` | 🟡 P | Planned |
| CONV-B1-01 | [UNIT-B1](../digital-twin.md) | B | `1fa0cc02-…-b1` | D5 | 45 | 46 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-b10000000004` | 🟡 P | Planned |
| SBM-B1-01 | [UNIT-B1](../digital-twin.md) | B | `1fa0cc02-…-b1` | D5 | 50 | 46 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-b10000000005` | 🟡 P | Planned |
| IM-B2-01 | [UNIT-B2](../digital-twin.md) | B | `1fa0cc02-…-b1` | B6 | 30 | 56 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-b20000000001` | 🟡 P | Planned |
| IM-B3-01 | [UNIT-B3](../digital-twin.md) | B | `1fa0cc02-…-b1` | C6 | 40 | 56 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-b30000000001` | 🟡 P | Planned |
| IM-B4-01 | [UNIT-B4](../digital-twin.md) | B | `1fa0cc02-…-b1` | D6 | 50 | 56 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-b40000000001` | 🟡 P | Planned |

---

## 4. Anchor Register — Area E (Utilities)

| Asset ID | Digital Twin Ref | Zone | Zone IFC GUID (ref) | Bay Grid Ref | X (m) | Y (m) | Z (m) | XY Tolerance | BIM GUID | Grade | Commissioning Status |
|----------|-----------------|------|---------------------|--------------|-------|-------|-------|--------------|----------|-------|----------------------|
| CHILL-E1-01 | [UNIT-E1](../digital-twin.md) | E | `1fa0cc05-…-e1` | E7 | 54 | 74 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e10000000001` | 🟡 P | Planned |
| CT-E1-01 | [UNIT-E1](../digital-twin.md) | E | `1fa0cc05-…-e1` | F7 | 60 | 74 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e10000000002` | 🟡 P | Planned |
| PUMP-E1-01 | [UNIT-E1](../digital-twin.md) | E | `1fa0cc05-…-e1` | E7 | 56 | 77 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e10000000003` | 🟡 P | Planned |
| PUMP-E1-02 | [UNIT-E1](../digital-twin.md) | E | `1fa0cc05-…-e1` | E7 | 58 | 77 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e10000000004` | 🟡 P | Planned |
| COMP-E2-01 | [UNIT-E2](../digital-twin.md) | E | `1fa0cc05-…-e1` | F7 | 62 | 74 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e20000000001` | 🟡 P | Planned |
| COMP-E2-02 | [UNIT-E2](../digital-twin.md) | E | `1fa0cc05-…-e1` | F7 | 64 | 74 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e20000000002` | 🟡 P | Planned |
| DRY-E2-01 | [UNIT-E2](../digital-twin.md) | E | `1fa0cc05-…-e1` | F7 | 66 | 74 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e20000000003` | 🟡 P | Planned |
| SOLAR-E3-01 | [UNIT-E3](../digital-twin.md) | E | `1fa0cc05-…-e1` | G8 | 74 | 88 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e30000000001` | 🟡 P | Planned |
| INV-E3-01 | [UNIT-E3](../digital-twin.md) | E | `1fa0cc05-…-e1` | G8 | 72 | 86 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e30000000002` | 🟡 P | Planned |
| BESS-E3-01 | [UNIT-E3](../digital-twin.md) | E | `1fa0cc05-…-e1` | F8 | 64 | 84 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e30000000003` | 🟡 P | Planned |
| BESS-E3-02 | [UNIT-E3](../digital-twin.md) | E | `1fa0cc05-…-e1` | F8 | 66 | 84 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e30000000004` | 🟡 P | Planned |
| GEN-E3-01 | [UNIT-E3](../digital-twin.md) | E | `1fa0cc05-…-e1` | G7 | 70 | 76 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e30000000005` | 🟡 P | Planned |
| ETP-E4-01 | [UNIT-E4](../digital-twin.md) | E | `1fa0cc05-…-e1` | E8 | 52 | 84 | 0.00 | ±0.5 m | `2ea10001-7b3c-4d00-8001-e40000000001` | 🟡 P | Planned |

---

## 5. Cross-References

| Need | Document |
|------|----------|
| Asset hierarchy and IDs (authoritative) | [docs/digital-twin.md](../digital-twin.md) Section 2 |
| Zone polygons and constraints (authoritative) | [zone-boundaries.md](./zone-boundaries.md) Section 2 |
| Sensor tag mapping by asset | [docs/sensor-map.md](../sensor-map.md) |
| Simulation dataset requirements | [docs/simulation-readiness.md](../simulation-readiness.md) |

---

## 6. Coverage Summary

| Area | Total Assets in Register | Planning-Grade 🟡 | Commissioning-Grade 🟠 | As-Built 🟢 |
|------|--------------------------|-------------------|------------------------|-------------|
| Area A — Extrusion Hall | 15 | 15 | 0 | 0 |
| Area B — Moulding Hall | 8 | 8 | 0 | 0 |
| Area E — Utilities | 13 | 13 | 0 | 0 |
| **Total** | **36** | **36** | **0** | **0** |

Gate 3 closure requires: 0 planning-grade entries remaining; all 36 assets at Commissioning or As-Built grade.

---

## 7. Revision History

| Revision | Date | Author | Changes |
|----------|------|--------|---------|
| 1.0 | 2026-05-13 | Smart Factory Core Team | Initial planning-grade asset anchors (TBD GUID placeholders) |
| 2.0 | 2026-05-13 | Smart Factory Core Team | Replaced `TBD-*` GUIDs with planning-grade UUIDs; added Digital Twin Ref column; added Zone IFC GUID ref; added X/Y/Z with tolerance; added Grade column; added coverage summary; added traceability rules; added revision history |

---

*All coordinates are planning-grade (🟡 P) estimates. Final survey-validated coordinates and IFC-authoring-tool GUIDs must be recorded in revision 3.0 at FEED/detailed design stage. No asset may advance to production commissioning without its BIM anchor confirmed at Commissioning grade (🟠 C) or better.*
