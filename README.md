# Human Bond + TIME Protocol

A NEAR-native protocol for agreements among verified humans and a simple market for purchased human time.

Human Bond and TIME Protocol share one technical home:

- **World ID** anchors the proof that each participant is a unique human.
- **NEAR** hosts the agreements, agents, assets, governance, treasury, and settlement.
- **NEAR Intents** is the core marketplace for time offers, buyer intents, discovery, matching, recruitment, and negotiated settlement. Chain Signatures provide optional external-chain delivery without making another chain a core dependency.

## The thesis

Human Bond is an operating system for partnerships among humans. It helps two or more people turn a relationship that already exists in practice—marriage, household, family enterprise, small business, co-ownership, or project—into a human-readable agreement with explicit contributions, shares, roles, treasury rules, permissions, obligations, and exit terms.

Many partnerships are difficult to manage in real life. A small business or household partnership may need bylaws or a partnership agreement, a lawyer, a bank account, accounting, spending controls, savings and investment decisions, records, and a plan for disagreement or dissolution. Those institutions are important, but difficult and expensive to assemble. Human Bond provides the shared operating layer and connects the partners to lawyers, accountants, banks, legal entities, and regulated providers when needed.

Marriage is one of the clearest partnership templates. One spouse may earn most or all of the visible income while the other contributes care, household management, property work, or support that makes that income possible. Human Bond can model the partnership’s agreed economic rules, including joint treasury, contributions, savings, investments, and distributions, without assuming that cash income is the only contribution or replacing jurisdiction-specific law.

Marriage is a template, not the category.

TIME Protocol lets a verified human offer time to a buyer that may be human or non-human: **1 TIME = 1 hour of human time offered and purchased through the protocol**. TIME does not verify work performance; that belongs to the parties or a separate system.

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

The legal entity, if one is needed, is an external legal wrapper. The Human Bond remains an agreement among humans. A bank, company, lawyer, accountant, investment provider, or other institution can connect to the partnership but is not a Human Bond member.

## Repository status

This is the new NEAR + World ID technical home. It is a greenfield redesign, not an in-place migration of the previous World Chain/Soroban implementations.

- [Architecture](docs/architecture.md)
- [Protocol specification](docs/specification.md)
- [Human Bond model](docs/human-bond.md)
- [Partnership operating platform](docs/partnership-platform.md)
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
5. Build the partnership operating layer: treasury, budgets, spending, savings, investments, distributions, records, and dissolution.
6. Make NEAR Intents the core marketplace for global human-time offers and buyer intents.
7. Add the consent-based, paid Bond Registry with minimal signed claims.
8. Implement time offers, purchases, receipts, minting, settlement, and aggregate rate statistics.
9. Add NEAR-native assets and treasury settlement.
10. Add optional external-chain delivery only after the NEAR-native path is sound.

**Status:** architecture reset; contracts not yet implemented.

License: MIT
