# Gate 3 Preparation Sprint — Two-Week Readiness Tracker

**Factory:** Coo-Cah Plastics & Polymers Factory (CCH-PLS)  
**Document:** Integrated Readiness Sprint Tracker v1.0  
**Status:** ACTIVE — Focused on unblocked Gate 3 preparation work  
**Sprint Start Basis:** 2026-06-03  

---

## 1. Sprint Objective

This tracker consolidates the next two weeks of Gate 3 preparation work into a single coordinated
readiness sprint.

The sprint explicitly avoids trying to close items that require commissioned lines or live 30-day
data windows. Instead, it prepares the evidence, owners, prerequisites, and cross-document
traceability needed to accelerate later closure of GAP-010 and GAP-011.

---

## 2. Scope Decision

| GAP | Topic | Current Status | Machine Dependency | Sprint Treatment |
| --- | --- | --- | --- | --- |
| GAP-006 | BIM zone boundaries | 🔶 Partial | Partial | Tighten traceability and evidence path now |
| GAP-007 | BIM asset anchors | 🔶 Partial | Partial | Tighten traceability and evidence path now |
| GAP-008 | Sensor registry | 🔶 Partial | Partial | Freeze mapping and acceptance checklist now |
| GAP-009 | Pentest execution | 🔴 Open | No | Launch immediately |
| GAP-010 | AI production go-live | ⛔ Blocked | Yes | Prepare dependencies only |
| GAP-011 | MES / historian commissioning dataset | ⛔ Blocked | Yes | Prepare acceptance path only |
| GAP-012 | Simulation readiness | 🔶 Partial | Partial | Freeze sign-off baseline now |

---

## 3. Two-Week Backlog

### 3.1 Week 1 Deliverables

| ID | Deliverable | Owner | Target Output | Acceptance Evidence |
| --- | --- | --- | --- | --- |
| W1-01 | Integrated readiness backlog finalised for GAP-006 to GAP-012 | Programme Director | Single tracker published | This document |
| W1-02 | Pentest kickoff path defined | InfoSec Lead | Vendor shortlist, scope confirmation, staging prerequisites, execution window | [pentest-kickoff-pack.md](./pentest-kickoff-pack.md) |
| W1-03 | Simulation sign-off workshop pack frozen | Process Engineer / Smart Factory Lead | Baseline inputs, sign-off agenda, deferred items register | [simulation-signoff-baseline.md](./simulation-signoff-baseline.md) |
| W1-04 | BIM and sensor consistency review completed | BIM Lead / Instrumentation Engineer | Asset-to-zone-to-tag traceability review | [bim-sensor-traceability-matrix.md](./bim-sensor-traceability-matrix.md) |
| W1-05 | Executive dependency map issued | Programme Director | Clear split of closeable now vs commissioning-blocked work | Section 4 |

### 3.2 Week 2 Deliverables

| ID | Deliverable | Owner | Target Output | Acceptance Evidence |
| --- | --- | --- | --- | --- |
| W2-01 | Staging pentest kickoff package approved | InfoSec Lead | Approved execution package ready for vendor issue | [pentest-kickoff-pack.md](./pentest-kickoff-pack.md) |
| W2-02 | First-use-case simulation baseline frozen | Process Engineer / Smart Factory Lead / Operations Lead | Signed baseline pack for SC-001 to SC-003; SC-004 deferred pending vibration window | [simulation-signoff-baseline.md](./simulation-signoff-baseline.md) |
| W2-03 | Historian and MES commissioning data acceptance checklist issued | Smart Factory Lead / MES Lead | Commissioning-ready validation checklist | [commissioning-data-acceptance-checklist.md](./commissioning-data-acceptance-checklist.md) |
| W2-04 | Gate 3 evidence dashboard published | Programme Director / Workstream Owners | Owner-by-owner evidence tracker with dates | [gate3-evidence-dashboard.md](./gate3-evidence-dashboard.md) |
| W2-05 | Next 30–60 day leadership sequence locked | Programme Director | Sequenced post-sprint plan approved | Section 5 |

---

## 4. Executive Dependency Map

### 4.1 Closeable in This Sprint

- GAP-009 kickoff readiness
- BIM and sensor traceability cleanup supporting GAP-006, GAP-007, and GAP-008
- Simulation sign-off baseline supporting GAP-012
- Acceptance and evidence templates supporting later closure of GAP-010 and GAP-011

### 4.2 Not Closeable in This Sprint

- **GAP-010 — AI production go-live**
  - blocked by edge node commissioning, historian feeds, utilities telemetry, and model validation
- **GAP-011 — full MES / historian commissioning dataset**
  - blocked by live tags, validated 30-day window, and commissioned lines

### 4.3 Critical Path

`GAP-011 commissioning dataset -> GAP-010 AI production go-live + GAP-012 trial simulation runs`

### 4.4 Parallel Path

`GAP-009 staging pentest kickoff -> staging pentest execution -> remediation planning`

---

## 5. Locked Post-Sprint Sequence (30–60 Days)

1. Execute the staging pentest and baseline remediation.
2. Commission server room, MES room, historian, VPN, and OT network foundations.
3. Start live tag ingestion and validate the first continuous 30-day historian window.
4. Replace planning BIM placeholders with commissioning or as-built values as IFC and delivery data arrive.
5. Run first simulation trial runs once dataset freeze conditions are met.
6. Promote AI services from stub-ready to live only after validated MES and historian evidence exists.

---

## 6. Sprint Governance

| Cadence | Participants | Purpose |
| --- | --- | --- |
| Twice-weekly sprint review | Programme Director, BIM Lead, Smart Factory Lead, MES Lead, InfoSec Lead, Process Engineer | Track W1/W2 deliverables and unblock dependencies |
| End-of-week owner check | Deliverable owner + approver | Confirm evidence pack readiness |
| Leadership lock review | Programme Director, Factory leadership, Smart Factory Lead | Approve post-sprint 30–60 day sequence |

---

## 7. Definition of Sprint Success

The sprint is successful when all of the following are true:

- A single backlog exists for GAP-006 to GAP-012.
- The pentest path is ready to issue to a selected vendor.
- Simulation inputs are frozen for first-use-case planning even where live data is deferred.
- BIM, sensor, and simulation traceability mismatches are removed or explicitly logged.
- Commissioning teams have an agreed acceptance checklist for historian and MES validation.
- Evidence owners, dates, and expected proof are visible in one dashboard.

---

*This sprint tracker is the coordination artifact for the next two weeks and should be reviewed with
the gap closure report and the underlying Gate 3 artifacts.*
