# Protocol specification

## Core invariants

1. Every agreement member is a cryptographically verified unique human.
2. Agreements contain humans, not LLCs, DAOs, or other entities as members.
3. A human may participate in multiple agreements unless a template explicitly applies an exclusivity policy.
4. TIME is a market/settlement protocol, not a work-verification protocol.
5. TIME requires the seller to be a verified human; the buyer may be a human or a non-human buyer account unless an application-specific policy says otherwise.
6. A member’s wallet is replaceable; the privacy-preserving human identity commitment is the durable identity key.
7. Shares are explicit and sum to 10,000 basis points.
8. No agent can unilaterally alter a charter, add a member, or release shared funds.
9. Every agreement has an explicit exit and dissolution path.
10. TIME records offers and purchases of human time; it does not verify work performance or deliverable quality.
11. Canonical TIME accounting is independent of exchange rates and external-chain settlement.

## Agreement

```text
Agreement {
  id
  members[]
  charter_hash
  template
  policy
  treasury
  status
  created_at
  amended_at
}

Member {
  human_commitment
  account_id
  share_bps
  role
  joined_at
  status
}

Policy {
  exclusive
  transferable
  amendment_rule
  treasury_rule
  exit_rule
  dispute_rule
}
```

Initial scope: 2–8 members. Larger groups can later use a separate collective/DAO model without weakening the Human Bond human-member invariant.

## Initial contract boundaries

- `HumanRegistry`: World ID attestation commitments, nullifier uniqueness, revocation, and recovery.
- `AgreementRegistry`: agreement lifecycle, membership, charter commitments, and policy.
- `Treasury`: deposits, claims, distributions, spending limits, and dissolution.
- `TimeMarket`: time offers, purchases, prices, availability, cancellations, and settlement.
- `TimeReceipt`: a receipt for an agreed time purchase; it is not proof that work was performed.
- `TimeCalendar`: optional availability/calendar commitments per verified human.
- `TimeToken`: TIME issuance, transfer, and policy-controlled retirement.
- `ExternalVerificationAdapter` (optional): references a separate verifier or Human Bond agreement without making verification part of TIME’s core.
- `CommonsDistributor`: distribution mechanism for protocol-defined commons income.
- `AgentPolicy`: agent registration, attestation, capabilities, rate limits, and revocation.

These names are provisional until the contract interfaces are specified.
