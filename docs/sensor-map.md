# Plastics — Sensor Map

> **Gate 3 Artifact (Digital Twin Spatial Readiness)**

This standalone sensor map is the source of truth for physical sensor placement and calibration governance for **Plastics**.

## 1. Sensor Registry

| Sensor ID | Sensor Model | Sensor Type | Location (Zone) | Mounted On (Asset ID) | Anchor Ref | Protocol | Calibration Interval | Last Calibration | Data Owner | Notes |
|-----------|--------------|-------------|------------------|-----------------------|------------|----------|----------------------|------------------|------------|-------|
| [SENSOR_ID] | [MODEL] | [TYPE] | [ZONE_ID] | [DT-ASSET-ID] | [ANCHOR_ID] | [MQTT/OPC-UA/Modbus/REST] | [INTERVAL] | [YYYY-MM-DD] | [TEAM/ROLE] | [NOTES] |

## 2. Naming and Mapping Rules

- `Location (Zone)` values MUST match zone IDs used in [`floor-plan.md`](../floor-plan.md).
- `Mounted On (Asset ID)` values MUST match asset IDs used in [`digital-twin.md`](../digital-twin.md).
- `Anchor Ref` values MUST map to anchors in [`bim/asset-anchors.md`](./bim/asset-anchors.md).

