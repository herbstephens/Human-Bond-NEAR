# Human Bond agent architecture on NEAR

## The three-agent pattern

The Lisbon prototype used an agent for each partner plus an agent representing the formed partnership. That pattern is part of the NEAR design.

For an agreement with members `A`, `B`, and optionally more members:

```text
Partner A  ↔  Partner B  ↔  ...  ↔  Partner N
    │             │                    │
    ▼             ▼                    ▼
Agent A       Agent B              Agent N
    \             |                    /
     \            |                   /
      └──── Partnership Agent ────────┘
                    │
                    ▼
          NEAR Agreement Contract
```

### 1. Partner agents

Each verified human has a personal Human Bond agent. The agent represents that person’s stated interests and constraints—not their identity itself.

A partner agent may:

- capture its principal’s goals, preferences, boundaries, and proposed contributions;
- explain draft terms and their consequences;
- negotiate with other partner agents within explicit limits;
- prepare or review charter amendments;
- request its principal’s approval for consequential actions;
- monitor obligations, deadlines, time offers, purchase intents, and registry disclosures;
- discover and recruit sellers or buyers through the TIME Intents marketplace;
- negotiate time-sale terms within the principal’s explicit rate, availability, and buyer constraints;
- present proposed distributions or settlement actions.

A partner agent cannot prove humanity, impersonate its principal, change the agreement, consent on the principal’s behalf without an explicit authorization, publish a time offer outside its principal’s constraints, accept a purchase without authorization, or spend shared funds outside policy.

### 2. Partnership agent

Once the parties accept an agreement, a separate Partnership Agent is created to represent the collective agreement itself. It is not another human, is not a member, and has no independent human identity claim.

The Partnership Agent may:

- coordinate authorized TIME Intents for the agreement;
- recruit counterparties and prepare negotiated time purchases;
- maintain the agreement’s operational state and charter commitment;
- coordinate the partner agents;
- translate the accepted charter into permitted workflows;
- track shared deadlines, TIME offers, purchase intents, purchases, balances, and claims;
- recruit counterparties and coordinate NEAR Intent settlement for authorized time purchases;
- propose distributions, amendments, renewals, or dissolution steps;
- prepare authorized registry responses;
- act as the agreement’s interface to NEAR contracts and approved external services;
- produce an auditable activity and decision log.

The Partnership Agent cannot:

- publish a member’s time or change a member’s rate without authorization;
- accept a purchase on behalf of a human without the required approval;
- add or remove a partner by itself;
- change shares or charter terms;
- decide that work was performed;
- release funds without the agreement’s authorization policy;
- disclose private terms or a partner’s identity beyond approved scope;
- convert its agent account into a Human Bond member.

### Lifecycle

```text
1. Human A verifies through World ID and creates Partner Agent A.
2. Human B verifies through World ID and creates Partner Agent B.
3. Partner agents negotiate a proposed charter within their principals’ constraints.
4. Humans review and approve the final charter.
5. NEAR creates the Agreement and Partnership Agent.
6. The Partnership Agent coordinates operations under the accepted policy.
7. Partner agents approve consequential changes and treasury actions.
8. On dissolution, the Partnership Agent enters winding-down state and cannot create new obligations.
```

The same pattern scales to 2–8 human partners. The partnership agent remains one agent per agreement, while each participant retains their own independent agent.

## Authorization model

The protocol distinguishes three things:

| Actor | Represents | Authority |
|---|---|---|
| Partner agent | One human’s interests | Propose, negotiate, monitor, request approval |
| Partnership Agent | The accepted collective agreement | Coordinate and execute only already-authorized workflows |
| NEAR Agreement/Treasury contracts | Protocol rules | Enforce membership, approval, spending, and exit policy |

An agent’s successful signature is not equivalent to human consent. Consequential operations require the relevant participant approvals, threshold rule, or multisig policy recorded by the Agreement contract.

## NEAR implementation boundary

The initial implementation should use:

- a `PartnerAgent` registration and capability record;
- a `PartnershipAgent` record linked to exactly one Agreement;
- principal-to-agent delegation with explicit scope and expiry;
- agent attestation or whitelisting where Shade Agents are used;
- nonces, replay protection, rate limits, revocation, and replacement;
- event logs that identify proposer, approver, Partnership Agent, action, and result.

Agent private context remains private. The chain stores commitments, authorizations, capability status, and action proofs—not unrestricted prompts, relationship conversations, or personal data.

## Registry interaction

The Partnership Agent may prepare a third-party registry response, but it cannot invent or broaden the claim. A paid query must still satisfy:

1. a named claim;
2. subject or Bond authorization;
3. disclosure scope and expiry;
4. payment;
5. the Agreement’s disclosure policy;
6. a minimal signed `true`, `false`, or `unknown` response.

For a relationship-status query, the policy may require approval from both human partners. The Partnership Agent is the controlled interface—not an independent source of consent.
