# Architecture

## System boundary

Human Bond + TIME Protocol has three layers:

```text
World ID
  proof that a participant is a unique human

NEAR
  Human Registry
  Agreement contracts
  Human Bond agents
  Bond Registry (paid, consent-based queries)
  TIME market and purchase receipts
  fungible tokens and NFTs
  treasuries, governance, and settlement

Optional external execution
  NEAR Intents / Chain Signatures
  delivery to another chain when a user explicitly requests it
```

NEAR is the canonical technical home. External-chain execution is an adapter, never the source of truth for an agreement or TIME accounting.

## Human Bond flow

1. Participants prove uniqueness through World ID.
2. Each participant’s constrained Human Bond agent helps capture intent and negotiate terms.
3. Participants review the human-readable charter.
4. The NEAR Agreement contract records the charter commitment, members, shares, permissions, and exit policy.
5. A NEAR treasury enforces approved deposits, distributions, and withdrawals.
6. Agents monitor deadlines and propose actions; the authorization policy and human approvals decide.

## TIME flow

1. A seller’s verified-human attestation is recorded in the NEAR Human Registry.
2. The seller offers a quantity of time, price, asset, availability, and terms.
3. A buyer—human or non-human, depending on application policy—accepts and purchases the offered time.
4. The protocol records the purchase and settles payment, optionally through escrow.
5. A Time Receipt records the agreed purchase; it is not proof that work was performed.
6. TIME can be held, transferred, exchanged, distributed through the commons mechanism, or used in a Human Bond agreement.
7. If the parties want work verification, they arrange it outside TIME. TIME does not adjudicate performance or quality.

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

## Optional cross-chain execution

The canonical obligation remains on NEAR. A user may request delivery elsewhere:

```text
Canonical obligation: Alice receives 4 TIME-equivalent units.
Execution request: deliver equivalent value in an allowed asset on a supported chain.
```

The route may fail or expire without changing the underlying agreement record.
