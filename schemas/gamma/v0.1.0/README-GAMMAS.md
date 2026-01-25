# Gamma Schema

> **Version:** 0.1.0  
> **Protocol:** Internet of Sports Protocol (IoSP)

---

## Overview

Gamma is the entity-specific calibration layer that adjusts Alpha and Omega projections.

**Gamma is not a projection.** Gamma does not compute ceiling or floor. Gamma computes **weights** that make Alpha and Omega accurate for THIS specific entity.

**Gamma is what makes Alpha and Omega personal.**

Without Gamma, Alpha and Omega are generic domain projections. With Gamma, they account for the entity's unique attributes—wingspan, injury history, age, training age, resources, genetics, context.

---

## Alpha, Omega, and Gamma

| Aspect | Alpha | Omega | Gamma |
|--------|-------|-------|-------|
| Projects | Ceiling | Floor | Neither |
| Output | AWIN trajectory | ORISK trajectory | Calibration weights |
| Question | "Who could I become?" | "What could I lose?" | "How do MY specifics affect both?" |
| Updates | Per sync/computation | Per sync/computation | Per attribute change |

Gamma feeds into both Alpha and Omega:

```
Entity Attributes
      │
      ▼
┌─────────────┐
│    GAMMA    │
│ (calibrate) │
└─────────────┘
      │
      ├──────────────────┬──────────────────┐
      ▼                  ▼                  ▼
┌──────────┐      ┌──────────┐      ┌──────────┐
│  ALPHA   │      │  OMEGA   │      │  Shared  │
│ weights  │      │ weights  │      │ weights  │
└──────────┘      └──────────┘      └──────────┘
```

---

## Schema File

| File | Purpose |
|------|---------|
| `gamma-iosp-schema.json` | Defines entity-specific calibration attributes and weight generation |

Gamma has no bridge or feedback schema. It's a calibration layer, not a projection system. Alpha and Omega bridges handle feedback delivery.

---

## Key Concepts

### Entity Attributes

Gamma captures attributes that make an entity unique:

**Physical Attributes:**
- Body composition (height, weight, wingspan, limb ratios)
- Physiological markers (VO2 max, lactate threshold, heart rate zones)
- Genetic factors (if available/consented)
- Age, biological age, training age

**Historical Attributes:**
- Injury history (type, severity, recurrence)
- Performance history (peaks, valleys, trajectories)
- Training history (volume, intensity, adaptation patterns)
- Recovery patterns (how entity responds to load)

**Contextual Attributes:**
- Resource availability (time, money, equipment, coaching)
- Environmental factors (climate, altitude, facilities)
- Support system (family, team, medical access)
- Life stage (student, professional, transitioning, retired)

**Psychological Attributes:**
- Stress response patterns
- Motivation factors
- Risk tolerance
- Learning style

### Weight Generation

Gamma takes attributes and generates weights that adjust projections:

**Alpha Weights:**
- Ceiling adjustments (what's realistically achievable for THIS entity)
- Objective weights (which AWIN objectives are more/less attainable)
- Dimension weights (which dimensions have more/less potential)
- Timeline weights (how fast can THIS entity progress)

**Omega Weights:**
- Floor adjustments (which risks are elevated for THIS entity)
- Threshold weights (which ORISK thresholds are closer/further)
- Dimension weights (which dimensions carry more/less risk)
- Recovery weights (how quickly can THIS entity bounce back)

**Shared Weights:**
- Some weights apply to both projections (e.g., age affects both ceiling and floor)

### Calibration Events

Gamma recalibrates when attributes change:

| Event | Example | Impact |
|-------|---------|--------|
| Injury | ACL tear | Omega weights shift, Alpha ceiling adjusts |
| Age milestone | Turning 30 | Both projections recalibrate |
| Resource change | New coaching staff | Alpha weights may improve |
| Performance data | New personal record | Ceiling recalibrated upward |
| Medical assessment | Bone density scan | Risk weights updated |
| Context change | Moving to altitude | Environmental weights adjust |

### Attribute Confidence

Not all attributes are equally reliable:

| Confidence | Source | Example |
|------------|--------|---------|
| High | Direct measurement | Height, weight, VO2 max test |
| Medium | Derived/calculated | Training age from history |
| Low | Self-reported | Sleep quality, stress level |
| Inferred | Pattern analysis | Recovery rate from performance data |

Gamma tracks confidence for each attribute. Low-confidence attributes generate wider weight ranges (more uncertainty in projections).

---

## Entity Type Variations

Different entity types have different attribute sets:

**Athletes:**
- Full physical, historical, psychological attributes
- Most granular calibration

**Individuals (pre-athlete funnel):**
- Limited historical data
- Baseline physical attributes
- Potential indicators

**Clubs:**
- Organizational attributes (resources, facilities, staff)
- Roster composition
- Historical performance

**Brands:**
- Market attributes
- Partnership history
- Audience demographics

Gamma schema uses flexible attribute structures to accommodate all entity types.

---

## NEPH Integration

Gamma contains highly sensitive personal data:

- Physical measurements
- Medical history
- Genetic information (if present)
- Psychological assessments

All Gamma operations require NEPH authorization:

- Gamma creation → requires NEPH
- Attribute access → requires NEPH
- Weight generation → requires NEPH
- Calibration updates → requires NEPH

Gamma data is never shared with clusters in identifiable form. Only anonymized calibration patterns contribute to network learning.

---

## Relationship to Other Schemas

```
agent-iosp-schema.json (entity exists)
        │
        ▼
gamma-iosp-schema.json (entity calibration)
        │
        ├──────────────────┬──────────────────┐
        │                  │                  │
        ▼                  ▼                  ▼
  Alpha weights      Omega weights     Shared weights
        │                  │                  │
        ▼                  ▼                  ▼
alpha-iosp-schema    omega-iosp-schema
  (calibrated)         (calibrated)
        │                  │
        ▼                  ▼
    Feedback           Feedback
   (accurate)         (accurate)
```

Without Gamma: Generic projections
With Gamma: Personalized projections

---

## Design Principles

1. **Entity sovereignty** — Entity controls what attributes are captured
2. **Consent-based** — Sensitive attributes require explicit consent
3. **Confidence tracking** — All attributes have confidence levels
4. **Flexible structure** — Different entity types have different attribute sets
5. **Privacy by design** — All operations are NEPH-gated
6. **No direct feedback** — Gamma calibrates, Alpha and Omega provide feedback

---

## What Gamma Is NOT

- NOT a projection (that's Alpha and Omega)
- NOT a feedback system (no gamma_feedback schema)
- NOT optional for accurate projections
- NOT shared across entities
- NOT accessible without authorization

Gamma is the personalization layer that makes Alpha and Omega accurate for the individual.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 0.1.0 | 2025-01 | Initial release |
