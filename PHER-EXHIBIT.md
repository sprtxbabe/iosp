# PHER Exhibit — Architecture Diagrams

## IoSP Perimeter Defense Layer v0.1.0

**Exhibit Add-On to IoSP Architecture Documentation**
**Schema Reference:** `pher-iosp-schema.json`

---

## Exhibit A: Full IoSP Stack with PHER

```
┌─────────────────────────────────────────────────────────────────────┐
│                        INBOUND REQUEST                              │
│    (human, supervised agent, autonomous bot, unknown)               │
│    (declared device, undeclared hardware, BCI, rogue transceiver)   │
└────────────────────────────────┬────────────────────────────────────┘
                                 │
                                 ▼
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│    ██████╗ ██╗  ██╗███████╗██████╗                                  │
│    ██╔══██╗██║  ██║██╔════╝██╔══██╗                                 │
│    ██████╔╝███████║█████╗  ██████╔╝                                 │
│    ██╔═══╝ ██╔══██║██╔══╝  ██╔══██╗                                 │
│    ██║     ██║  ██║███████╗██║  ██║                                 │
│    ╚═╝     ╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝                                 │
│                                                                     │
│    Permissible Human Entry Request                                  │
│    ONE GATE — TWO DOORS — "What are you?"                           │
│                                                                     │
│    ┌─────────────────────────┐  ┌──────────────────────────┐        │
│    │  DOOR 1 - DIGITAL DOOR  │  │  DOOR 2 - PHYSICAL DOOR  │        │
│    │     (pher_check)        │  │      (pher_scan)         │        │
│    │                         │  │                          │        │
│    │  Classify requestor     │  │  Detect RF devices       │        │
│    │  Behavioral analysis    │  │  Classify hardware       │        │ 
│    │  Liveness check         │  │  BCI policy enforcement  │        │
│    │  Sovereignty prefs      │  │  Hardware policy         │        │
│    │                         │  │                          │        │
│    │  Verdicts:              │  │  Zone status:            │        │
│    │  PASS | CHALLENGE       │  │  CLEAR | ADVISORY        │        │
│    │  REJECT | QUARANTINE    │  │  ALERT | CRITICAL        │        │
│    └────────────┬────────────┘  └──────────────┬───────────┘        │
│                 │                              │                    │
│                 └──────────┬───────────────────┘                    │
│                            │                                        │
│                   SHARED SOVEREIGNTY                                │
│                   SHARED THREAT REGISTRY                            │
│                   SHARED INCIDENT LOG                               │
│                                                                     │
└────────────────────────────────┬────────────────────────────────────┘
                                 │
                    ┌────────────┼─────────────┐
                    │            │             │
                    ▼            ▼             ▼
              ┌──────────┐ ┌─────────┐   ┌──────────┐
              │ REJECTED │ │CHALLENGE│   │QUARANTINE│
              │ (logged) │ │(pending)│   │(entity   │
              └──────────┘ └────┬────┘   │ reviews) │
                                │        └──────────┘
                           responded?
                            ├─ pass ──┐
                            └─ fail ──► REJECTED
                                      │
                    ┌─────────────────┘
                    ▼
         ┌───────────────-──┐
         │  PHER PASS TOKEN │
         │  30s TTL, signed │
         └────────┬────────-┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│    ███╗   ██╗███████╗██████╗ ██╗  ██╗                               │
│    ████╗  ██║██╔════╝██╔══██╗██║  ██║                               │
│    ██╔██╗ ██║█████╗  ██████╔╝███████║                               │
│    ██║╚██╗██║██╔══╝  ██╔═══╝ ██╔══██║                               │
│    ██║ ╚████║███████╗██║     ██║  ██║                               │
│    ╚═╝  ╚═══╝╚══════╝╚═╝     ╚═╝  ╚═╝                               │
│                                                                     │
│    NEPH Key Validation — "Who are you?"                             │
│    Step 0: PHER pass + SPRTX entity + private key                   │
│    Steps 1-3: validate → generate → co-sign                         │
│    Result: close_out ──or── timed_out                               │
│                                                                     │
└────────────────────────────────┬────────────────────────────────────┘
                                 │
                                 ▼
┌─────────────────────────────────────────────────────────────────────┐
│                     PROJECTION LAYERS                               │
│                  (abidance is never required)                       │
│    ┌─────────┐       ┌─────────┐       ┌─────────┐                  │
│    │  ALPHA  │       │  OMEGA  │       │  GAMMA  │                  │
│    │ Ceiling │       │  Floor  │       │Calibrate│                  │
│    └─────────┘       └─────────┘       └─────────┘                  │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Exhibit B: Physical Door — pher_scan Flow

```
┌────────────────────────────────────────────────────────────-─────┐
│                       RF ZONE                                    │
│         (facility, club, training ground, field)                 │
│                                                                  │
│  ┌───────────────────────────────────────────────────-───┐       │
│  │ 1. DETECT                                             │       │
│  │                                                       │       │
│  │  Scan protocols:                                      │       │
│  │  ├─ Bluetooth Classic / BLE                           │       │
│  │  ├─ WiFi 2.4/5/6 GHz                                  │       │
│  │  ├─ NFC / UWB                                         │       │
│  │  ├─ Cellular                                          │       │
│  │  └─ Custom RF                                         │       │
│  │                                                       │       │
│  │  Every broadcasting device is found.                  │       │
│  └──────────────────┬───────────────────────────────-────┘       │
│                     ▼                                            │
│  ┌─────────────────────────────────────────────────-─────┐       │
│  │ 2. CLASSIFY (device_classification)                   │       │
│  │                                                       │       │
│  │  Device registry match? ──► authorized_entity_device  │       │
│  │  Facility infrastructure? ► authorized_infrastructure │       │
│  │  Guest declaration match? ► declared_guest_device     │       │
│  │  Environmental baseline? ─► known_benign              │       │
│  │  Known threat signature? ─► suspected_harvester       │       │
│  │  BCI advertising payload? ► bci_neural_interface      │       │
│  │  None of the above? ─────► unknown_device             │       │
│  └──────────────────┬───────────────────────────────-────┘       │
│                     ▼                                            │
│  ┌───────────────────────────────────────────────────-───┐       │
│  │ 3. EVALUATE (hardware_policy)                         │       │
│  │                                                       │       │
│  │  Device type permitted in this zone?                  │       │
│  │  BCI declared? BCI policy compliance?                 │       │
│  │  Guest device within duration limit?                  │       │
│  │  Recording device authorized?                         │       │
│  │  Unknown transceiver? → always flag (protocol floor)  │       │
│  └──────────────────┬────────────────────────────────-───┘       │
│                     ▼                                            │
│  ┌────────────────────────────────────────────────-──────┐       │
│  │ 4. ANALYZE BROADCAST BEHAVIOR                         │       │
│  │                                                       │       │
│  │  Actively scanning? ─────────────── suspicious if     │       │
│  │  Connection attempts? ──────────────  unauthorized    │       │
│  │  High data transmission? ───────────  = exfiltration  │       │
│  │  Promiscuous mode? ─────────────────  = harvesting    │       │
│  │  MAC randomization + other signals? ─ = evasion       │       │
│  └──────────────────┬───────────────────────────────-────┘       │
│                     ▼                                            │
│  ┌────────────────────────────────────────────────--─────┐       │
│  │ 5. VERDICT PER DEVICE                                 │       │
│  │                                                       │       │
│  │  CLEAR ──────► no action                              │       │
│  │  ADVISORY ───► log + monitor                          │       │
│  │  ALERT ──────► notify staff + entity + enforce        │       │
│  │  CRITICAL ───► security response + threat registry    │       │
│  └───────────────────────────────────────────────────-───┘       │
│                                                                  │
│  ZONE STATUS: clear / advisory / alert / critical                │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

## Exhibit C: BCI Threat Scenario

```
SCENARIO: Person enters SPRTX Club with undeclared Neuralink device

pher_scan detects BLE advertising with bci_signature
       │
       ▼
device_classification:
    ├── device_type_inference: bci_neural_interface
    ├── classification: unauthorized_transceiver
    │   (not in entity_registered_devices, no guest declaration)
    ├── broadcast_behavior:
    │   ├── is_actively_scanning: true
    │   ├── data_transmission_volume: elevated
    │   └── advertising_payload_analysis: bci_signature
    │
    ▼
hardware_policy check:
    ├── bci_neural_interfaces: must_declare_and_audit
    ├── declaration found: NO
    ├── VIOLATION: undeclared BCI
    │
    ▼
bci_specific_policy:
    ├── declaration_required_on_entry: true (FAILED)
    ├── data_transmission_monitoring: true (flagged elevated)
    ├── third_party_data_sharing_prohibited: true
    │
    ▼
scan_incident generated:
    ├── incident_type: undeclared_bci_detected
    ├── severity: high
    ├── action_taken: staff_notified + entity_notified
    ├── affected_entities: [athletes in zone]
    │
    ▼
OUTCOME:
    ├── Staff approaches individual
    ├── Declaration requested
    ├── If declared → reclassified as authorized_entity_device
    │   └── BCI data monitoring begins per policy
    ├── If refused → enforcement escalation per facility policy
    │
    ▼
threat_registry: bci_signature logged for protocol-wide awareness
```

---

## Exhibit D: Cross-Layer Integration

```
                    ┌──────────────────────-─┐
                    │    THREAT REGISTRY     │
                    │  (protocol-wide)       │
                    │  Digital + Physical    │
                    │  signatures            │
                    └───────┬──────┬────────-┘
                       ▲    │      │    ▲
            contribute │    │ query│    │ contribute
                       │    ▼      │    │
        ┌──────────────┴───────────┴────┴──────────────┐
        │                                              │
        │                    PHER                      │
        │        Permissible Human Entry Request       │
        │                                              │
        │   ┌──────────-───┐    ┌──────────────┐       │
        │   │ DIGITAL DOOR │    │PHYSICAL DOOR │       │
        │   │ pher_check   │◄──►│ pher_scan    │       │
        │   └─────────────-┘    └──────────────┘       │
        │      │  physical_presence bridges  │         │
        │      │  physical to digital        │         │
        │      │  liveness attestation       │         │
        └──┬──────-─┬──────────┬───────────┬───────────┘
           │        │          │           │
    ┌──────▼──┐  ┌──▼─────┐ ┌-─▼───────┐ ┌-▼──────────┐
    │  NEPH   │  │ ALPHA  │ │  OMEGA   │ │   GAMMA    │
    │         │  │        │ │          │ │            │
    │ receives│  │ PHER   │ │ receives │ │ tunes PHER │
    │ pher_   │  │enforces│ │ digital  │ │ behavioral │
    │ pass_   │  │ Alpha  │ │ + physic.│ │ score      │
    │ token   │  │ceiling │ │ security │ │ weights    │
    │         │  │ limits │ │ metrics  │ │            │
    └─────────┘  └────────┘ └──────────┘ └────────────┘
```

---

## Exhibit E: Protocol Floor vs Entity Sovereignty

```
┌──────────────────────────────────────────────────────────────-───┐
│                    PROTOCOL FLOOR (immutable)                    │
│                                                                  │
│    DIGITAL                          PHYSICAL                     │
│    ──────────────────               ──────────────────           │
│    • Autonomous agents:             • Scan enabled for           │
│      ALWAYS REJECTED                  facilities: ALWAYS         │
│    • Behavioral analysis:           • Unknown transceivers:      │
│      ALWAYS ON                        ALWAYS FLAGGED             │
│    • Liveness for txns:             • Threat registry:           │
│      ALWAYS REQUIRED                  MANDATORY PARTICIPATION    │
│    • PHER pass for NEPH:                                         │
│      ALWAYS REQUIRED                                             │
│                                                                  │
│    These are NOT features. These are the foundation.             │
│    "Abidance is never required" does NOT apply here.             │
│                                                                  │
│    ┌───────────────────────────────────────────────────--────┐   │
│    │              ENTITY SOVEREIGNTY ZONE                    │   │
│    │              (configurable above floor)                 │   │
│    │                                                         │   │
│    │  DIGITAL                    PHYSICAL                    │   │
│    │  ▲ human_only               ▲ active_response           │   │
│    │  │ allowlisted_only         │ active_monitoring         │   │
│    │  │ supervised_allowed       │ advisory                  │   │
│    │  │ (default)                │ (default)                 │   │
│    │  ├──────────────────────────┤                           │   │
│    │  │     PROTOCOL FLOOR       │  PROTOCOL FLOOR           │   │
│    │  └──────────────────────────┴────────────────────────   │   │
│    │                                                         │   │
│    │  Entities raise the bar. Never lower it.                │   │
│    │  Only human_direct can change settings.                 │   │
│    └───────────────────────────────────────────────────-───-─┘   │
└────────────────────────────────────────────────────────────────-─┘
```

---

## Exhibit F: Moltbook Bot or Sim + Rogue Hardware — Combined Scenario

```
SCENARIO: SPRTX Club under simultaneous digital and physical attack

═══ DIGITAL DOOR ═══

OpenClaw bot or similar bot scraping athlete profiles via API
       │
       ▼
pher_check:
├── classification: autonomous_agent (no SPRTX registration)
├── behavioral_risk: critical (0.87)
├── threat_registry: MATCH openclaw-scraper signature
├── VERDICT: REJECT
├── incident logged, threat registry updated
└── NEPH never sees this request

═══ PHYSICAL DOOR ═══

Simultaneously: unknown Bluetooth device detected in weight room
       │
       ▼
pher_scan:
├── device_type_inference: bluetooth_relay
├── classification: unauthorized_transceiver
├── broadcast_behavior:
│   ├── is_actively_scanning: true
│   ├── connection_attempts_observed: 14
│   ├── is_promiscuous_mode: true
│   └── data_transmission_volume: high
├── VERDICT: CRITICAL
├── action: security_alert_triggered + device_blocked_from_network
├── affected_entities: [athletes in weight room] notified
└── threat_registry: hardware signature shared protocol-wide

═══ COMBINED ═══

Both incidents logged to unified pher_incident with incident_domain
Both contribute to threat_registry (digital + physical)
Both feed PHER → Omega security metrics
Entity notified once with combined summary
Facility security responds to physical threat
Digital threat handled automatically

The sea monster guards the shore.
The sea monster also patrols the waters inside.
```

---

## Exhibit G: Schema Manifest

```
┌────────────────────────────────────────────────────────────--─────┐
│                     IoSP SCHEMA STACK                             │
│                                                                   │
│  v0.1.0 (current)                                                 │
│  ├── iosp-protocol-schema.json         Unified protocol spec      │
│  ├── iosp-sprtx-bridge-schema.json     Protocol ↔ chain bridge    │
│  ├── iosp-agent-schema.json            AI agents bound to entity  │
│  ├── iosp-agent-bridge-schema.json     Agent dual-layer bridge    │
│  │                                                                │
│  v0.1.0 (new addition — self-contained)                           │
│  ├── iosp-pher-schema.json      ◄──── PHER perimeter defense      │
│  │     19 definitions                   (digital + physical)      │
│  ├── README.md                  ◄──── PHER documentation          │
│  └── PHER-EXHIBIT.md            ◄──── PHER diagrams (this file)   │
│                                                                   │
│  v0.2.0 (planned — integration)                                   │
│  ├── iosp-protocol-schema.json  ◄──── + pher_pass in neph_state   │
│  │                              ◄──── + sovereignty on entities   │
│  ├── iosp-agent-schema.json     ◄──── + pher_status on agent      │
│  ├── iosp-agent-bridge-schema   ◄──── + pher_required routing     │
│  └── iosp-sprtx-bridge-schema   ◄──── + pher endpoints            │
│                                                                   │
│  Repository: github.com/sprtxbabe/iosp                            │
└───────────────────────────────────────────────────────────────--──┘
```

---

*PHER — the sea monster guards our shore and patrols our waters inside.*
*One gate. Two doors. Human-backed or nothing.*
