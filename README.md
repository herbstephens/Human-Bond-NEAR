# Human Bond + TIME Protocol

A NEAR-native protocol for agreements among verified humans and a simple market for purchased human time.

Human Bond and TIME Protocol share one technical home:

- **World ID** anchors the proof that each participant is a unique human.
- **NEAR** hosts the agreements, agents, assets, governance, treasury, and settlement.
- **NEAR Intents and Chain Signatures** provide optional cross-chain execution without making another chain a core dependency.

## The thesis

People need better primitives for working together. Human Bond lets two or more verified humans create a private, human-readable agreement with explicit contributions, shares, permissions, obligations, and exit terms. TIME Protocol lets one verified human offer time and another verified human purchase it: **1 TIME = 1 hour of human time offered and purchased through the protocol**. TIME does not verify work performance; that belongs to the parties or a separate system.

Marriage is one Human Bond template—not the product definition. Other templates include business partnerships, co-ownership, project teams, cooperatives, caregiving, and other human arrangements.

## NEAR-native architecture

```text
World ID attestation
        ↓
NEAR Human Registry
        ↓
Human Bond agents on NEAR
        ↓
Agreement contracts + TIME offers/purchase receipts
        ↓
NEAR assets, treasury, governance, and settlement
        ↓
Optional NEAR Intents / Chain Signatures for external-chain delivery
```

Agents propose, negotiate, explain, and monitor. They do not unilaterally change a charter or release treasury funds. Participant approvals and contract policy remain authoritative.

## Repository status

This is the new NEAR + World ID technical home. It is a greenfield redesign, not an in-place migration of the previous World Chain/Soroban implementations.

- [Architecture](docs/architecture.md)
- [Protocol specification](docs/specification.md)
- [Human Bond model](docs/human-bond.md)
- [TIME Protocol model](docs/time-protocol.md)
- [NEAR agent boundary](docs/agent-architecture.md)
- [Security and privacy](docs/security.md)

## Development direction

1. Define the agreement and identity invariants.
2. Build the NEAR contracts and test them locally.
3. Integrate World ID attestations through a privacy-preserving registry.
4. Add constrained Human Bond agents and approval flows.
5. Implement simple time offers, purchases, receipts, minting, and settlement.
6. Add NEAR-native assets and treasury settlement.
7. Add optional cross-chain delivery only after the NEAR-native path is sound.

**Status:** architecture reset; contracts not yet implemented.

License: MIT
