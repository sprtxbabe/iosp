# Alpha Schemas

> **Version:** 0.1.0  
> **Protocol:** Internet of Sports Protocol (IoSP)

---

## Overview

Alpha is the optimal projection of an entity's potential within a domain.

**Alpha is not an agent.** Alpha does not act for the entity. Alpha does not automate decisions. Alpha does not replace human judgment.

**Alpha is the entity's best version yet to become.**

Alpha competes ahead of the entity—simulating, optimizing, projecting—and reports back. The gap between where the entity is and where Alpha shows they could be becomes the roadmap for growth.

---

## The Alpha Loop

```
Entity (actual state)
    │
    ├──► performs, decides, acts
    │
    ▼
Reality (outcomes)
    │
    ├──► same inputs flow to Alpha
    │
    ▼
Alpha (optimal projection)
    │
    ├──► computes optimal response
    ├──► "plays the game"
    ├──► projects AWIN
    │
    ▼
Delta Analysis
    │
    ├──► what did Alpha do differently?
    ├──► where is the gap?
    ├──► what matters most?
    │
    ▼
Feedback ──────────────────────────► Entity
    "here's who you could become"
```

The entity remains the actor. Alpha never acts in the world. Alpha shows what's possible. The entity decides whether to close the gap.

---

## Schema Files

| File | Purpose |
|------|---------|
| `alpha_schema.json` | Defines what an Alpha IS—the optimal projection structure |
| `alpha_bridge.json` | Defines the entity-to-Alpha relationship and feedback channel |
| `alpha_feedback.json` | Defines the structure of feedback Alpha produces |

---

## Key Concepts

### Entity Types

Alpha serves all entity types in the ecosystem:

| Type | Description |
|------|-------------|
| `individual` | Non-athlete persons—sportsfans, family, friends. The funnel to athlete. A person before becoming an athlete. |
| `athlete` | Active competitive participant |
| `coach` | Training and development guidance |
| `representative` | Live-person business representative (sports agent) |
| `agent` | AI/system agent |
| `club` | Team or organization |
| `league` | Competition organizing body |
| `federation` | Governing body |
| `venue` | Physical location for competition/training |
| `brand` | Commercial entity in the sports space |
| `event` | Specific occurrence (game, match, meet) |
| `competition` | Series of events (tournament, season) |
| `legacy` | Historical or retired entity preservation |

The `individual` type is significant. Every athlete was first a person. Family and friends of athletes are entities with their own growth trajectories within the ecosystem. The sportsfan is a funnel—today's fan may be tomorrow's athlete, or they may support an athlete's journey. Alpha serves them all.

The distinction between `representative` (live-person) and `agent` (AI/system) is critical for clarity in the protocol.

### AWIN Definition

AWIN (Alpha-WIN) is entity-defined. It's not a universal metric—it's what winning means for THIS entity in THIS domain at THIS time.

**For athletes**, AWIN can be:
- Championship pursuit
- Personal record achievement
- Career longevity
- Earnings optimization
- Skill acquisition
- Injury prevention
- A weighted combination of any of these

**For individuals (non-athletes)**, AWIN can be:
- Becoming an athlete (the funnel)
- Supporting an athlete's journey (family/friend)
- Engagement depth (sportsfan progression)
- Community involvement
- Health and fitness goals (pre-competitive)

**For clubs/organizations**, AWIN can be:
- Championship success
- Talent development pipeline
- Financial sustainability
- Community impact
- Brand value

**For brands**, AWIN can be:
- Market position
- Athlete partnership effectiveness
- Audience engagement
- Value alignment

AWIN can change. An athlete pivoting from peak performance to longevity can recalibrate their AWIN definition. A sportsfan becoming serious about competition shifts their AWIN entirely. Alpha recalculates accordingly.

### Delta

The gap between entity state and Alpha state is the delta. Delta exists across multiple dimensions:

**Performance Dimensions (primarily athletes/coaches):**
- Physical
- Technical
- Tactical
- Mental
- Recovery

**Universal Dimensions (all entities):**
- Contextual
- Relational
- Financial

**Organizational Dimensions (clubs, leagues, venues, events):**
- Operational
- Developmental (talent pipeline)

**Brand/Fan Dimensions:**
- Engagement
- Reputational

Not all deltas matter equally. Priority is determined by AWIN impact—which gaps, if closed, would most affect the entity's defined objectives.

### Instantiation: Automatic Creation, Optional Access

**Alpha creation is AUTOMATIC.** When an entity is created, its alpha is instantiated—like tokens. This is not optional. Every entity has an alpha from the moment they exist in the ecosystem.

**Alpha access is OPTIONAL.** An entity may choose to never engage with their alpha. The alpha exists, computes, maintains state—but the entity is not required to look at it, receive feedback, or act on recommendations.

**Abidance is NEVER required.** Even when accessing alpha feedback, neither the entity nor any other authorized target (representative, agent, coach, family) is obligated to follow recommendations. Alpha informs. Entity decides.

### Multi-Target Feedback

Alpha can deliver feedback to multiple targets:

| Target | Role | Example |
|--------|------|---------|
| Entity | Primary | The athlete themselves |
| Representative | Advisory | Live-person business rep receiving strategy feedback |
| Agent | Autonomous | AI agent receiving data for automated analysis |
| Coach | Advisory | Technical guidance receiver |
| Club | Monitoring | Organizational oversight |
| Family | Support | Supporting the entity's journey |

Targets can receive feedback:
- **Independently** — Each at different times/triggers
- **Simultaneously** — All together

When targets have different views on recommendations, conflict resolution follows entity priority by default—the entity's decision prevails.

### Cluster Contribution

Alpha doesn't exist in isolation. The network learns from all alphas:

```
Individual Alpha
      │
      ├──► contributes anonymized patterns
      │
      ▼
Cluster (domain, entity_type, geography, performance_tier)
      │
      ├──► aggregates patterns
      │
      ▼
SPRTX Model
      │
      ├──► generates insights
      │
      ▼
All Alphas ◄─── receive cluster-informed insights
```

This is the network intelligence layer. Individual alphas contribute anonymized data to clusters. Clusters inform the aggregate model. The model's insights flow back to improve all alphas.

Contribution is opt-in with full anonymization by default. Entities can:
- Enable/disable contribution
- Choose anonymization level
- Receive or decline cluster insights

### Computation Reference

The `computation_ref` in alpha_schema is intentionally opaque. The schema defines THAT a computation model exists and its interface contract. The schema does NOT define HOW the computation works.

The computation model is the intelligence layer. It is implementation-private.

### Feedback Types

Alpha produces different types of recommendations:
- **Immediate** — Actions for the next 24-48 hours
- **Short-term** — Changes over days to weeks
- **Structural** — Fundamental approach shifts over weeks to months
- **Strategic** — Long-term trajectory changes over months to years
- **Observational** — Things to monitor without immediate action

---

## Protocol Context

Alpha schemas support dual protocol namespaces:

- **iosp://** — Protocol-portable, interoperable context
- **sprtx://** — SPRTX network-specific context

An Alpha can operate in:
- IoSP only (maximum portability)
- SPRTX only (maximum feature access)
- Both simultaneously (common case)

The `protocol_context` field in each schema defines which namespaces are active and their configuration.

---

## NEPH Integration

Alpha creation is automatic, but all Alpha ACCESS operations require NEPH authorization.

- Alpha creation → **AUTOMATIC** (no NEPH required)
- Bridge establishment → requires NEPH
- Feedback access → requires NEPH
- AWIN modification → requires NEPH
- Adding feedback targets → requires NEPH

Alpha data is among the most sensitive in the ecosystem. It represents:
- Complete entity state analysis
- Optimal strategy projection
- Specific gaps and weaknesses
- The growth roadmap itself

Unauthorized access to an entity's Alpha is competitive intelligence theft.

---

## Usage

### Alpha Instantiation (Automatic)

1. Entity is created (per `agent_schema.json`)
2. Alpha is automatically instantiated
3. Alpha begins computing in background
4. Entity may or may not ever access it

### Accessing Alpha (Optional)

1. Entity decides to engage with their alpha
2. Request access through NEPH-authorized channel
3. Configure AWIN objectives
4. Configure state model dimensions
5. Establish bridge for feedback delivery

### Establishing a Bridge

1. Entity and Alpha exist (alpha always exists if entity exists)
2. Request bridge through NEPH
3. Configure sync policy (how entity state flows to Alpha)
4. Configure feedback channel (how Alpha reports back)
5. Configure feedback targets (entity only, or entity + representative/agent/coach/family)
6. Set permissions (data access and feedback scope)
7. Activate bridge

### Receiving Feedback

1. Bridge is active
2. Entity state syncs per policy
3. Alpha computes
4. Feedback generated per frequency config
5. Feedback delivered to all configured targets
6. Targets receive delta analysis and recommendations
7. **Each target decides action independently—abidance is never required**

---

## Relationship to Other Schemas

```
agent_schema.json (entity exists)
        │
        ├────────────────────────────┐
        ▼                            ▼
agent_schema_bridge.json      alpha_schema.json
(entity-to-entity relations)   (entity's optimal projection)
                                     │
                                     ▼
                              alpha_bridge.json
                           (entity-to-alpha channel)
                                     │
                                     ▼
                            alpha_feedback.json
                              (growth roadmap)
```

---

## Design Principles

1. **Separation of interface and implementation** — Schemas define structure and contracts, not algorithms
2. **Entity sovereignty** — The entity defines AWIN, controls the bridge, decides action
3. **Automatic existence, optional engagement** — Alpha always exists; entity chooses whether to look
4. **No forced abidance** — Recommendations inform, never command
5. **Privacy by design** — All access operations are NEPH-gated
6. **Protocol flexibility** — Support for both iosp:// and sprtx:// namespaces
7. **Network intelligence** — Individual alphas contribute to and benefit from cluster learning
8. **Extensibility** — Extension points for domain-specific additions

---

## What Alpha Is NOT

- NOT an agent that acts for you
- NOT a digital twin that mirrors current state
- NOT a prediction of what will happen
- NOT a replacement for coaching or judgment
- NOT accessible without authorization
- NOT mandatory to follow — ever
- NOT isolated — alpha learns from and contributes to the network

Alpha is a mirror that shows not who you are, but who you could become.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 0.1.0 | 2025-01 | Initial release |
