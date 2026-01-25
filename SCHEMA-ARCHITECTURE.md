# IoSP Schema Architecture

> **Version:** 0.1.0  
> **Protocol:** Internet of Sports Protocol (IoSP)

---

## Complete System Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                   ENTITY LAYER                                      │
│                                                                                     │
│    ┌─────────────────────────────┐         ┌─────────────────────────────────┐      │
│    │   agent-iosp-schema.json    │────────▶│ agent-iosp-sprtx-bridge-schema  │      │
│    │      (Entity Definition)    │         │      (Entity Relationships)     │      │
│    └──────────────┬──────────────┘         └─────────────────────────────────┘      │
│                   │                                                                 │
│                   │  Entity created = Alpha + Omega + Gamma AUTO-INSTANTIATED       │
│                   │                                                                 │
└───────────────────┼─────────────────────────────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                               CALIBRATION LAYER                                     │
│                                                                                     │
│                      ┌─────────────────────────────┐                                │
│                      │   gamma-iosp-schema.json    │                                │
│                      │   (Entity Calibration)      │                                │
│                      └──────────────┬──────────────┘                                │
│                                     │                                               │
│    ┌────────────────────────────────┼────────────────────────────────┐              │
│    │                                │                                │              │
│    ▼                                ▼                                ▼              │
│  ┌─────────────┐            ┌─────────────┐              ┌─────────────┐            │
│  │   Physical  │            │ Historical  │              │ Contextual  │            │
│  │  Attributes │            │ Attributes  │              │ Attributes  │            │
│  └─────────────┘            └─────────────┘              └─────────────┘            │
│         │                          │                            │                   │
│         └──────────────────────────┴────────────────────────────┘                   │
│                                    │                                                │
│                                    ▼                                                │
│                    ┌──────────────────────────────┐                                 │
│                    │        WEIGHT MODEL          │                                 │
│                    │  ┌─────────┐   ┌─────────┐   │                                 │
│                    │  │ Alpha   │   │ Omega   │   │                                 │
│                    │  │ Weights │   │ Weights │   │                                 │
│                    │  └────┬────┘   └────┬────┘   │                                 │
│                    └───────┼─────────────┼────────┘                                 │
│                            │             │                                          │
└────────────────────────────┼─────────────┼──────────────────────────────────────────┘
                             │             │
           ┌─────────────────┘             └─────────────────┐
           │                                                 │
           ▼                                                 ▼
┌──────────────────────────────────┐    ┌──────────────────────────────────┐
│        ALPHA (Ceiling)           │    │        OMEGA (Floor)             │
│                                  │    │                                  │
│  ┌────────────────────────────┐  │    │  ┌────────────────────────────┐  │
│  │  alpha-iosp-schema.json    │  │    │  │  omega-iosp-schema.json    │  │
│  │   (Optimal Projection)     │  │    │  │    (Risk Projection)       │  │
│  │                            │  │    │  │                            │  │
│  │   ┌──────────────────┐     │  │    │  │   ┌──────────────────┐     │  │
│  │   │      AWIN        │     │  │    │  │   │     ORISK        │     │  │
│  │   │ (What WIN means) │     │  │    │  │   │ (What RISK means)│     │  │
│  │   └──────────────────┘     │  │    │  │   └──────────────────┘     │  │
│  └─────────────┬──────────────┘  │    │  └─────────────┬──────────────┘  │
│                │                 │    │                │                 │
│                ▼                 │    │                ▼                 │
│  ┌────────────────────────────┐  │    │  ┌────────────────────────────┐  │
│  │ alpha-iosp-sprtx-bridge    │  │    │  │ omega-iosp-sprtx-bridge    │  │
│  │       -schema.json         │  │    │  │       -schema.json         │  │
│  │  (Entity-Alpha Channel)    │  │    │  │  (Entity-Omega Channel)    │  │
│  └─────────────┬──────────────┘  │    │  └─────────────┬──────────────┘  │
│                │                 │    │                │                 │
│                ▼                 │    │                ▼                 │
│  ┌────────────────────────────┐  │    │  ┌────────────────────────────┐  │
│  │ alpha-iosp-feedback-schema │  │    │  │ omega-iosp-feedback-schema │  │
│  │          .json             │  │    │  │          .json             │  │
│  │    (Growth Roadmap)        │  │    │  │      (Risk Map)            │  │
│  └─────────────┬──────────────┘  │    │  └─────────────┬──────────────┘  │
│                │                 │    │                │                 │
└────────────────┼─────────────────┘    └────────────────┼─────────────────┘
                 │                                       │
                 │    ┌─────────────────────────┐        │
                 └───▶│        ENTITY           │◀────-──┘
                      │   (Receives BOTH)       │
                      │                         │
                      │   Growth + Risk = Full  │
                      │       Picture           │
                      └───────────┬─────────────┘
                                  │
                                  ▼
                      ┌─────────────────────────┐
                      │    ENTITY DECIDES       │
                      │                         │
                      │  Abidance NEVER forced  │
                      └─────────────────────────┘


┌─────────────────────────────────────────────────────────────────────────────────────┐
│                               SECURITY LAYER                                        │
│                                                                                     │
│                         ┌─────────────────────────────┐                             │
│                         │           NEPH              │                             │
│                         │   (Private Specification)   │                             │
│                         └──────────────┬──────────────┘                             │
│                                        │                                            │
│                                        ▼                                            │
│                         ┌─────────────────────────────┐                             │
│                         │    Guards ALL Access:       │                             │
│                         │    • Gamma operations       │                             │
│                         │    • Alpha bridge/feedback  │                             │
│                         │    • Omega bridge/feedback  │                             │
│                         │    • AWIN/ORISK changes     │                             │
│                         │    • Adding targets         │                             │
│                         └─────────────────────────────┘                             │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘


┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              NETWORK INTELLIGENCE                                   │
│                                                                                     │
│     Alpha ──────┐                                                                   │
│                 │      ┌────────────────┐      ┌────────────────┐                   │
│     Omega ──────┼─────▶│    CLUSTERS    │─────▶│  SPRTX MODEL   │──── insights ──┐  │
│                 │      │  (anonymized)  │      │  (aggregate)   │                │  │
│     Gamma ──────┘      └────────────────┘      └────────────────┘                │  │
│                                                                                  │  │
│     ◀────────────────────────────────────────────────────────────────────────────┘  │
│                              (improves all projections)                             │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘


┌─────────────────────────────────────────────────────────────────────────────────────┐
│                            PROTOCOL ADDRESSING                                      │
│                                                                                     │
│     ┌───────────────────────┐              ┌───────────────────────┐                │
│     │       iosp://         │              │       sprtx://        │                │
│     │   (Protocol Layer)    │              │   (Network Layer)     │                │
│     │                       │              │                       │                │
│     │   • Portable          │              │   • Network-specific  │                │
│     │   • Interoperable     │              │   • Full features     │                │
│     │   • Standard          │              │   • NEPH (sprtx only) │                │
│     └───────────────────────┘              └───────────────────────┘                │
│                                                                                     │
│     Both address: entities, alpha, omega, gamma, bridges, feedback                  │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## Schema Inventory

### Entity Layer (2 schemas)
| Schema | File | Purpose |
|--------|------|---------|
| Entity | `schemas/agent/v0.1.0/agent-iosp-schema.json` | Defines what an entity IS |
| Entity Bridge | `schemas/agent/v0.1.0/agent-iosp-sprtx-bridge-schema.json` | Entity-to-entity relationships |

### Calibration Layer (1 schema)
| Schema | File | Purpose |
|--------|------|---------|
| Gamma | `schemas/gamma/v0.1.0/gamma-iosp-schema.json` | Entity-specific calibration weights |

### Projection Layer - Alpha (3 schemas)
| Schema | File | Purpose |
|--------|------|---------|
| Alpha | `schemas/alpha/v0.1.0/alpha-iosp-schema.json` | Ceiling (optimal) projection |
| Alpha Bridge | `schemas/alpha/v0.1.0/alpha-iosp-sprtx-bridge-schema.json` | Entity-to-alpha channel |
| Alpha Feedback | `schemas/alpha/v0.1.0/alpha-iosp-feedback-schema.json` | Growth roadmap delivery |

### Projection Layer - Omega (3 schemas)
| Schema | File | Purpose |
|--------|------|---------|
| Omega | `schemas/omega/v0.1.0/omega-iosp-schema.json` | Floor (risk) projection |
| Omega Bridge | `schemas/omega/v0.1.0/omega-iosp-sprtx-bridge-schema.json` | Entity-to-omega channel |
| Omega Feedback | `schemas/omega/v0.1.0/omega-iosp-feedback-schema.json` | Risk map delivery |

### Security Layer (1 specification)
| Schema | File | Purpose |
|--------|------|---------|
| NEPH | *Private* | Access authorization (not public) |

---

## Total Schema Count

| Layer | Count |
|-------|-------|
| Entity | 2 |
| Calibration | 1 |
| Alpha | 3 |
| Omega | 3 |
| **Total Public** | **9** |
| Security (Private) | 1 |
| **Total** | **10** |

---

## Folder Structure

```
iosp/
├── README.md
├── README-ALPHAS.md
├── README-OMEGAS.md
├── README-GAMMAS.md
├── README-AGENTS.md
├── SCHEMA-ARCHITECTURE.md
│
└── schemas/
    ├── agent/
    │   └── v0.1.0/
    │       ├── agent-iosp-schema.json
    │       └── agent-iosp-sprtx-bridge-schema.json
    │
    ├── alpha/
    │   └── v0.1.0/
    │       ├── alpha-iosp-schema.json
    │       ├── alpha-iosp-sprtx-bridge-schema.json
    │       └── alpha-iosp-feedback-schema.json
    │
    ├── omega/
    │   └── v0.1.0/
    │       ├── omega-iosp-schema.json
    │       ├── omega-iosp-sprtx-bridge-schema.json
    │       └── omega-iosp-feedback-schema.json
    │
    └── gamma/
        └── v0.1.0/
            └── gamma-iosp-schema.json
```

---

## Key Relationships

### Instantiation Flow
```
Entity Created
      │
      └──▶ AUTOMATIC: Alpha + Omega + Gamma instantiated
                │
                └──▶ Access is OPTIONAL (requires NEPH)
```

### Data Flow
```
Entity State ──▶ Gamma ──▶ Weights ──┬──▶ Alpha (calibrated ceiling)
                                     │
                                     └──▶ Omega (calibrated floor)
```

### Feedback Flow
```
Alpha ──▶ Alpha Bridge ──▶ Alpha Feedback ──┐
                                            ├──▶ Entity (decides action)
Omega ──▶ Omega Bridge ──▶ Omega Feedback ──┘
```

### Network Intelligence Flow
```
Alpha ──┐
        │
Omega ──┼──▶ Clusters (anonymized) ──▶ Model ──▶ Insights ──▶ All Projections
        │
Gamma ──┘
```

---

## Entity Types (13)

All schemas support:

| Type | Description |
|------|-------------|
| `individual` | Non-athlete persons (sportsfan, family, friend) — the funnel |
| `athlete` | Active competitive participant |
| `coach` | Training and development guidance |
| `representative` | Live-person business rep |
| `agent` | AI/system agent |
| `club` | Team or organization |
| `league` | Competition organizing body |
| `federation` | Governing body |
| `venue` | Physical location |
| `brand` | Commercial entity |
| `event` | Specific occurrence |
| `competition` | Series of events |
| `legacy` | Historical preservation |

---

## Core Metrics

| Metric | Schema | Purpose |
|--------|--------|---------|
| **AWIN** | alpha-iosp-schema.json | What winning means for this entity |
| **ORISK** | omega-iosp-schema.json | What risk means for this entity |

---

## Core Principles

1. **Entity sovereignty** — Entity defines AWIN/ORISK, controls access, decides action
2. **Automatic instantiation** — Alpha, Omega, Gamma created with entity
3. **Optional access** — Entity may never engage with projections
4. **No forced abidance** — Feedback informs, never commands
5. **Calibrated accuracy** — Gamma makes projections personal
6. **Dual projection** — Alpha (ceiling) + Omega (floor) = full picture
7. **NEPH-gated** — All access operations require authorization
8. **Network intelligence** — Anonymized patterns improve all projections
9. **Dual protocol** — iosp:// for portability, sprtx:// for features

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 0.1.0 | 2026-01 | IoSP Initial release — Entity, Alpha, Omega, Gamma (9 public schemas) |
