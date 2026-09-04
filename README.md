# Human Bond + TIME Protocol

A NEAR-native protocol for agreements among verified humans and a simple market for purchased human time.

Human Bond and TIME Protocol share one technical home:

- **World ID** anchors the proof that each participant is a unique human.
- **NEAR** hosts the agreements, agents, assets, governance, treasury, and settlement.
- **NEAR Intents** is the core marketplace for time offers, buyer intents, discovery, matching, recruitment, and negotiated settlement. Chain Signatures provide optional external-chain delivery without making another chain a core dependency.

## The thesis

People need better primitives for working together. Human Bond lets two or more verified humans create a private, human-readable agreement with explicit contributions, shares, permissions, obligations, and exit terms. TIME Protocol lets a verified human offer time to a buyer that may be human or non-human: **1 TIME = 1 hour of human time offered and purchased through the protocol**. TIME does not verify work performance; that belongs to the parties or a separate system.

Marriage is one Human Bond template—not the product definition. Other templates include business partnerships, co-ownership, project teams, cooperatives, caregiving, and other human arrangements.

## NEAR-native architecture

```text
World ID attestation
        ↓
NEAR Human Registry
        ↓
Partner Agents on NEAR (one per human)
        ↓
Partnership Agent on NEAR (one per formed agreement)
        ↓
NEAR Intents: global human-time offer marketplace
        ↓
TIME purchase contracts, receipts, and rate statistics
        ↓
NEAR assets, treasury, governance, and settlement
        ↓
Optional Chain Signatures for external-chain delivery
```

Agents propose, negotiate, explain, and monitor. They do not unilaterally change a charter or release treasury funds. Participant approvals and contract policy remain authoritative.

## Repository status

This is the new NEAR + World ID technical home. It is a greenfield redesign, not an in-place migration of the previous World Chain/Soroban implementations.

- [Architecture](docs/architecture.md)
- [Protocol specification](docs/specification.md)
- [Human Bond model](docs/human-bond.md)
- [TIME Protocol model](docs/time-protocol.md)
- [TIME Marketplace and Intents](docs/time-marketplace.md)
- [NEAR agent boundary](docs/agent-architecture.md)
- [Human Bond Registry](docs/registry.md)
- [Security and privacy](docs/security.md)

## Development direction

1. Define the agreement and identity invariants.
2. Build the NEAR contracts and test them locally.
3. Integrate World ID attestations through a privacy-preserving registry.
4. Add Partner Agents, the Partnership Agent, and approval flows.
5. Make NEAR Intents the core marketplace for global human-time offers and buyer intents.
6. Add the consent-based, paid Bond Registry with minimal signed claims.
7. Implement time offers, purchases, receipts, minting, settlement, and aggregate rate statistics.
8. Add NEAR-native assets and treasury settlement.
9. Add optional external-chain delivery only after the NEAR-native path is sound.

**Status:** architecture reset; contracts not yet implemented.

License: MIT
