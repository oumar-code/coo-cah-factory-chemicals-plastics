<!-- docs/master-repo-ref.md — MkDocs-linked version of root MASTER_REPO_REF.md.
     Content mirrors MASTER_REPO_REF.md; cross-links use paths relative to docs/ for MkDocs compatibility. -->

# Master Repository Reference

## Coo-Kah-Doks — Single Source of Truth

| Attribute               | Detail                                                              |
|-------------------------|---------------------------------------------------------------------|
| **Master Repo**         | [oumar-code/Coo-Kah-Doks](https://github.com/oumar-code/Coo-Kah-Doks) |
| **Purpose**             | Single source of truth for strategy, architecture, blueprints, and group-wide standards |
| **Template Version**    | v1.0                                                               |
| **Factory Registration**| `orchestration/factory-status-registry.md` in Coo-Kah-Doks         |
| **Factory Blueprint**   | `factories/chemicals/plastics/` in Coo-Kah-Doks                    |
| **Template Format**     | `factories/_template/` in Coo-Kah-Doks                             |

---

## Factory Registration in Orchestration Registry

This factory is registered in the master repo at:

```
Coo-Kah-Doks / orchestration / factory-status-registry.md
```

| Field                  | Value                                             |
|------------------------|---------------------------------------------------|
| **Factory ID**         | CCH-PLS                                           |
| **Factory Name**       | Coo-Cah Plastics & Polymers Factory               |
| **Repository**         | `coo-cah-factory-chemicals-plastics`              |
| **Vertical**           | Chemicals / Plastics                              |
| **Tier**               | Tier 1 — Critical Infrastructure                 |
| **Phase**              | Phase 1                                           |
| **Status**             | PLANNED                                           |
| **Registered Version** | v1.0                                              |

---

## Blueprint Traceability

All foundational blueprints for this factory originate from the master repo at:

```
Coo-Kah-Doks / factories / chemicals / plastics /
```

Documents in this repository have been expanded from those blueprints with factory-specific
engineering specifications, supplier details, and operational data.

---

## Group-Wide Standards Compliance

This repository confirms compliance with all group-wide standards defined in
`Coo-Kah-Doks / docs /`:

| Standard Domain              | Master Repo Location                             | Local Reference                | Status     |
|------------------------------|--------------------------------------------------|--------------------------------|------------|
| ISO Requirements (9001, 14001, 45001, 50001) | `docs/iso-standards.md`        | [regulatory.md](regulatory.md) | Adopted    |
| Automation Phases (Phase 1–3) | `docs/automation-strategy.md`                  | [automation-roadmap.md](automation-roadmap.md) | Adopted    |
| Supply Chain Doctrine        | `docs/supply-chain-doctrine.md`                 | [supply-chain.md](supply-chain.md) | Adopted    |
| Energy Strategy              | `docs/energy-strategy.md`                       | [energy-profile.md](energy-profile.md) | Adopted    |
| AI Platform                  | `docs/ai-platform.md`                           | [digital-twin.md](digital-twin.md) | Adopted    |
| MES Integration Standards    | `docs/mes-integration-standards.md`             | [mes-integration.md](mes-integration.md) | Adopted    |
| Factory Document Template    | `factories/_template/`                          | —                              | v1.0 Used  |

---

## Versioning and Change Log

| Version | Date       | Author          | Change Summary                                    |
|---------|------------|-----------------|---------------------------------------------------|
| v1.0    | 2025-Q2    | Coo-Cah Engineering | Initial factory repository created from master repo blueprint |

---

## Referencing This Repo from the Master Repo

When linking to documents in this repo from Coo-Kah-Doks, use:

```
https://github.com/oumar-code/coo-cah-factory-chemicals-plastics
```

Factory-specific documents should be cross-referenced in the master repo's
`orchestration/factory-status-registry.md` under factory ID `CCH-PLS`.

---

*This file must be kept current whenever the master repo version is updated or the factory registration changes.*
