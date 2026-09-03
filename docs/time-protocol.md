# TIME Protocol

**1 TIME = 1 hour of human time offered and purchased through the protocol.**

TIME Protocol is a simple market and settlement layer for human time. One verified human offers time; another verified human purchases it. NEAR is the canonical home for the identity attestations, offers, purchases, balances, escrow, and settlement.

TIME does **not** verify whether the work was performed, whether the buyer was satisfied, or whether a deliverable met an external standard. Those questions belong to the buyer and seller, their Human Bond agreement, or a separate verification, reputation, arbitration, or legal system.

## Components

- human verification registry;
- time offers and purchase agreements;
- TIME balances or receipts representing purchased hours;
- payment, escrow, cancellation, and settlement;
- optional marketplace discovery;
- optional commons distribution;
- governance and treasury controls.

## The simple transaction

```text
Seller: offers 5 hours at an agreed price and terms.
Buyer: accepts and purchases the 5 hours.
Protocol: records the bilateral transaction and settles the payment.
```

The protocol may record the agreed time, price, asset, availability, cancellation terms, and payment status. It does not attest that the seller subsequently performed the work. If the parties want work verification, they can attach an external verifier or a separate Human Bond agreement without changing TIME’s core function.

## Identity and privacy

World ID establishes that the seller and buyer are unique humans; it does not verify work. NEAR records only the commitments and settlement data needed by the protocol. Private terms and personal context should remain encrypted or selectively disclosed.

## Relationship to Human Bond

Human Bond supplies the broader agreement layer for collaboration, including terms, roles, responsibilities, and exit rules. TIME supplies the simple human-time market and settlement layer. A Human Bond agreement may use TIME to price or settle time, while any verification of work remains outside TIME Protocol.
