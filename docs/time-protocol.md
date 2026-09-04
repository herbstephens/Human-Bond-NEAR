# TIME Protocol

**1 TIME = 1 hour of human time offered and purchased through the protocol.**

TIME Protocol is a simple market and settlement layer for human time. A verified human offers time; a buyer—who may be a human, company, institution, agent, or other permitted account—purchases it. NEAR is the canonical home for the seller’s identity attestation, offers, purchases, balances, escrow, and settlement.

TIME does **not** verify whether the work was performed, whether the buyer was satisfied, or whether a deliverable met an external standard. Those questions belong to the buyer and seller, their Human Bond agreement, or a separate verification, reputation, arbitration, or legal system.

## Components

- human verification registry;
- time offers and purchase agreements;
- TIME balances or receipts representing purchased hours;
- NEAR Intents time-offer and purchase marketplace;
- agent discovery, recruitment, negotiation, and solver execution;
- payment, escrow, cancellation, and settlement;
- aggregate global rate statistics;
- optional commons distribution;
- governance and treasury controls.

## The canonical time intent

The canonical TIME marketplace action is a NEAR Intent:

```text
I intend to sell 1 hour of my human time for $X.
```

The seller chooses the hourly rate. The intent is discoverable by buyer agents, recruiters, and matching services. They may recruit the seller, negotiate within the seller’s declared constraints, and prepare a purchase or Human Bond. The seller must explicitly authorize the resulting purchase.

NEAR Intents is therefore part of TIME’s core marketplace, not an optional adapter. TIME contracts remain authoritative for seller constraints, accepted purchases, escrow, settlement, and receipts.

See [TIME Marketplace](time-marketplace.md) for the offer schema, buyer intents, matching flow, and aggregate-rate design.

## The simple transaction

```text
Seller: verified human publishes a NEAR Intent to sell 5 hours at a self-chosen rate and terms.
Agents: discover, recruit, negotiate, and prepare a proposed purchase within those constraints.
Buyer: human, company, institution, agent, or other permitted account accepts and purchases the 5 hours.
Protocol: records the accepted purchase and settles the payment.
```

The protocol may record the agreed time, price, asset, availability, cancellation terms, and payment status. It does not attest that the seller subsequently performed the work. If the parties want work verification, they can attach an external verifier or a separate Human Bond agreement without changing TIME’s core function.

## Identity and privacy

World ID establishes that the seller is a unique human; the buyer does not need to be human unless a particular application or agreement requires it. World ID does not verify work. NEAR records only the commitments and settlement data needed by the protocol. Private terms and personal context should remain encrypted or selectively disclosed.

## Relationship to Human Bond

Human Bond supplies the broader agreement layer for collaboration, including terms, roles, responsibilities, and exit rules. TIME supplies the simple human-time market and settlement layer. A Human Bond agreement may use TIME to price or settle time, while any verification of work remains outside TIME Protocol.
