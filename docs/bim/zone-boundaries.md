# BIM Zone Boundaries

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)  
**Document:** Zone Polygon Definitions & Interfaces v2.0  
**Status:** PLANNED — Planning-Grade Baseline (🟡 P)  
**Artifact Grade:** 🟡 Planning — coordinates are design-intent estimates (±0.5 m); IFC GUIDs are planning-grade placeholders pending architect model delivery

---

## 1. Coordinate Basis

- Site datum: **NW corner** of the starting production block (local survey origin)
- Coordinate unit: **meters (m)**
- Polygon format: `(x, y)` clockwise from NW corner
- All boundaries below are planning geometry derived from [docs/floor-plan.md](../floor-plan.md)
- **Coordinate accuracy:** Planning-grade ±0.5 m; resurvey to ±50 mm required before Gate 3 closure
- **IFC model reference:** Architect to deliver IFC 4.3 file; GUIDs below are planning-grade placeholders — replace with authoring-tool GUIDs on model receipt

### 1.1 IFC Model Traceability

| IFC Attribute | Value |
|---------------|-------|
| IFC schema | IFC 4.3 (ISO 16739-1:2024) |
| Target object type | `IfcSpace` (one per zone) |
| GUID source | Architect BIM authoring tool (Revit / ArchiCAD) on model delivery |
| Placeholder format | `PLAN-ZONE-{letter}-v1` — replaced with real GUID at Gate 3 |
| Model delivery milestone | FEED (Front End Engineering Design) stage |

---

## 2. Zone Polygon Definitions (A–H)

| Zone | Name | IFC GUID (Planning) | IFC Object Type | Boundary Owner | Coord Accuracy | Polygon Corners (m) | Area (m²) | Clear Height | Floor Loading | Key Clearance Requirements |
|------|------|---------------------|-----------------|----------------|----------------|----------------------|-----------|--------------|---------------|----------------------------|
| A | Extrusion Hall | `1fa0cc01-5afe-4b00-a001-0000000000a1` | `IfcSpace` | Production Manager | ±0.5 m 🟡 | `(24,10) (72,10) (72,40) (24,40)` | 1,440 | 10 m | 30 kN/m² | Crane and die-change aisles ≥ 3.0 m |
| B | Moulding Hall | `1fa0cc02-5afe-4b00-a001-0000000000b1` | `IfcSpace` | Production Manager | ±0.5 m 🟡 | `(24,40) (72,40) (72,70) (24,70)` | 1,440 | 10 m | 30 kN/m² | Machine service aisle ≥ 2.5 m; robot cell clearance ≥ 1.5 m |
| C | Raw Material Warehouse | `1fa0cc03-5afe-4b00-a001-0000000000c1` | `IfcSpace` | Warehouse Manager | ±0.5 m 🟡 | `(0,10) (16,10) (16,30) (0,30)` | 320 | 8 m | 30 kN/m² | Forklift aisle ≥ 3.5 m; silo transfer corridor maintained |
| D | Chemical Hazmat Storage | `1fa0cc04-5afe-4b00-a001-0000000000d1` | `IfcSpace` | EHS Manager | ±0.5 m 🟡 | `(72,10) (84,10) (84,26) (72,26)` | 192 | 8 m | 30 kN/m² | Bunded floor at 110% largest container; restricted access envelope |
| E | Utilities Building | `1fa0cc05-5afe-4b00-a001-0000000000e1` | `IfcSpace` | Facilities / Maintenance Manager | ±0.5 m 🟡 | `(48,70) (68,70) (68,85) (48,85)` | 300 | 8 m | 30 kN/m² | Equipment maintenance clearance ≥ 1.2 m around major units |
| F | Control Room / MES | `1fa0cc06-5afe-4b00-a001-0000000000f1` | `IfcSpace` | Smart Factory Lead | ±0.5 m 🟡 | `(24,70) (36,70) (36,78) (24,78)` | 96 | 4 m | 7.5 kN/m² | Pressurised envelope and protected cable ingress |
| G | QC Laboratory | `1fa0cc07-5afe-4b00-a001-000000000001` | `IfcSpace` | QA Manager | ±0.5 m 🟡 | `(12,70) (24,70) (24,82) (12,82)` | 144 | 4 m | 7.5 kN/m² | Sample chain corridor to Zone B with contamination control |
| H | Finished Goods & Dispatch | `1fa0cc08-5afe-4b00-a001-000000000002` | `IfcSpace` | Warehouse Manager | ±0.5 m 🟡 | `(68,70) (92,70) (92,95) (68,95)` | 600 | 8 m | 30 kN/m² | Dock apron turning radius and quarantine bay segregation |

---

## 3. Zone-to-Zone Interface Points

| Interface ID | From | To | Type | IFC Object Type | Nominal Location (m) | Requirement |
|--------------|------|----|------|-----------------|----------------------|-------------|
| IF-A-C-01 | Zone C | Zone A | Raw material transfer | `IfcRelSpaceBoundary` | `(20,22)` | Forklift and pneumatic line coexistence |
| IF-D-A-01 | Zone D | Zone A | Controlled additive transfer | `IfcRelSpaceBoundary` | `(72,24)` | Permit-controlled transfer point |
| IF-A-B-01 | Zone A | Zone B | Internal production passage | `IfcDoor` / `IfcRelSpaceBoundary` | `(48,40)` | Clear width ≥ 3.0 m |
| IF-B-G-01 | Zone B | Zone G | QC sample handoff | `IfcRelSpaceBoundary` | `(24,74)` | Enclosed sample route |
| IF-B-F-01 | Zone B | Zone F | Controls/data interface | `IfcRelSpaceBoundary` | `(30,70)` | Segregated cable route |
| IF-E-A-01 | Zone E | Zone A | Utility distribution | `IfcRelSpaceBoundary` | `(48,70)` | Chilled water/compressed air manifold |
| IF-E-B-01 | Zone E | Zone B | Utility distribution | `IfcRelSpaceBoundary` | `(60,70)` | Chilled water/compressed air manifold |
| IF-B-H-01 | Zone B | Zone H | Finished goods transfer | `IfcDoor` / `IfcRelSpaceBoundary` | `(72,78)` | Outbound pallet corridor |

---

## 4. Spatial Compliance Constraints

The following boundary constraints are mandatory inputs for BIM model checking:

| Constraint | Spatial Rule | BIM Check Method |
|-----------|--------------|------------------|
| Fire escape travel distance | Max travel distance to exit ≤ 45 m | Clash/path check in Navisworks or Solibri |
| Fire routes | Minimum 2 escape routes from all occupied zones | Manual BIM walkthrough + fire engineer sign-off |
| Hose reel spacing | Reach coverage at ≤ 30 m intervals in production zones | BIM coverage sphere analysis |
| Hazmat containment | Zone D bunding volume ≥ 110% largest container | Volumetric check in BIM model |
| Emergency wash access | Eyewash/shower access at hazmat entry and production adjacency | Equipment placement check |
| Control room protection | Positive-pressure envelope maintained relative to production floor | MEP (HVAC) model coordination check |
| Utility maintenance access | Service envelope maintained around chiller/compressor/BESS equipment | Clearance envelope modelled as `IfcSpace` exclusion zone |

Regulatory and EHS reference: [docs/regulatory.md](../regulatory.md) and [docs/floor-plan.md](../floor-plan.md).

---

## 5. Zone Traceability Rules

The following rules must be enforced to maintain consistency across all Gate 3 documents.
Violations block Gate 3 closure.

1. **Zone-to-floor-plan consistency:** every zone polygon defined here must match the zones in [docs/floor-plan.md](../floor-plan.md) Section 2. Any discrepancy must be resolved in floor-plan.md first, then reflected here.
2. **Zone-to-asset-anchor consistency:** every `Zone` value in [asset-anchors.md](./asset-anchors.md) must be a letter (A–H) that matches a row in this table. Orphan zone references are invalid.
3. **Zone-to-sensor-map consistency:** every `Zone` column entry in [docs/sensor-map.md](../sensor-map.md) must map to a zone defined here.
4. **IFC GUID uniqueness:** no two zones may share the same GUID. On receipt of architect IFC, run a GUID uniqueness check before updating this document.
5. **GUID change control:** planning-grade GUIDs may be replaced only when the architect IFC is delivered and the new GUID is verified in the model. The superseded GUID must be recorded in the change log of this document.
6. **Boundary owner acknowledgement:** the boundary owner listed for each zone must acknowledge (via email or document sign-off) that the polygon and constraints are correct before Gate 3 closure.

---

## 6. Revision History

| Revision | Date | Author | Changes |
|----------|------|--------|---------|
| 1.0 | 2026-05-13 | Smart Factory Core Team | Initial planning-grade zone polygons and interface points |
| 2.0 | 2026-05-13 | Smart Factory Core Team | Added IFC GUID column (planning-grade), IFC object types, boundary owners, coordinate accuracy, BIM check methods, traceability rules |

---

*Polygon coordinates are planning-grade values (🟡 P) for Phase 1 and must be resurveyed to ±50 mm at FEED. Planning-grade IFC GUIDs must be replaced with architect model GUIDs before Gate 3 closure.*
