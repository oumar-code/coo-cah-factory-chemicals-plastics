# Coo-Cah Plastics & Polymers Factory — Intragroup Supply Coordination

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Plastics & Polymers Factory | **Factory ID:** CCH-PLS
> **Location:** Agbara Industrial Estate, Lagos State / Sagamu, Ogun State
> **Document Version:** 1.0 | **Owner:** Supply Chain Manager
> **Status:** Design complete — activation pending factory commissioning

---

## 1. Overview

The Plastics & Polymers Factory is the **primary internal plastics converter** for the
Coo-Cah manufacturing ecosystem. This document defines the recurring intercompany supply
relationships, call-off rules, service levels, escalation paths, and settlement principles
that govern materials flow between this factory and sister factories.

| Supply Relationship | Direction | Counterparty Factory | Materials | Operating Pattern |
|---------------------|-----------|----------------------|-----------|-------------------|
| Link A | Outbound | Kitchen Electronics Factory | ABS/PC housings, HIPS liners, SDA casings | Daily |
| Link B | Outbound | Consumer Goods factories | PET bottles, PET preforms, blown-film packaging | Daily / weekly |
| Link C | Outbound | Chemicals — Paint & Coatings Factory | HDPE jerrycans, pails, closures | Weekly |
| Link D | Inbound | Garage / Power Electronics Factory | UPS and inverter backup units for control systems | One-off commissioning and support |

All intragroup movements are governed by the **Coo-Cah Group Transfer Pricing Policy** and
recorded in the group ERP through intercompany purchase orders, delivery notes, and
goods-receipt confirmations.

---

## 2. Link A — Plastics Factory -> Kitchen Electronics Factory

### 2.1 Materials Supplied

| Component Family | Example Part Prefix | Specification | Nominal Volume | Safety Stock at Receiver |
|------------------|---------------------|---------------|----------------|--------------------------|
| Refrigerator interior liners | `CCK-PLAS-REF-LIN` | HIPS, food-safe, no-warp cosmetic finish | 320 units/day | 7 days |
| Microwave outer housings | `CCK-PLAS-MW-HSG` | ABS HH, cosmetic class A | 200 units/day | 7 days |
| Small appliance housing sets | `CCK-PLAS-SDA-*` | ABS/PP blends, food-contact where applicable | 1,200 units/day combined | 7 days |
| Cooker control housings | `CCK-PLAS-CK-PNL` | Heat-resistant PC+ABS | 180 units/day | 7 days |

### 2.2 Delivery Model

| Parameter | Detail |
|-----------|--------|
| Dispatch frequency | Two runs per day |
| First dispatch | 06:00 WAT |
| Second dispatch | 13:00 WAT |
| Route | Plastics Factory dispatch -> Agbara/Sagamu industrial corridor -> Kitchen Electronics receiving dock |
| Packaging | Reusable dunnage trays and labelled pallets |
| Transport owner | Coo-Cah Group Logistics |

### 2.3 Call-Off Rules

1. Kitchen Electronics sends the next-day call-off by 15:00 WAT.
2. Plastics Factory confirms within 2 hours.
3. Quantities may change by plus or minus 15% until 20:00 WAT.
4. Emergency top-up requests target a 4-hour response for critical SKUs.

### 2.4 Service Levels

| KPI | Target | Escalation Trigger |
|-----|--------|-------------------|
| On-time delivery | At least 97% | Below 95% in a week |
| Quantity accuracy | At least 99% | Below 98% in a week |
| Incoming quality pass rate | At least 98% | Below 96% in any shipment |
| Emergency response | Within 4 hours | Any miss |

---

## 3. Link B — Plastics Factory -> Consumer Goods Factories

### 3.1 Materials Supplied

| Product | Example SKU / Family | Use Case | Replenishment Pattern |
|---------|----------------------|----------|-----------------------|
| PET bottles | `CCH-PLS-004` variants | Bottled water, household chemicals, personal care | Daily |
| PET preforms | PET preform family | Receiver-side blow-moulding where required | Weekly |
| Blown-film rolls | `CCH-PLS-003` variants | Sachet, pouch, shrink, and overwrap packaging | Daily |
| Foam protective inserts | `CCH-PLS-005` | Secondary packaging and transit protection | Weekly |

### 3.2 Operating Principles

- Consumer Goods factories provide a rolling 14-day forecast every Friday.
- Locked production call-offs are issued daily for the next 72 hours.
- High-volume PET and blown-film orders are prioritised over lower-volume custom moulding during constrained capacity windows.
- Food-contact and cosmetic-packaging lots require traceable QC release before dispatch.

### 3.3 SLA

| KPI | Target |
|-----|--------|
| Forecast adherence | At least 90% within locked 72-hour window |
| OTIF (on-time in-full) | At least 95% |
| QC release lead time | Same-day for standard SKUs |
| Batch traceability completeness | 100% |

---

## 4. Link C — Plastics Factory -> Chemicals Paint & Coatings Factory

### 4.1 Materials Supplied

| Product | Specification | Typical Pattern |
|---------|---------------|-----------------|
| HDPE jerrycans | 1 L, 4 L, 20 L chemical-resistant containers | Weekly truckload |
| Paint pails and lids | Stackable pail sets | Weekly or campaign-based |
| Closures and fitments | Tamper-evident caps and accessories | Weekly |

### 4.2 Special Handling Rules

| Requirement | Detail |
|-------------|--------|
| Chemical compatibility | Only approved resin and colour masterbatch combinations allowed |
| Batch segregation | Packaging lots for regulated chemicals remain segregated through dispatch |
| Returnables | Defective lots returned with NCR reference and quarantine label |
| Emergency buffer | Receiver maintains at least 5 production days of containers |

---

## 5. Link D — Garage / Power Electronics Factory -> Plastics Factory

This link supports control-system resilience rather than recurring materials supply.

| Item | Purpose | Quantity | Timing |
|------|---------|----------|--------|
| Rack-mount UPS units | MES room, historian, and network backup power | 6 units | Commissioning |
| Pure sinewave inverter units | Critical DCS/SIS resilience for short outages | 2 units | Commissioning |
| Warranty support | Repair / replacement | As needed | Post-commissioning |

---

## 6. Escalation Path

| Level | Trigger | Action | Owner |
|-------|---------|--------|-------|
| Level 1 | Single late or short shipment | Planner-to-planner resolution | Supply Chain Coordinator |
| Level 2 | Repeated SLA miss in one week | Ops manager review and recovery plan | Supply Chain Manager |
| Level 3 | Three-day disruption or major quality incident | Cross-factory recovery meeting | Group Supply Chain Director |
| Level 4 | Five-day sustained outage | Executive intervention and external sourcing activation | Group CEO / COO |

---

## 7. Transfer Pricing & Settlement

| Parameter | Detail |
|-----------|--------|
| Pricing basis | Group cost plus standard transfer markup |
| Settlement cycle | Monthly intercompany netting |
| Currency | Nigerian Naira |
| Evidence | ERP PO, dispatch note, receiver GRN, and invoice |
| Dispute path | Supply Chain Director to Group CFO |

---

## 8. Disruption Protocol

If the Plastics Factory cannot supply a critical intercompany SKU:

1. Receiving factory consumes on-hand safety stock.
2. Cross-factory review confirms expected outage length within 4 hours.
3. Approved external converter is activated if outage exceeds 72 hours.
4. Production schedules across affected factories are re-prioritised by the Group Supply Chain Director.

---

*For raw material sourcing context, refer to [supply-chain.md](./supply-chain.md).*
*For implementation dependencies, refer to [implementation-plan.md](./implementation-plan.md).*
