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
  TIME calendar and work receipts
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

1. A verified-human attestation is recorded in the NEAR Human Registry.
2. The participant receives one calendar subject to the protocol’s time rules.
3. Work is proposed through a Human Bond agreement or another authorized work relationship.
4. Completion evidence and approvals create a Work Receipt.
5. The TIME contract mints or allocates value only after the configured verification condition is met.
6. TIME can be held, transferred, exchanged, distributed through the commons mechanism, or used in an agreement.

## Trust boundaries

- A NEAR account is not proof of humanity.
- An agent is not a human and cannot self-authorize as one.
- Agent keys must be constrained, replaceable, rate-limited, and auditable.
- Agents cannot custody shared funds or bypass the agreement’s approval policy.
- World ID proves uniqueness; it does not prove that work happened.
- Work verification requires explicit evidence, counterparty approval, dispute windows, and anti-collusion controls.
- Private charters and evidence stay encrypted off-chain; NEAR stores commitments and selective disclosures.

## Optional cross-chain execution

The canonical obligation remains on NEAR. A user may request delivery elsewhere:

```text
Canonical obligation: Alice receives 4 TIME-equivalent units.
Execution request: deliver equivalent value in an allowed asset on a supported chain.
```

The route may fail or expire without changing the underlying agreement record.
