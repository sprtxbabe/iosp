# Internet of Sports Protocol (IoSP)

## A Decentralized Framework for Athlete Data Sovereignty and the Optimization of Human Performance

**Version 0.1.0**  
**January 2026**

---

## Abstract

The Internet of Bodies (IoB) has emerged as the dominant paradigm for connected human-centric data systems, framing the body as a subject of medical surveillance—a patient to be monitored for dysfunction. This paper introduces the Internet of Sports Protocol (IoSP), a counter-framework that treats the human body not as a liability to be managed, but as an instrument to be optimized. IoSP establishes a decentralized, athlete-owned data protocol designed for eventual migration beyond traditional IP infrastructure, enabling a future where all people identify as athletes and own the longitudinal record of their physical development.

IoSP is not an application. It is a protocol—the foundational rails upon which the entire sports data ecosystem can operate.

---

## Table of Contents

1. [Introduction: The Problem with IoB](#1-introduction-the-problem-with-iob)
2. [The IoSP Vision](#2-the-iosp-vision)
3. [Core Principles](#3-core-principles)
4. [Technical Architecture](#4-technical-architecture)
5. [Addressing Scheme](#5-addressing-scheme)
6. [Data Schema](#6-data-schema)
7. [Tokenization Layer](#7-tokenization-layer)
8. [Network Evolution](#8-network-evolution)
9. [Governance](#9-governance)
10. [Implementation Roadmap](#10-implementation-roadmap)
11. [Conclusion](#11-conclusion)

---

## 1. Introduction: The Problem with IoB

The Internet of Bodies represents the convergence of connected devices worn on, implanted in, or ingested into the human body. Pacemakers, continuous glucose monitors, fitness trackers, and smart pills form an ecosystem that collects, transmits, and acts upon biometric data.

The framing is inherently medical. The body is a site of potential failure. Data flows to institutions—hospitals, insurers, pharmaceutical companies—who maintain custody and extract value. The individual is a data subject, not a data owner.

**The IoB model creates three fundamental problems:**

1. **Ownership Asymmetry**: The individual generates the data but rarely controls it. Healthcare systems, device manufacturers, and insurers hold the keys.

2. **Reactive Framing**: IoB is designed to detect dysfunction—disease, deterioration, deviation from baseline. It optimizes for avoiding negative outcomes rather than achieving positive ones.

3. **Infrastructure Dependency**: IoB relies entirely on existing internet infrastructure controlled by centralized entities. Data flows through servers owned by corporations and governed by jurisdictions that may not align with individual interests.

---

## 2. The IoSP Vision

The Internet of Sports Protocol inverts the IoB paradigm.

Where IoB sees a patient, IoSP sees an athlete. Where IoB monitors for failure, IoSP tracks toward optimization. Where IoB centralizes custody, IoSP distributes ownership.

**The core assertion**: All people are athletes. Not in the professional sense, but in the fundamental sense that every human body is capable of physical development, measurable performance, and longitudinal improvement.

IoSP creates the infrastructure for this identity. An 80-year-old tracking walking cadence is an athlete. A child learning to swim is an athlete. A weekend cyclist is an athlete. A social pickleball player is an athlete. A professional quarterback is an athlete. The protocol makes no distinction in kind—only in data density.

---

## 3. Core Principles

### 3.1 Universal Athletic Identity

Every participant receives a persistent, portable identity that travels with them across platforms, applications, and organizations. This identity is not owned by any single service provider.

### 3.2 Data Sovereignty Through Co-Ownership

Athletes own their data. The protocol establishes a co-ownership model where the athlete retains majority stake (85%) and the network retains a minority stake (15%) to ensure data persistence and network sustainability. This is non-revocable by design—once data enters the network, it cannot be unilaterally deleted, only permissioned.

### 3.3 Protocol Independence

IoSP is designed for migration beyond IP infrastructure. While current implementations use web protocols, the addressing scheme and data model are transport-agnostic. As mesh networks, named data networking, and other post-IP architectures mature, IoSP can migrate without changing its fundamental structure.

### 3.4 Tokenization as Ownership Layer

Every entity in the network—athlete, team, league, facility—can be tokenized. Tokens represent ownership stakes, governance rights, and economic participation. The token layer sits atop the data layer, inheriting its structure.

---

## 4. Technical Architecture

### 4.1 Four-Layer Stack

```
┌─────────────────────────────────────────────────────────┐
│                    CONSENSUS LAYER                      │
│                      SPRTX.net                          │
│         Root blockchain network for all IoSP chains     │
└─────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────┐
│                   RESOLUTION LAYER                      │
│              iosp:// address → location                 │
│                  web | mesh | ndn                       │
└─────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────┐
│                      DATA LAYER                         │
│     entities | relationships | assets | events | gov    │
└─────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────┐
│                    IDENTITY LAYER                       │
│           canonical address + alias + token             │
└─────────────────────────────────────────────────────────┘
```

### 4.2 Identity Layer

Every entity has a canonical address (UUID-based, immutable) and may have one or more aliases (human-readable, mutable). The canonical address is the permanent identifier; aliases are convenience mappings.

### 4.3 Data Layer

Structured data conforming to published JSON schemas. The schema definitions are versioned and extensible. All data is signed by the originating entity and timestamped.

### 4.4 Consensus Layer

Validates ownership and state changes. Token transfers, contract executions, and permission grants require consensus. The blockchain serves as the auditable record of ownership, not the storage mechanism for data. SPRTX.net operates as the root blockchain network coordinating all IoSP chains—a necessity of the co-ownership model, where protocol-level stake must be verifiable across every entity regardless of which chain hosts their token.

### 4.5 Resolution Layer

Maps `iosp://` addresses to network locations. In the current web-based implementation, this resolves to HTTPS endpoints. Future implementations may resolve to mesh node identifiers, NDN names, or other addressing schemes.

---

## 5. Addressing Scheme

### 5.1 Canonical Address

```
iosp://[entity-type]/[uuid]
```

Example:
```
iosp://athlete/550e8400-e29b-41d4-a716-446655440000
```

### 5.2 Alias Address

```
iosp://[entity-type]/[slug]
```

Example:
```
iosp://athlete/maria-smith-etc
```

### 5.3 Namespaces

The protocol defines the following entity types:

| Namespace | Description |
|-----------|-------------|
| `iosp://athlete/` | Individual athletes |
| `iosp://team/` | Organized teams |
| `iosp://league/` | Leagues and governing bodies |
| `iosp://organization/` | Academies, agencies, sponsors |
| `iosp://facility/` | Physical locations |
| `iosp://media/` | Content assets |
| `iosp://stream/` | Live data feeds |
| `iosp://token/` | Tokenized assets |
| `iosp://contract/` | Agreements between entities |
| `iosp://session/` | Training and performance sessions |
| `iosp://competition/` | Competitive events |
| `iosp://transaction/` | Token and data movements |
| `iosp://governance/` | Rules and voting records |
| `iosp://permission/` | Access grants |
| `iosp://dispute/` | Conflict resolution records |

---

## 6. Data Schema

### 6.1 Top-Level Structure

```
IoSP
├── entities
│   ├── athletes[]
│   ├── teams[]
│   ├── leagues[]
│   ├── organizations[]
│   └── facilities[]
│
├── relationships
│   ├── memberships[]
│   ├── contracts[]
│   └── affiliations[]
│
├── assets
│   ├── tokens[]
│   ├── media[]
│   └── data_streams[]
│
├── events
│   ├── competitions[]
│   ├── sessions[]
│   └── transactions[]
│
├── governance
│   ├── rules[]
│   ├── permissions[]
│   └── disputes[]
│
└── meta
    ├── schema_version
    ├── protocol_id
    └── network_state{}
```

### 6.2 Entity Hierarchy

Entities form a natural hierarchy:

```
Athlete → Team → League
   ↓        ↓       ↓
 Token   Token   Token
```

Each level is a JSON object that contains references to the level below. The tokenization layer mirrors the entity structure exactly.

### 6.3 Schema Versioning

All schemas include a `schema_version` field. The protocol maintains backward compatibility—older schemas remain valid, newer schemas add fields without removing existing ones.

---

## 7. Tokenization Layer

### 7.1 Token Types

| Type | Description |
|------|-------------|
| **Entity Token** | Represents ownership stake in an entity (athlete, team, league) |
| **Access Token** | Grants permission to view or use specific data |
| **Governance Token** | Confers voting rights in protocol decisions |
| **Utility Token** | Redeemable for services within the network |

### 7.2 Token Properties

Every IoSP token includes:

- **Bound Entity**: The iosp_address of the entity it represents
- **Chain**: The entity-specific chain
- **Chain Network**: SPRTX.net as root network coordinating all IoSP chains
- **Contract Address**: On-chain location
- **Token Standard**: ERC-721, ERC-1155, or custom
- **Supply Metrics**: Total and circulating supply
- **Metadata URI**: Link to off-chain attributes

### 7.3 Co-Ownership Encoding

```json
{
  "ownership": {
    "sprtx_share": 15,
    "entity_share": 85,
    "terms_hash": "0xabc123...",
    "non_revocable": true,
    "monetization_rights": "full"
  }
}
```

### 7.4 External Chain Interoperability

IoSP tokens are native to SPRTX.net. External blockchains may reference IoSP state but cannot modify it.

**Read-only access patterns:**

| Method | Description |
|--------|-------------|
| **Oracle Feeds** | External chains subscribe to verified SPRTX.net state updates |
| **Light Client Proofs** | Cryptographic proofs of token ownership verifiable without trust |
| **Public Indexers** | Queryable APIs exposing IoSP data for external consumption |

**External chains can:**
- Verify token existence and ownership
- Validate athlete credentials and affiliations
- Reference co-ownership percentages
- Confirm contract terms

**External chains cannot:**
- Transfer or burn IoSP tokens
- Modify entity state
- Execute SPRTX.net contracts
- Override governance decisions

This model enables broad ecosystem integration—fantasy platforms, credential verifiers, sponsors, and third-party applications—while preserving data sovereignty on SPRTX.net. External systems consume; they do not control.

### 7.5 Three-Key Security Model

Traditional blockchains operate on a two-key architecture:

1. **Public key** — identity
2. **Private key** — owner control

This model grants absolute authority to the private key holder. Loss means permanent loss. Theft means permanent theft. No recovery, no recourse.

SPRTX.net introduces a third key — the **Network Ephemeral (NEPH) Key**:

1. **Public key** — identity
2. **Private key** — owner control
3. **NEPH Key** — protocol co-signature

The NEPH Key is not stored. It is generated at transaction time, used to co-sign the operation, and immediately destroyed. What persists is the cryptographic proof—timestamp and event record—not the key itself.

**This enables:**
- Cryptographic enforcement of co-ownership
- Recovery mechanisms for lost private keys
- Protocol-level transaction validation
- Immunity to external chain manipulation
- No persistent secret to compromise

The three-key model is why external chains cannot modify IoSP state—they cannot generate the NEPH Key. Read access requires no signature; write access requires two, one of which exists only for an instant.

Co-ownership is not a policy. It is a cryptographic condition.

---

## 8. Network Evolution

### 8.1 Phase 1: Web Infrastructure (Current)

The protocol operates on existing web infrastructure. Resolvers map `iosp://` addresses to HTTPS endpoints. Data is stored in conventional databases with blockchain anchoring for ownership records.

### 8.2 Phase 2: Hybrid Infrastructure

As decentralized storage (IPFS, Arweave) matures, data layer migrates to content-addressed storage. Resolution layer gains redundancy through multiple resolver implementations.

### 8.3 Phase 3: Protocol Independence

Full migration to transport-agnostic addressing. Mesh networks, satellite links, and named data networking become viable resolution targets. The protocol survives infrastructure fragmentation.

---

## 9. Governance

### 9.1 Protocol Governance

Major protocol changes require token-weighted voting. Schema modifications, fee structure changes, and network upgrades follow a proposal → discussion → vote → implementation cycle.

### 9.2 Entity Governance

Individual entities (teams, leagues) may implement their own governance rules within the protocol framework. A league may require member teams to adopt specific data sharing policies. A team may grant token holders voting rights on roster decisions.

### 9.3 Dispute Resolution

The protocol includes a dispute resolution framework for conflicts between entities. Disputes are logged on-chain with resolution records permanently attached.

---

## 10. Implementation Roadmap

| Phase | Timeline | Milestone |
|-------|----------|-----------|
| **Foundation** | Q1 2026 | Protocol specification, core schemas, reference resolver |
| **Pilot** | Q2-Q3 2026 | Partner integrations, athlete onboarding, token pilot |
| **Scale** | Q4 2026 | Public launch, multi-chain deployment, governance activation |
| **Independence** | 2027+ | Alternative transport layers, mesh network support |

---

## 11. Conclusion

The Internet of Bodies frames humanity as patients. The Internet of Sports Protocol frames humanity as athletes.

This is not a semantic distinction. It is an architectural one. The systems we build encode the assumptions we make about human potential. IoB assumes decline; IoSP assumes development. IoB centralizes control; IoSP distributes ownership. IoB depends on existing infrastructure; IoSP prepares for independence.

IoSP is a protocol, not a product. It defines the rails upon which an entire ecosystem can operate—streaming platforms, coaching applications, scouting services, fantasy sports, insurance products, facility networks, and applications not yet imagined.

The protocol belongs to athletes. All people can become athletes.

This is the infrastructure for that future.

---

## Appendix A: Schema Specifications

Full JSON Schema specifications are maintained in the `/schemas` directory:

```
iosp/
├── schemas/
│   ├── iosp-protocol-schema.json
│   ├── iosp-athlete-schema.json
│   ├── iosp-team-schema.json
│   ├── iosp-league-schema.json
│   ├── iosp-organization-schema.json
│   ├── iosp-facility-schema.json
│   ├── iosp-contract-schema.json
│   ├── iosp-token-schema.json
│   ├── iosp-media-schema.json
│   ├── iosp-stream-schema.json
│   ├── iosp-competition-schema.json
│   ├── iosp-session-schema.json
│   ├── iosp-transaction-schema.json
│   ├── iosp-permission-schema.json
│   ├── iosp-dispute-schema.json
│   └── iosp-governance-schema.json
└── examples/
    └── sample-entities/
```

---

## Appendix B: Terminology

| Term | Definition |
|------|------------|
| **IoSP** | Internet of Sports Protocol |
| **IoAT** | Internet of Athletes — the network of athlete entities in IoSP |
| **Canonical Address** | UUID-based, immutable entity identifier |
| **Alias** | Slug-based, human-readable entity identifier |
| **Co-Ownership** | Shared data rights between entity and protocol |
| **Non-Revocable** | Data layer cannot be deleted from network |
| **Resolver** | Service that maps iosp:// addresses to network locations |
| **SPRTX.net** | Root blockchain network coordinating all IoSP chains |
| **NEPH Key** | Network Ephemeral Key — protocol co-signature generated by SPRTX.net at transaction time and immediately destroyed |

---

## License

This specification is released under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

---

*This document establishes the foundational specification for the Internet of Sports Protocol. Version 0.1.0 reflects the initial public release of the protocol architecture and schema framework.*

*Published: January 2026*

**https://internetofsports.org**

*The protocol belongs to athletes. All people can become athletes.*
