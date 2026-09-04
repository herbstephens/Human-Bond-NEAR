# Architecture

## System boundary

Human Bond + TIME Protocol has three layers:

```text
World ID
  proof that a participant is a unique human

NEAR
  Human Registry
  Agreement contracts
  Partner Agents (one per human member)
  Partnership Agent (one per formed agreement)
  Bond Registry (paid, consent-based queries)
  NEAR Intents marketplace: time offers, buyer intents, matching, recruitment
  TIME purchases, receipts, and rate statistics
  fungible tokens and NFTs
  treasuries, governance, and settlement

Optional external execution
  NEAR Intents / Chain Signatures
  delivery to another chain when a user explicitly requests it
```

NEAR is the canonical technical home. External-chain execution is an adapter, never the source of truth for an agreement or TIME accounting.

## Human Bond flow

1. Participants prove uniqueness through World ID.
2. Each participant’s Partner Agent helps capture intent and negotiate terms.
3. The Partner Agents present a proposed charter to the participants.
4. Participants review and approve the human-readable charter.
5. NEAR creates the Agreement and its Partnership Agent, which coordinates the accepted charter.
6. A NEAR treasury enforces approved deposits, distributions, and withdrawals.
7. Partner Agents and the Partnership Agent monitor deadlines and propose actions; the authorization policy and human approvals decide.

## TIME flow

1. A seller’s verified-human attestation is recorded in the NEAR Human Registry.
2. The seller publishes a NEAR Intent: “I intend to sell one hour of my time for $X,” with rate, availability, and constraints.
3. Buyer agents, recruiters, and matching services discover the Intent.
4. Agents negotiate within the seller’s declared constraints; the seller explicitly authorizes the final purchase.
5. A buyer—human or non-human, depending on application policy—accepts and purchases the offered time.
6. The protocol records the purchase and settles payment, optionally through escrow.
7. A Time Receipt records the agreed purchase; RateStatistics publishes privacy-preserving aggregate rates. Neither is proof that work was performed.
8. If the parties want work verification, they arrange it outside TIME. TIME does not adjudicate performance or quality.

## Trust boundaries

- A NEAR account is not proof of humanity.
- An agent is not a human and cannot self-authorize as one.
- Agent keys must be constrained, replaceable, rate-limited, and auditable.
- Agents cannot custody shared funds or bypass the agreement’s approval policy.
- World ID proves uniqueness; it does not prove that work happened.
- In Human Bond, every member is a verified human. In the general TIME market, only the seller is required to be a verified human unless an application policy says otherwise.
- TIME does not verify work, deliverables, quality, or satisfaction. Any such verification belongs to the parties or a separate system.
- Registry access is consent-based, paid, scoped, expiring, and privacy-preserving; it is not unrestricted relationship-graph access.
- Private charters and evidence stay encrypted off-chain; NEAR stores commitments and selective disclosures.

## NEAR Intents marketplace

NEAR Intents is a core TIME component. A seller publishes the intent to sell one or more hours at a self-chosen rate. Buyer agents, recruiters, and matching agents discover the intent, negotiate within the seller’s declared constraints, and present a final purchase for explicit seller authorization. The resulting purchase is recorded and settled by NEAR-native TIME contracts.

The canonical offer, seller constraints, accepted purchase, and rate statistics remain on NEAR. Chain Signatures and external-chain delivery are optional execution adapters, not the marketplace itself.

See [TIME Marketplace](time-marketplace.md) for the offer schema, agent flow, Human Bond formation path, and global rate-statistics design.

## Optional cross-chain execution

The canonical obligation remains on NEAR. A user may request delivery elsewhere:

```text
Canonical obligation: Alice receives 4 TIME-equivalent units.
Execution request: deliver equivalent value in an allowed asset on a supported chain.
```

The route may fail or expire without changing the underlying agreement record.
