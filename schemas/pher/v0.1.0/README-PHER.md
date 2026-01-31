# PHER — Permissible Human Entry Request

**Perimeter defense layer for the Internet of Sports Protocol.**

[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](https://github.com/sprtxbabe/iosp)
[![License](https://img.shields.io/badge/license-CC%20BY--SA%204.0-green.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

---

## Overview

PHER is the perimeter gate of IoSP. One gate, two doors.

The **digital door** (`pher_check`) classifies, analyzes, and gates all inbound API requests before they reach NEPH. The **physical door** (`pher_scan`) detects, classifies, and enforces policy against unauthorized hardware and transceivers inside sovereign physical spaces — facilities, clubs, training grounds, and other SPRTX capital assets.

PHER determines **what** a requestor is (digital) and **what** hardware is present (physical). NEPH determines **who** a requestor is. If you can't prove human backing digitally, NEPH never sees you. If your device isn't declared physically, the facility knows.

Autonomous unbound agents are rejected at the protocol level. Unauthorized transceivers are flagged at the facility level. Both protections exist from day one.

From Greek *pherein* — to carry, to bear. You must bear proof of human involvement to enter digitally. You must bear declared, authorized hardware to enter physically.

---

## Request Flow — Digital Door

```
REQUEST
   │
   ▼
┌──────┐
│ PHER │  classify → analyze → challenge (if needed) → verdict
└──┬───┘
   │
   ├── autonomous_agent ────► REJECT (always)
   ├── unknown ─────────────► CHALLENGE or REJECT
   ├── quarantine ──────────► ENTITY REVIEWS
   │
   ▼
┌───────────┐
│ PHER PASS │  single-use token, 30s TTL
└──┬────────┘
   │
   ▼
┌──────┐
│ NEPH │  step 0: entity + private key + PHER pass
└──┬───┘
   │
   ├── validate → generate → co-sign
   │
   ▼
┌────────────────────-─┐
│ close_out / timed_out│
└──┬──────────────────-┘
   │
   ▼
┌──────────────────────-───┐
│ ALPHA / OMEGA / GAMMA    │
│ (abidance never required)│
└────────────────────────-─┘
```

## Scan Flow — Physical Door

```
RF ZONE (facility, club, training ground)
   │
   ▼
┌───────────┐
│ PHER SCAN │  detect → classify → evaluate policy → verdict per device
└──┬────────┘
   │
   ├── authorized_entity_device ──► CLEAR
   ├── authorized_infrastructure ─► CLEAR
   ├── declared_guest_device ─────► CLEAR
   ├── unknown_device ────────────► FLAG + INVESTIGATE
   ├── unauthorized_transceiver ──► ALERT + ENFORCE
   ├── suspected_harvester ───────► CRITICAL + SECURITY
   ├── undeclared_bci ────────────► ALERT + BCI POLICY
   │
   ▼
┌────────────────────--─┐
│ ZONE STATUS           │
│ clear / advisory /    │
│ alert / critical      │
└───────────────────────┘
```

---

## Requestor Classification — Digital Door

| Class | Description | Verdict |
|-------|-------------|---------|
| `human_direct` | Human at device, no AI intermediary | Pass |
| `human_supervised_agent` | IoSP-registered agent with verified human oversight | Pass |
| `autonomous_agent` | AI agent without human oversight or IoSP binding | **Reject** (always) |
| `unknown` | Cannot determine | Challenge or Reject |

## Device Classification — Physical Door

| Class | Description | Verdict |
|-------|-------------|---------|
| `authorized_entity_device` | Registered to an IoSP entity | Clear |
| `authorized_facility_infrastructure` | Facility-owned hardware | Clear |
| `declared_guest_device` | Declared at check-in | Clear |
| `known_benign_environmental` | Neighboring WiFi, public infra | Clear |
| `unauthorized_transceiver` | Not declared or registered | **Alert** |
| `suspected_harvester` | Actively collecting data | **Critical** |
| `unknown_device` | Cannot classify | **Flag + Investigate** |

---

## Behavioral Analysis — Digital Door

Eight scoring dimensions detect bot patterns. Humans are messy. Bots are clockwork.

| Dimension | Weight |
|-----------|--------|
| `timing_regularity` | 0.15 |
| `request_velocity` | 0.15 |
| `challenge_response_pattern` | 0.15 |
| `data_access_pattern` | 0.15 |
| `interaction_diversity` | 0.10 |
| `session_pattern` | 0.10 |
| `coordination_signal` | 0.10 |
| `linguistic_entropy` | 0.10 |

Weights are tunable by Gamma calibration.

## RF Analysis — Physical Door

Device broadcast behavior is analyzed across multiple dimensions:

| Signal | What It Detects |
|--------|-----------------|
| Active scanning | Device probing for other devices/networks |
| Connection attempts | Unauthorized pairing or data pull attempts |
| Data transmission volume | Unusual outbound = active exfiltration |
| Promiscuous mode | Listening to all traffic, not just addressed |
| MAC randomization | Evasion technique combined with other signals |
| Advertising payload | Known harvester or BCI device signatures |

---

## Hardware Policy — Physical Door

Per-facility rules for device categories:

| Device Type | Default Policy |
|-------------|----------------|
| Smartphones / Tablets | Must declare |
| Smartwatches / Fitness trackers | Allowed |
| Laptops | Must declare |
| **BCI / Neural interfaces** | **Must declare and audit** |
| Smart glasses / AR | Restricted zones only |
| Recording devices | Facility-authorized only |
| Medical implants | Always allowed |
| Unknown transceivers | **Flag and investigate** (protocol floor) |

### BCI-Specific Policy

Brain-computer interfaces require special handling. They are physically attached or implanted, potentially always-on, and can harvest neural, biometric, and environmental data from the wearer and nearby individuals.

| Setting | Default |
|---------|---------|
| Declaration required on entry | Yes |
| Data transmission monitoring | Yes |
| Local-storage-only while in facility | No (requested, not enforced) |
| Shielded zones available | No (facility infrastructure dependent) |
| Third-party data sharing prohibited | Yes |

---

## Protocol Floor

These are enforced for all entities, always, no exceptions:

- Autonomous agents are **rejected** (digital)
- Behavioral analysis is **always on** (digital)
- Liveness for transactions is **always required** (digital)
- PHER pass required for NEPH is **always true** (digital)
- Threat registry participation is **mandatory** (both)
- Physical scan enabled for facilities is **always true** (physical)
- Unauthorized transceivers are **always flagged** (physical)

Entities configure their own perimeter **above** the floor. They can be stricter but never looser.

"Abidance is never required" applies to IoSP features. Security is not a feature. Security is the foundation.

---

## Cross-Layer Integration

| Layer | Integration | Direction |
|-------|-------------|-----------|
| **NEPH**  | `pher_pass_token` required at step 0 | PHER → NEPH (+ feedback loop) |
| **Alpha** | Enforces ceiling limits at perimeter | Alpha → PHER (read-only) |
| **Omega** | Security risk metrics feed (digital + physical) | PHER → Omega (opt-in) |
| **Gamma** | Tunes behavioral score weights | Gamma ↔ PHER (bidirectional) |

Physical presence detected by `pher_scan` can serve as supporting liveness evidence for the digital door, bridging the two perimeters.

---

## Schema Definitions

### Digital Door

| Definition | Purpose |
|------------|---------|
| `requestor_classification` | Classify what a requestor is |
| `liveness_attestation` | Prove human is in the loop (includes physical_presence type) |
| `behavioral_fingerprint` | 8-dimension bot detection |
| `pher_challenge` | Challenge uncertain requestors |
| `pher_check` | Core digital perimeter gate |
| `pher_pass_token` | Single-use bridge to NEPH |
| `quarantine_record` | Entity reviews suspicious requests |

### Physical Door

| Definition | Purpose |
|------------|---------|
| `rf_zone` | Define sovereign physical spaces |
| `device_classification` | Classify detected hardware |
| `hardware_policy` | Per-facility device rules + BCI policy |
| `pher_scan` | Core physical perimeter sweep |
| `scan_incident` | Logged unauthorized hardware events |

### Shared

| Definition | Purpose |
|------------|---------|
| `sovereignty_preferences` | Per-entity config (digital + physical) |
| `pher_incident` | Unified incident log (both doors) |
| `threat_registry_entry` | Protocol-wide collective immunity (both domains) |
| `pher_neph_bridge` | PHER ↔ NEPH handoff contract |
| `pher_omega_feed` | Security metrics to Omega (digital + physical) |
| `pher_gamma_integration` | Gamma calibration loop |
| `pher_alpha_consideration` | Alpha ceiling enforcement |

---

## Files

| File | Description |
|------|-------------|
| `iosp-pher-schema.json` | PHER schema — 19 definitions |
| `README.md` | This document |
| `PHER-EXHIBIT.md` | Architecture diagrams |

---

## Terminology

| Term | Definition |
|------|------------|
| **PHER** | Permissible Human Entry Request — perimeter defense layer |
| **Phered** | Past tense — a request classified and processed by PHER |
| **PHER Pass** | Single-use, short-lived token granting access to NEPH |
| **pher_check** | Digital door — API request perimeter gate |
| **pher_scan** | Physical door — RF zone hardware sweep |
| **RF Zone** | Defined sovereign physical space monitored by pher_scan |
| **Protocol Floor** | Non-configurable security minimums for all entities |
| **Sovereignty Preferences** | Per-entity PHER settings (digital + physical) above the floor |
| **Threat Registry** | Protocol-wide shared threat signatures (digital + physical) |
| **Liveness Attestation** | Proof that a human is actively in the loop |
| **Behavioral Fingerprint** | Composite scoring of requestor behavior patterns |
| **Device Classification** | Physical hardware categorization within an RF zone |
| **Hardware Policy** | Per-facility rules for permitted devices |
| **BCI** | Brain-computer interface (e.g., Neuralink) |

---

## License

This specification is released under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

---

**https://internetofsports.org**

*The protocol belongs to athletes. All people can become athletes.*
