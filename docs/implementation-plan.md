# Coo-Cah Plastics & Polymers Factory — Phase 1 Implementation Plan

> **Project Coo-Cah | AI-Powered Manufacturing Ecosystem**
> **Factory:** Coo-Cah Plastics & Polymers Factory | **Factory ID:** CCH-PLS
> **Location:** Agbara Industrial Estate, Lagos State / Sagamu, Ogun State
> **Document Version:** 1.0 | **Owner:** Factory Programme Director
> **Status:** Active — Phase 1 planning and documentation sprint

---

## 1. Purpose & Scope

This document defines the implementation plan for the Coo-Cah Plastics & Polymers Factory
from planning and design through to full Phase 1 production readiness. It consolidates the
programme workstreams, gate criteria, critical dependencies, and the machine-free deliverables
that can be completed before physical commissioning begins.

The plan is structured around three gates:

| Gate | Name | Criteria |
|------|------|----------|
| Gate 1 | Design Complete | All planning, readiness, cyber, BIM, and supply-chain documents signed off |
| Gate 2 | Infrastructure Ready | Site, utilities, control room, and core factory infrastructure commissioned |
| Gate 3 | Production Ready | Phase 1 lines, MES, quality systems, and supplier flows fully commissioned |

---

## 2. Programme Overview

| Phase | Period | Theme | Outcome |
|------|--------|-------|---------|
| Phase 1 | 2025–2027 | Foundation | Blown film, PET bottles/preforms, core utilities, MES, and initial intragroup supply |
| Phase 2 | 2028–2029 | Expansion | Injection moulding, HDPE pipe, recycling/compounding, live digital twin |
| Phase 3 | 2030+ | Optimisation | Autonomous control on approved loops, advanced AI optimisation, full ecosystem scale-up |

**Current Phase:** Phase 1 — Planning & design
**Strategic Priority:** Tier 1 critical infrastructure for all downstream Coo-Cah factories
**Master Repo Reference:** [oumar-code/Coo-Kah-Doks](https://github.com/oumar-code/Coo-Kah-Doks)

---

## 3. Workstream Structure

### Workstream 1 — Regulatory, Legal & Corporate Setup

**Lead:** Regulatory Affairs Manager
**Objective:** Secure all permits, licences, and legal entities required before operations begin.

| # | Deliverable | Owner | Target | Gate | Machine Required? |
|---|-------------|-------|--------|------|-------------------|
| R1 | Operating entity incorporated; RC and TIN issued | Legal / Finance | Q3 2025 | G1 | No |
| R2 | Lease for 5,000–8,000 m² starter bay executed | Legal / Finance | Q4 2025 | G1 | No |
| R3 | NESREA environmental operating path agreed | Regulatory Affairs | Q4 2025 | G1 | No |
| R4 | DPR/NUPRC feedstock handling requirements documented | Regulatory Affairs | Q4 2025 | G1 | No |
| R5 | NAFDAC food-contact plastics compliance path defined | Regulatory Affairs / QA | Q4 2025 | G1 | No |
| R6 | SON certification plan for structural plastics approved | Regulatory Affairs / QA | Q1 2026 | G2 | No |
| R7 | Fire service and local authority inspections completed | EHS / Facilities | Q2 2026 | G2 | Yes |
| R8 | Phase 1 licence pack complete | Regulatory Affairs | Q3 2026 | G3 | Yes |

### Workstream 2 — Site, Utilities & EHS Readiness

**Lead:** Facilities & Engineering Manager
**Objective:** Deliver the starter factory footprint, utilities, safety systems, and control-room environment.

| # | Deliverable | Owner | Target | Gate | Machine Required? |
|---|-------------|-------|--------|------|-------------------|
| F1 | Starter-bay layout locked against [floor-plan.md](./floor-plan.md) | Facilities | Q4 2025 | G1 | No |
| F2 | Utility load schedule approved (grid, diesel, solar, BESS, air, chilled water) | Utilities / Energy Team | Q4 2025 | G1 | No |
| F3 | Hazmat storage concept and ETP concept signed off | EHS / Facilities | Q4 2025 | G1 | No |
| F4 | Control room and MES room design completed | Smart Factory / Facilities | Q4 2025 | G1 | No |
| F5 | 33 kV or industrial tariff grid arrangement executed | Facilities / Finance | Q1 2026 | G2 | No |
| F6 | Solar PV, BESS, diesel backup, and compressor package commissioned | Utilities / Energy Team | Q2 2026 | G2 | Yes |
| F7 | Chilled water and process cooling systems commissioned | Facilities | Q2 2026 | G2 | Yes |
| F8 | ETP and hazmat containment systems certified | EHS / Facilities | Q3 2026 | G3 | Yes |

### Workstream 3 — Smart Factory, MES, AI & Cyber Readiness

**Lead:** Smart Factory Core Team / IT Manager
**Objective:** Stand up the digital backbone before physical production ramps.

| # | Deliverable | Owner | Target | Gate | Machine Required? |
|---|-------------|-------|--------|------|-------------------|
| S1 | MES integration architecture baseline approved | Smart Factory | Q4 2025 | G1 | No |
| S2 | AI platform status documented with stub endpoints | AI Platform Team | Q4 2025 | G1 | No |
| S3 | Penetration test scoping approved | InfoSec / Smart Factory | Q4 2025 | G1 | No |
| S4 | Sensor registry design phase complete | Smart Factory | Q4 2025 | G1 | No |
| S5 | BIM spatial model design set complete | BIM / Smart Factory | Q4 2025 | G1 | No |
| S6 | Factory network, server room, VPN, and historian infrastructure deployed | IT / Smart Factory | Q2 2026 | G2 | Yes |
| S7 | MES and historian commissioning complete | Smart Factory | Q3 2026 | G3 | Yes |
| S8 | Pentest executed and High/Critical findings closed | InfoSec / Vendor | Q3 2026 | G3 | No |

### Workstream 4 — Feedstock, Intragroup Supply & Logistics

**Lead:** Supply Chain Manager
**Objective:** Secure all inbound feedstocks and activate outbound intragroup delivery agreements.

| # | Deliverable | Owner | Target | Gate | Machine Required? |
|---|-------------|-------|--------|------|-------------------|
| SC1 | INDORAMA commercial engagement and draft long-term supply terms | Supply Chain | Q4 2025 | G1 | No |
| SC2 | Dangote downstream engagement opened for propylene / polymer intermediates | Supply Chain | Q4 2025 | G1 | No |
| SC3 | PET resin import protocol and approved agents finalised | Supply Chain / Finance | Q4 2025 | G1 | No |
| SC4 | Intragroup supply coordination document signed off | Supply Chain | Q4 2025 | G1 | No |
| SC5 | Safety stock policy configured in ERP/MES | Supply Chain / IT | Q2 2026 | G2 | No |
| SC6 | Daily outbound call-off model validated with sister factories | Supply Chain / Smart Factory | Q2 2026 | G2 | No |
| SC7 | First inbound polymer deliveries QC-cleared | Supply Chain / QA | Q3 2026 | G3 | Yes |
| SC8 | First intercompany deliveries to downstream factories achieved | Supply Chain / Operations | Q3 2026 | G3 | Yes |

### Workstream 5 — Production Equipment & Commissioning

**Lead:** Engineering & Production Manager
**Objective:** Procure, install, and ramp the Phase 1 process lines and supporting plant.

| # | Deliverable | Owner | Target | Gate | Machine Required? |
|---|-------------|-------|--------|------|-------------------|
| E1 | Blown film line ordered and FAT plan agreed | Procurement / Engineering | Q1 2026 | G2 | No |
| E2 | PET preform injection and SBM line ordered | Procurement / Engineering | Q1 2026 | G2 | No |
| E3 | DCS and SIS hardware package ordered | Procurement / Automation | Q1 2026 | G2 | No |
| E4 | QC lab equipment package ordered | QA / Procurement | Q1 2026 | G2 | No |
| E5 | Blown film line installed and dry commissioned | Engineering | Q2 2026 | G3 | Yes |
| E6 | PET preform and bottle line commissioned | Engineering | Q3 2026 | G3 | Yes |
| E7 | DCS/SIS cause-and-effect testing complete | Automation / EHS | Q3 2026 | G3 | Yes |
| E8 | First conforming external and intercompany production lots released | Production / QA | Q3 2026 | G3 | Yes |

### Workstream 6 — Quality, People & Operating System

**Lead:** QA Manager / HR Director / EHS Manager
**Objective:** Build the operating system, quality framework, and trained workforce required for repeatable production.

| # | Deliverable | Owner | Target | Gate | Machine Required? |
|---|-------------|-------|--------|------|-------------------|
| H1 | Factory organisation structure and headcount plan approved | HR | Q4 2025 | G1 | No |
| H2 | Quality management framework aligned to ISO 9001/14001/45001/50001 | QA / EHS | Q4 2025 | G1 | No |
| H3 | Standard operating procedure register defined | Operations / QA | Q1 2026 | G2 | No |
| H4 | Shift, maintenance, and escalation model approved | Operations | Q1 2026 | G2 | No |
| H5 | Operator and technician training curriculum complete | HR / Engineering | Q2 2026 | G2 | No |
| H6 | Commissioning crew trained on DCS, SIS, and QC release process | HR / Automation / QA | Q3 2026 | G3 | Yes |
| H7 | OEE, quality, and energy KPI governance active | Operations / Smart Factory | Q3 2026 | G3 | Yes |

---

## 4. Machine-Free Sprint — Immediate Deliverables

The following items can be completed now without construction, process equipment, or production activity. These form the current Gate 1 sprint.

| # | Deliverable | Document | Owner | Status |
|---|-------------|----------|-------|--------|
| 1 | Implementation plan | `docs/implementation-plan.md` | Programme Director | Done |
| 2 | Intragroup supply coordination | `docs/intragroup-supply-coordination.md` | Supply Chain Manager | Done |
| 3 | Penetration test scoping | `docs/pentest-scoping.md` | InfoSec / Smart Factory | Done |
| 4 | AI platform status | `docs/ai-platform-status.md` | AI Platform Team | Done |
| 5 | BIM zone boundaries | `docs/bim/zone-boundaries.md` | BIM / Smart Factory | Done — IFC linkage pending |
| 6 | BIM asset anchors | `docs/bim/asset-anchors.md` | BIM / Smart Factory | Done — IFC linkage pending |
| 7 | Sensor registry (design phase) | `docs/sensor-map.md` | Smart Factory | Done — commissioning expands |
| 8 | Gap closure report | `docs/gap-closure-report.md` | Programme Director | Done |
| 9 | MkDocs site navigation and styling | `mkdocs.yml`, `docs/stylesheets/extra.css` | Documentation owner | Done |

---

## 5. Critical Path & Dependencies

```text
Lease executed + regulatory path locked
  -> starter-bay layout approved
    -> utilities design completed
      -> long-lead equipment ordered
        -> site and utility infrastructure commissioned
          -> DCS/SIS + MES infrastructure installed
            -> production lines commissioned
              -> inbound feedstocks QC-cleared
                -> first intercompany and external deliveries
```

**Key dependency notes:**

- INDORAMA and PET-resin sourcing decisions must be closed before equipment FAT recipes are frozen.
- Control-room and historian infrastructure must be live before meaningful MES and AI validation can begin.
- Pentest execution can start in staging before machines arrive, but production go-live requires closure of any High/Critical findings.
- Outbound intragroup coordination must be agreed before sister factories rely on daily call-off volumes.

---

## 6. Gate Criteria Summary

### Gate 1 — Design Complete (Target: Q4 2025)

| Check | Criterion | Evidence |
|------|-----------|----------|
| G1-01 | All advanced planning documents populated | This repo |
| G1-02 | Intragroup supply coordination documented | `docs/intragroup-supply-coordination.md` |
| G1-03 | AI platform readiness and stub endpoints documented | `docs/ai-platform-status.md` |
| G1-04 | Pentest scoping approved | `docs/pentest-scoping.md` |
| G1-05 | Design-phase BIM and sensor documentation complete | `docs/bim/*`, `docs/sensor-map.md` |
| G1-06 | MkDocs site navigation exposes all supplementary docs | `mkdocs.yml` |

### Gate 2 — Infrastructure Ready (Target: Q2 2026)

| Check | Criterion | Evidence |
|------|-----------|----------|
| G2-01 | Starter bay and utilities ready for install | Facilities acceptance record |
| G2-02 | Control room, historian, VPN, and MES infrastructure available | Smart Factory commissioning report |
| G2-03 | Feedstock logistics, safety stock, and call-off workflows configured | ERP/MES configuration sign-off |
| G2-04 | Core permits and inspections completed | Regulatory document pack |

### Gate 3 — Production Ready (Target: Q3 2026)

| Check | Criterion | Evidence |
|------|-----------|----------|
| G3-01 | Blown film and PET lines commissioned | OAT / SAT records |
| G3-02 | DCS, SIS, and MES running with validated data completeness | Smart Factory validation report |
| G3-03 | First conforming production lots released | QA release records |
| G3-04 | Intercompany outbound flows activated | Delivery and GRN records |
| G3-05 | High/Critical pentest findings closed | Pentest close-out report |

---

## 7. Risk Register

| Risk ID | Risk | Likelihood | Impact | Mitigation |
|---------|------|------------|--------|------------|
| RK-01 | Delay in securing starter bay or site utilities | Medium | High | Maintain Agbara primary and Sagamu fallback options |
| RK-02 | Domestic polymer supply volatility | Medium | High | Dual-source imported backup and 30-day safety stock |
| RK-03 | PET resin import delays at port | Medium | Medium | Approved agents, Form M readiness, and early ordering |
| RK-04 | MES/historian deployment delayed by control-room readiness | Medium | High | Separate digital workstream with early server-room design freeze |
| RK-05 | Pentest findings delay production go-live | Low | High | Execute staging pentest early and remediate before SAT |
| RK-06 | Intragroup downstream demand ramps before plastics capacity stabilises | Medium | Medium | SLA-based phased call-offs and external B2B volume throttling |
| RK-07 | Utility instability affects line commissioning | Medium | High | Solar, BESS, diesel backup, and staged load testing |

---

*For supply-chain detail, refer to [supply-chain.md](./supply-chain.md).*
*For AI readiness, refer to [ai-platform-status.md](./ai-platform-status.md).*
*For gate tracking, refer to [gap-closure-report.md](./gap-closure-report.md).*
