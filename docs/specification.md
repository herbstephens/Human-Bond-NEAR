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
10. TIME records seller intents, offers, purchases, and settlement of human time; it does not verify work performance or deliverable quality.
11. NEAR Intents is the canonical marketplace interface for TIME offers, discovery, recruitment, negotiation, and purchase preparation.
12. Every seller chooses their own rate; aggregate statistics are descriptive and do not set wages.
13. Canonical TIME accounting is independent of exchange rates and external-chain settlement.

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
- `AgreementRegistry`: agreement lifecycle, membership, charter commitments, policy, status, and Partnership Agent linkage.
- `AgentPolicy`: registration, attestation, capabilities, rate limits, delegation, and revocation for Partner Agents and Partnership Agents.
- `BondRegistry`: consent-based paid third-party queries, disclosure policies, minimal signed responses, fees, expiry, and revocation.
- `Treasury`: deposits, claims, distributions, spending limits, and dissolution.
- `TimeIntentRegistry`: publish, update, expire, cancel, and discover seller TimeOffers and buyer PurchaseIntents through NEAR Intents.
- `TimeMatcher`: permissionless matching, recruitment, negotiation, and solver settlement interface within declared constraints.
- `TimePurchase`: bilateral purchase record, escrow, cancellation, and payment settlement.
- `TimeReceipt`: receipt for purchased time; it is not proof that work was performed.
- `RateStatistics`: privacy-preserving aggregate rate statistics with a committed methodology.
- `TimeCalendar`: optional availability/calendar commitments per verified human.
- `TimeToken`: TIME issuance, transfer, and policy-controlled retirement.
- `CommonsDistributor`: distribution mechanism for protocol-defined commons income.
## Bond Registry query contract

A registry query must include a subject authorization, a named claim, scope, expiry, nonce, and payment. The response is a minimal signed `true`, `false`, or `unknown` result with an as-of block/time. The registry must not expose the other member’s identity or private charter by default.

A query can be application-specific. Human Bond may require both members’ authorization for a relationship-status claim; another application may use a different disclosure policy. No client receives unrestricted access to the relationship graph.

These names are provisional until the contract interfaces are specified.
