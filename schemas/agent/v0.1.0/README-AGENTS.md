# Agent Schemas

> **Version:** 0.1.0  
> **Protocol:** Internet of Sports Protocol (IoSP)

---

## Overview

An **agent** in IoSP is an AI/system entity that can act autonomously within the ecosystem.

**Agent is not Alpha.** Alpha projects optimal state but never acts. Agent executes, operates, and makes decisions within authorized scope.

**Agent is not representative.** Representative is a live-person business rep (sports agent). Agent is software.

---

## Agent vs Alpha vs Representative

| Concept | What It Is | Acts? | Human? |
|---------|------------|-------|--------|
| **Alpha** | Optimal projection of entity potential | Never | No |
| **Agent** | AI/system that operates autonomously | Yes | No |
| **Representative** | Live-person business rep | Yes | Yes |

This distinction is fundamental to IoSP architecture:
- Alpha informs
- Agent executes
- Representative advises

---

## Agent as Entity Type

Agent is one of the 13 entity types in IoSP:

```
individual, athlete, coach, representative, agent,
club, league, federation, venue, brand, event, competition, legacy
```

As an entity type, an agent:
- Has its own identity (`iosp://agent/...` or `sprtx://agent/...`)
- Can have relationships via `agent_schema_bridge`
- Has its own Alpha (automatic, like all entities)
- Can define its own AWIN objectives

---

## Agent as Feedback Target

Agents can receive Alpha feedback alongside other targets:

| Target | Role | Description |
|--------|------|-------------|
| Entity | Primary | The entity itself |
| Representative | Advisory | Live-person business rep |
| **Agent** | Autonomous | AI receiving data for automated action |
| Coach | Advisory | Technical guidance |
| Club | Monitoring | Organizational oversight |
| Family | Support | Supporting entity's journey |

When an agent is a feedback target:
- It receives Alpha feedback per bridge configuration
- It may act on recommendations autonomously (within scope)
- It is NOT required to abide by recommendations
- Its actions are logged and auditable

---

## Agent Roles

Agents operate in defined roles:

### Autonomous
Agent operates independently within authorized scope. Receives feedback, makes decisions, executes actions without human approval for each action.

**Use cases:**
- Automated training schedule adjustments
- Real-time performance optimization
- Data collection and analysis
- Routine operational tasks

### Advisory
Agent provides recommendations but does not execute. Human (entity, representative, coach) makes final decision.

**Use cases:**
- Strategy suggestions
- Risk analysis
- Opportunity identification
- Decision support

### Monitoring
Agent observes and reports but does not intervene. Alerts humans when thresholds are crossed.

**Use cases:**
- Health monitoring
- Performance tracking
- Compliance watching
- Anomaly detection

### Delegated
Agent acts on behalf of another entity with explicit authorization. Actions are attributed to the delegating entity.

**Use cases:**
- Scheduled communications
- Routine approvals
- Data submissions
- Administrative tasks

---

## Agent-Alpha Relationship

Every agent entity has an Alpha (automatic instantiation). This creates a recursive but coherent structure:

```
Agent (entity)
    │
    ├──► has Alpha (automatic)
    │         │
    │         └──► Alpha projects agent's optimal performance
    │
    └──► receives feedback from OTHER entities' Alphas
              │
              └──► as configured feedback target
```

An agent's own Alpha tracks:
- Operational efficiency
- Decision quality
- Response accuracy
- Resource utilization

An agent receiving another entity's Alpha feedback:
- Processes recommendations
- May execute actions
- Reports outcomes
- Contributes to feedback lineage

---

## Agent Permissions

Agent operations require explicit authorization:

### Scope Definition
What the agent can do:
- Read access to specific data types
- Write access to specific systems
- Action types permitted
- Decision boundaries

### NEPH Requirements
- Agent creation requires NEPH
- Agent authorization for entity data requires NEPH
- Agent actions on sensitive operations require NEPH
- Cross-entity agent operations require dual NEPH

### Audit Trail
All agent actions are logged:
- Action type
- Timestamp
- Authorization reference
- Input data
- Output/result
- Affected entities

---

## Agent in Feedback Targets Schema

From `alpha_bridge.json`:

```json
{
  "feedback_targets": {
    "targets": [
      {
        "target_id": "sprtx://agent/performance-optimizer-001",
        "target_type": "agent",
        "target_role": "autonomous",
        "feedback_scope": ["physical", "recovery", "tactical"],
        "authorization_neph": "neph://auth/...",
        "abidance_required": false
      }
    ]
  }
}
```

Key fields:
- `target_type: "agent"` — identifies as AI agent
- `target_role` — defines operational mode
- `feedback_scope` — limits what dimensions agent receives
- `abidance_required: false` — agent is never forced to follow recommendations

---

## Agent Constraints

### What Agents Cannot Do
- Override entity sovereignty
- Act without authorization
- Access data outside scope
- Bypass NEPH requirements
- Force abidance on any target
- Operate outside defined role

### What Agents Must Do
- Log all actions
- Respect scope boundaries
- Honor NEPH authorization
- Report failures
- Maintain audit trail

---

## Agent Types by Function

| Function | Description | Typical Role |
|----------|-------------|--------------|
| Performance Agent | Optimizes training/competition | Autonomous |
| Analytics Agent | Processes and reports data | Monitoring |
| Communication Agent | Handles routine messaging | Delegated |
| Compliance Agent | Monitors regulatory requirements | Monitoring |
| Strategy Agent | Provides decision support | Advisory |
| Operations Agent | Manages logistics | Autonomous |
| Recovery Agent | Manages rest/rehabilitation | Advisory |

---

## Integration Points

### With Alpha System
- Receives feedback as target
- Processes recommendations
- Reports action outcomes
- Contributes to feedback lineage

### With Entity System
- Is an entity type
- Has relationships via bridges
- Operates on behalf of entities
- Respects entity sovereignty

### With NEPH System
- Requires NEPH for authorization
- Actions validated against NEPH scope
- Cross-entity operations require appropriate NEPHs

### With Cluster System
- Agent's own Alpha contributes to clusters
- Agent may process cluster insights
- Anonymization rules apply

---

## Design Principles

1. **Sovereignty preserved** — Agents never override entity decisions
2. **Scope-bound** — Agents operate only within explicit authorization
3. **Auditable** — All agent actions are logged
4. **NEPH-gated** — Sensitive operations require authorization
5. **Role-defined** — Agent behavior matches declared role
6. **Abidance optional** — Even agents are not forced to follow recommendations

---

## What Agent Is NOT

- NOT Alpha (agent acts, alpha projects)
- NOT a human (that's representative)
- NOT unlimited in scope
- NOT exempt from NEPH
- NOT above entity sovereignty
- NOT unaccountable

Agent is software that operates within defined boundaries to serve entity objectives.

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 0.1.0 | 2026-01 | Initial release |
