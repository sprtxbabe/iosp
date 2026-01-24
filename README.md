# Internet of Sports Protocol (IoSP)

**A decentralized framework for athlete data sovereignty and the optimization of human performance.**

[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](https://github.com/sprtxbabe/iosp)
[![License](https://img.shields.io/badge/license-CC%20BY--SA%204.0-green.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

---

## Overview

The Internet of Sports Protocol (IoSP) is a counter-framework to the Internet of Bodies (IoB). Where IoB frames the human body as a patient to be monitored, IoSP frames it as an instrument to be optimized.

IoSP is not an application. It is a protocol — the foundational rails upon which the entire sports data ecosystem can operate.

**Core tenets:**

- **Universal athletic identity** — all people can become athletes
- **Data sovereignty through co-ownership** — athletes own and monetize their data
- **Protocol independence** — designed for migration beyond IP infrastructure

---

## Documentation

| Document | Description |
|----------|-------------|
| [Whitepaper](whitepaper.md) | Complete protocol specification and vision |
| [Schemas](schemas/) | JSON Schema definitions for all entity types |

---

## Protocol Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    CONSENSUS LAYER                       │
│                      SPRTX.net                           │
│         Root blockchain network for all IoSP chains      │
└─────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────┐
│                   RESOLUTION LAYER                       │
│              iosp:// address → location                  │
│                  web | mesh | ndn                        │
└─────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────┐
│                      DATA LAYER                          │
│     entities | relationships | assets | events | gov     │
└─────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────┐
│                    IDENTITY LAYER                        │
│           canonical address + alias + token              │
└─────────────────────────────────────────────────────────┘
```

---

## Addressing Scheme

Every entity has a dual address:

**Canonical** (immutable, UUID-based)
```
iosp://athlete/550e8400-e29b-41d4-a716-446655440000
```

**Alias** (human-readable, registered)
```
iosp://athlete/maria-santos
```

### Namespaces

```
iosp://athlete/       iosp://team/          iosp://league/
iosp://organization/  iosp://facility/      iosp://media/
iosp://stream/        iosp://token/         iosp://contract/
iosp://session/       iosp://competition/   iosp://transaction/
iosp://governance/    iosp://permission/    iosp://dispute/
```

---

## Repository Structure

```
iosp/
├── README.md
├── whitepaper.md
├── LICENSE
└── schemas/
    ├── iosp-protocol-schema.json
    ├── iosp-athlete-schema.json
    ├── iosp-team-schema.json
    └── ...
```

---

## Contributing

IoSP is in active development. Schema contributions, implementation feedback, and integration partnerships are welcome.

---

## License

This specification is released under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

---

**https://internetofsports.org**

*The protocol belongs to athletes. All people can become athletes.*
