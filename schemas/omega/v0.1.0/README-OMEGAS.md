# Omega Schemas

> **Version:** 0.1.0  
> **Protocol:** Internet of Sports Protocol (IoSP)

---

## Overview

Omega is the floor projection of an entity's risk trajectory within a domain.

**Omega is not an agent.** Omega does not act for the entity. Omega does not automate decisions. Omega does not replace medical or professional judgment.

**Omega is the entity's worst trajectory yet to avoid.**

Omega competes toward loss—simulating deterioration, injury, decline—and reports back. The gap between where the entity is and where Omega shows they could fall becomes the risk map.

---

## Alpha and Omega

| Aspect | Alpha | Omega |
|--------|-------|-------|
| Direction | Ceiling | Floor |
| Projects | Optimal state | Risk state |
| Objective | AWIN (what winning means) | ORISK (what risk means) |
| Entity goal | Move TOWARD | Move AWAY |
| Question answered | "Who could I become?" | "What could I lose?" |

Alpha and Omega are mirrors. Neither acts. Both project. Together they define the full range of possibility.

An entity optimizing only toward Alpha is blind to risk. An entity only watching Omega is paralyzed by fear. **Balance is required.**

---

## The Omega Loop

```
Entity (actual state)
    │
    ├──► performs, decides, acts
    │
    ▼
Reality (outcomes)
    │
    ├──► same inputs flow to Omega
    │
    ▼
Omega (risk projection)
    │
    ├──► computes risk trajectory
    ├──► "plays the loss"
    ├──► projects ORISK
    │
    ▼
Risk Analysis
    │
    ├──► what leads to decline?
    ├──► where is the danger?
    ├──► what must be avoided?
    │
    ▼
Feedback ──────────────────────────► Entity
    "here's what you could lose"
```

The entity remains the actor. Omega never acts in the world. Omega shows what's at risk. The entity decides how to protect.

---

## Schema Files

| File | Purpose |
|------|---------|
| `omega-iosp-schema.json` | Defines what an Omega IS—the risk projection structure |
| `omega-iosp-sprtx-bridge-schema.json` | Defines the entity-to-Omega relationship and feedback channel |
| `omega-iosp-feedback-schema.json` | Defines the structure of risk feedback Omega produces |

---

## Key Concepts

### Entity Types

Omega serves all entity types—same as Alpha:

| Type | Description |
|------|-------------|
| `individual` | Non-athlete persons—sportsfans, family, friends |
| `athlete` | Active competitive participant |
| `coach` | Training and development guidance |
| `representative` | Live-person business representative |
| `agent` | AI/system agent |
| `club` | Team or organization |
| `league` | Competition organizing body |
| `federation` | Governing body |
| `venue` | Physical location for competition/training |
| `brand` | Commercial entity in the sports space |
| `event` | Specific occurrence (game, match, meet) |
| `competition` | Series of events (tournament, season) |
| `legacy` | Historical or retired entity preservation |

Every entity has risk. Omega tracks it.

### ORISK Definition

ORISK (Omega-RISK) is entity-defined. It's not a universal metric—it's what risk means for THIS entity in THIS domain at THIS time.

**For athletes**, ORISK can include:
- Injury (acute, chronic, career-ending)
- Burnout / overtraining
- Performance decline
- Career termination
- Financial instability
- Reputation damage
- Health deterioration

**For individuals (non-athletes)**, ORISK can include:
- Abandonment of goals
- Health decline
- Disengagement from sport
- Loss of community connection

**For clubs/organizations**, ORISK can include:
- Relegation
- Financial insolvency
- Talent exodus
- Reputation collapse
- Regulatory sanctions

**For brands**, ORISK can include:
- Market position loss
- Partnership failures
- Audience disengagement
- Value misalignment exposure

ORISK can change. An athlete's risk profile shifts with age, injury history, career stage. Omega recalculates accordingly.

### Risk Dimensions

Omega tracks risk across the same dimensions as Alpha, but projects floor instead of ceiling:

**Performance Dimensions (primarily athletes/coaches):**
- Physical → injury trajectory, fatigue accumulation
- Technical → skill degradation, bad habit formation
- Tactical → strategic blind spots, exploitable patterns
- Mental → burnout, confidence erosion, focus loss
- Recovery → insufficient rest, chronic fatigue

**Universal Dimensions (all entities):**
- Contextual → environmental risks, situational dangers
- Relational → relationship deterioration, support loss
- Financial → resource depletion, unsustainable costs

**Organizational Dimensions (clubs, leagues, venues, events):**
- Operational → system failures, process breakdowns
- Developmental → pipeline depletion, talent loss

**Brand/Fan Dimensions:**
- Engagement → audience loss, disconnection
- Reputational → brand damage, trust erosion

### Risk Delta

The gap between current state and Omega's projected floor is the risk delta. Unlike Alpha's delta (which you want to close), Omega's delta is protective distance.

**Large Omega delta** = entity is far from their floor = safer position
**Small Omega delta** = entity is approaching risk thresholds = danger

Priority is determined by ORISK impact—which risk dimensions, if breached, would most damage the entity's defined boundaries.

### Instantiation: Automatic Creation, Optional Access

**Omega creation is AUTOMATIC.** When an entity is created, its omega is instantiated—alongside its alpha. This is not optional. Every entity has an omega from the moment they exist.

**Omega access is OPTIONAL.** An entity may choose to never engage with their omega. The omega exists, computes risk trajectories, maintains state—but the entity is not required to look at it or act on warnings.

**Abidance is NEVER required.** Even when accessing omega feedback, neither the entity nor any other authorized target is obligated to follow recommendations. Omega warns. Entity decides.

### Multi-Target Feedback

Omega can deliver risk feedback to multiple targets:

| Target | Role | Example |
|--------|------|---------|
| Entity | Primary | The athlete receiving injury risk warnings |
| Representative | Advisory | Business rep receiving career risk assessment |
| Agent | Autonomous | AI monitoring for threshold breaches |
| Coach | Advisory | Technical guidance on overtraining risk |
| Club | Monitoring | Organizational oversight of athlete health |
| Family | Support | Supporting awareness of burnout signs |

Risk information is sensitive. Access requires NEPH authorization with explicit scope for risk data.

### Cluster Contribution

Omega contributes to network intelligence about risk patterns:

```
Individual Omega
      │
      ├──► contributes anonymized risk patterns
      │
      ▼
Cluster (injury type, sport, age group, training load)
      │
      ├──► aggregates risk indicators
      │
      ▼
SPRTX Model
      │
      ├──► generates risk insights
      │
      ▼
All Omegas ◄─── receive cluster-informed risk intelligence
```

This is critical for early warning. If cluster data shows athletes with pattern X develop injury Y, all omegas tracking similar patterns receive elevated risk signals.

Contribution is opt-in with full anonymization by default.

### Computation Reference

The `computation_ref` in omega_schema is intentionally opaque—same as alpha. The schema defines THAT a computation model exists. The schema does NOT define HOW the computation works.

Risk computation is implementation-private.

### Feedback Types

Omega produces different types of risk recommendations:
- **Immediate** — Actions for the next 24-48 hours (stop training, see physician)
- **Short-term** — Changes over days to weeks (reduce load, increase recovery)
- **Structural** — Fundamental approach shifts (change training methodology)
- **Strategic** — Long-term risk management (career path adjustment)
- **Observational** — Risk indicators to monitor without immediate action

---

## Protocol Context

Omega schemas support dual protocol namespaces:

- **iosp://** — Protocol-portable, interoperable context
- **sprtx://** — SPRTX network-specific context

An Omega can operate in:
- IoSP only (maximum portability)
- SPRTX only (maximum feature access)
- Both simultaneously (common case)

---

## NEPH Integration

Omega creation is automatic, but all Omega ACCESS operations require NEPH authorization.

- Omega creation → **AUTOMATIC** (no NEPH required)
- Bridge establishment → requires NEPH
- Risk feedback access → requires NEPH
- ORISK modification → requires NEPH
- Adding feedback targets → requires NEPH

Omega data is extremely sensitive. It represents:
- Injury vulnerabilities
- Decline trajectories
- Exploitable weaknesses
- Risk thresholds

Unauthorized access to an entity's Omega is worse than competitive intelligence theft—it's a map to their vulnerabilities.

---

## Usage

### Omega Instantiation (Automatic)

1. Entity is created (per `agent_schema.json`)
2. Alpha AND Omega are automatically instantiated
3. Omega begins computing risk trajectories in background
4. Entity may or may not ever access it

### Accessing Omega (Optional)

1. Entity decides to engage with their omega
2. Request access through NEPH-authorized channel
3. Configure ORISK thresholds
4. Configure risk dimensions to track
5. Establish bridge for feedback delivery

### Establishing a Bridge

1. Entity and Omega exist (omega always exists if entity exists)
2. Request bridge through NEPH
3. Configure sync policy (how entity state flows to Omega)
4. Configure feedback channel (how Omega reports risk)
5. Configure feedback targets
6. Set permissions (data access and feedback scope)
7. Activate bridge

### Receiving Feedback

1. Bridge is active
2. Entity state syncs per policy
3. Omega computes risk trajectory
4. Feedback generated per frequency config (or threshold breach)
5. Feedback delivered to all configured targets
6. Targets receive risk analysis and recommendations
7. **Each target decides action independently—abidance is never required**

---

## Relationship to Other Schemas

```
agent-iosp-schema.json (entity exists)
        │
        ├────────────────────────────┬────────────────────────────┐
        ▼                            ▼                            ▼
agent-iosp-sprtx-bridge-schema   alpha-iosp-schema.json     omega-iosp-schema.json
(entity-to-entity relations)      (ceiling projection)        (floor projection)
                                        │                            │
                                        ▼                            ▼
                              alpha-iosp-sprtx-bridge      omega-iosp-sprtx-bridge
                                        │                            │
                                        ▼                            ▼
                            alpha-iosp-feedback-schema   omega-iosp-feedback-schema
                                  (growth roadmap)            (risk map)
                                        │                            │
                                        └──────────┬─────────────────┘
                                                   ▼
                                          gamma-iosp-schema.json
                                      (entity-specific calibration)
```

---

## Design Principles

1. **Separation of interface and implementation** — Schemas define structure and contracts, not algorithms
2. **Entity sovereignty** — The entity defines ORISK, controls the bridge, decides action
3. **Automatic existence, optional engagement** — Omega always exists; entity chooses whether to look
4. **No forced abidance** — Warnings inform, never command
5. **Privacy by design** — All access operations are NEPH-gated
6. **Protocol flexibility** — Support for both iosp:// and sprtx:// namespaces
7. **Network intelligence** — Individual omegas contribute to and benefit from cluster risk learning
8. **Extensibility** — Extension points for domain-specific additions

---

## What Omega Is NOT

- NOT an agent that acts for you
- NOT a medical diagnosis system
- NOT a prediction of what WILL happen
- NOT a replacement for professional judgment
- NOT accessible without authorization
- NOT mandatory to follow — ever
- NOT isolated — omega learns from and contributes to network risk patterns

Omega is a mirror that shows not who you are, but what you could lose.

---

## Alpha and Omega Together

Neither is complete without the other:

| Alone | Problem |
|-------|---------|
| Alpha only | Blind to risk, overreaches |
| Omega only | Paralyzed by fear, underperforms |

**Together:**
- Alpha shows the ceiling
- Omega shows the floor
- Gamma calibrates both to the entity
- Entity navigates the space between

The optimal path is not maximum alpha pursuit. It's maximum alpha pursuit **within acceptable omega bounds**.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 0.1.0 | 2026-01 | Initial release |
