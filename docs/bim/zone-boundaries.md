# BIM Zone Boundaries

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)  
**Document:** Zone Polygon Definitions & Interfaces v1.0  
**Status:** PLANNED — Layout Basis

---

## 1. Coordinate Basis

- Site datum: **NW corner** of the starting production block
- Coordinate unit: **meters (m)**
- Polygon format: `(x, y)` clockwise from NW corner
- All boundaries below are planning geometry derived from [docs/floor-plan.md](../floor-plan.md)

---

## 2. Zone Polygon Definitions (A–H)

| Zone | Name | Polygon Corners (m) | Area (m²) | Clear Height | Floor Loading | Key Clearance Requirements |
|------|------|----------------------|-----------|--------------|---------------|----------------------------|
| A | Extrusion Hall | `(24,10) (72,10) (72,40) (24,40)` | 1,440 | 10 m | 30 kN/m² | Crane and die-change aisles ≥ 3.0 m |
| B | Moulding Hall | `(24,40) (72,40) (72,70) (24,70)` | 1,440 | 10 m | 30 kN/m² | Machine service aisle ≥ 2.5 m; robot cell clearance ≥ 1.5 m |
| C | Raw Material Warehouse | `(0,10) (16,10) (16,30) (0,30)` | 320 | 8 m | 30 kN/m² | Forklift aisle ≥ 3.5 m; silo transfer corridor maintained |
| D | Chemical Hazmat Storage | `(72,10) (84,10) (84,26) (72,26)` | 192 | 8 m | 30 kN/m² | Bunded floor at 110% largest container; restricted access envelope |
| E | Utilities Building | `(48,70) (68,70) (68,85) (48,85)` | 300 | 8 m | 30 kN/m² | Equipment maintenance clearance ≥ 1.2 m around major units |
| F | Control Room / MES | `(24,70) (36,70) (36,78) (24,78)` | 96 | 4 m | 7.5 kN/m² | Pressurised envelope and protected cable ingress |
| G | QC Laboratory | `(12,70) (24,70) (24,82) (12,82)` | 144 | 4 m | 7.5 kN/m² | Sample chain corridor to Zone B with contamination control |
| H | Finished Goods & Dispatch | `(68,70) (92,70) (92,95) (68,95)` | 600 | 8 m | 30 kN/m² | Dock apron turning radius and quarantine bay segregation |

---

## 3. Zone-to-Zone Interface Points

| Interface ID | From | To | Type | Nominal Location (m) | Requirement |
|--------------|------|----|------|----------------------|-------------|
| IF-A-C-01 | Zone C | Zone A | Raw material transfer | `(20,22)` | Forklift and pneumatic line coexistence |
| IF-D-A-01 | Zone D | Zone A | Controlled additive transfer | `(72,24)` | Permit-controlled transfer point |
| IF-A-B-01 | Zone A | Zone B | Internal production passage | `(48,40)` | Clear width ≥ 3.0 m |
| IF-B-G-01 | Zone B | Zone G | QC sample handoff | `(24,74)` | Enclosed sample route |
| IF-B-F-01 | Zone B | Zone F | Controls/data interface | `(30,70)` | Segregated cable route |
| IF-E-A-01 | Zone E | Zone A | Utility distribution | `(48,70)` | Chilled water/compressed air manifold |
| IF-E-B-01 | Zone E | Zone B | Utility distribution | `(60,70)` | Chilled water/compressed air manifold |
| IF-B-H-01 | Zone B | Zone H | Finished goods transfer | `(72,78)` | Outbound pallet corridor |

---

## 4. Spatial Compliance Constraints

The following boundary constraints are mandatory inputs for BIM model checking:

| Constraint | Spatial Rule |
|-----------|--------------|
| Fire escape travel distance | Max travel distance to exit ≤ 45 m |
| Fire routes | Minimum 2 escape routes from all occupied zones |
| Hose reel spacing | Reach coverage at ≤ 30 m intervals in production zones |
| Hazmat containment | Zone D bunding volume ≥ 110% largest container |
| Emergency wash access | Eyewash/shower access at hazmat entry and production adjacency |
| Control room protection | Positive-pressure envelope maintained relative to production floor |
| Utility maintenance access | Service envelope maintained around chiller/compressor/BESS equipment |

Regulatory and EHS reference: [docs/regulatory.md](../regulatory.md) and [docs/floor-plan.md](../floor-plan.md).

---

*Polygon coordinates are planning-grade values for Phase 1 and must be refined at FEED and detailed engineering.*
