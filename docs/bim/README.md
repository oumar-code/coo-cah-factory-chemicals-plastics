# BIM Layer Overview

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)  
**Document:** BIM Subdirectory Overview v1.0  
**Status:** PLANNED — FEED Alignment Baseline

---

## 1. Purpose

The BIM (Building Information Modelling) layer maps:

- Physical asset coordinates and anchor points
- Zone polygons and interface boundaries
- Spatial clearance and compliance constraints

onto the factory digital twin asset model.

This enables traceability between floor layout, asset registry, instrumentation, and operational analytics.

---

## 2. Source-of-Truth Relationships

| Domain | Authoritative Source |
|--------|----------------------|
| 2D layout basis and zone intent | [docs/floor-plan.md](../floor-plan.md) |
| Asset hierarchy and digital twin IDs | [docs/digital-twin.md](../digital-twin.md) |
| Sensor tag coverage and gateways | [docs/sensor-map.md](../sensor-map.md) |

---

## 3. BIM Standard and Naming Convention

- **Model exchange standard:** IFC 4.x (target at FEED and detailed design)
- **Authoring environment:** Revit-compatible workflow (exact authoring package finalised at FEED)
- **Coordinate convention:** local site datum (NW origin), metric units in meters
- **File naming convention:** `CCH-PLS_BIM_<discipline>_<revision>.<ext>`
  - Example: `CCH-PLS_BIM_ARCH_R01.ifc`
  - Example: `CCH-PLS_BIM_MEP_R01.rvt`

---

## 4. Documents in this BIM Folder

| Document | Purpose |
|----------|---------|
| [asset-anchors.md](./asset-anchors.md) | Major-asset grid references and approximate X/Y anchor positions |
| [zone-boundaries.md](./zone-boundaries.md) | Zone polygon extents, interface points, and spatial constraints |

---

*BIM coordinates are preliminary planning anchors and must be refined and locked at FEED/detailed design stage.*
