# TIME Marketplace

## The core intent

The TIME Marketplace is the place where a human offers their time to the world.

```text
I intend to sell 1 hour of my time for $X.
```

The seller is a World ID-verified human. The buyer may be another human, a company, an institution, an agent, or another permitted account. TIME does not verify what happens after the purchase; work performance remains between the parties or a separate system.

The intent is published into the NEAR Intents marketplace as a structured, discoverable offer. Other agents can find it, recruit the seller, negotiate terms within the seller’s boundaries, and form a purchase agreement or Human Bond. NEAR Intents is therefore a core TIME component, not an optional cross-chain feature.

## Offer intent

A seller’s offer should contain:

```text
TimeOffer {
  offer_id
  seller_human_commitment
  seller_account_id
  hours
  hourly_rate
  rate_asset
  minimum_block
  availability_window
  service_categories[]
  location_policy
  communication_policy
  cancellation_policy
  buyer_policy
  negotiation_policy
  expiry
  nonce
}
```

The seller chooses the hourly rate. The protocol does not set a universal wage, approve the rate, or judge whether the rate is fair.

The offer must distinguish:

- **price:** what the seller asks;
- **availability:** when the seller may sell time;
- **terms:** what a buyer may negotiate;
- **purchase:** the accepted quantity and price;
- **performance:** deliberately outside TIME.

## Agent marketplace flow

```text
Seller creates offer intent
          ↓
NEAR Intents marketplace publishes/discovers the intent
          ↓
Buyer, recruiter, or buyer-agent discovers the offer
          ↓
Agents negotiate within declared constraints
          ↓
Seller accepts the final terms
          ↓
TimePurchase contract records the transaction
          ↓
Escrow/payment settles in an accepted asset
          ↓
Time Receipt records the purchased hour(s)
```

A recruiter or agent may propose a buyer, bundle opportunities, negotiate a rate, or assemble a Human Bond. It cannot commit the seller without the seller’s explicit authorization. An agent may not lower the seller’s minimum rate, expand availability, or accept an unapproved buyer policy.

## Purchase intent

A buyer-side intent may specify:

```text
PurchaseIntent {
  buyer_account_id
  desired_hours
  maximum_rate
  payment_asset
  time_window
  categories[]
  location_policy
  required_terms
  expiry
}
```

A solver or agent may match a PurchaseIntent with one or more TimeOffers. The resulting transaction must state the seller, buyer, hours, price, asset, terms, and expiry. Matching does not certify work.

## Human Bond formation

Human Bond is the deeper agreement created when two or more verified humans decide to work together or otherwise enter a continuing relationship.

```text
TIME Offer Intent
  → discovery / recruitment
  → negotiation
  → two or more verified humans approve a Human Bond
  → Partnership Agent coordinates the formed agreement
  → TIME purchases and settlement occur under the Bond terms
```

A simple one-off time purchase does not need to become a Human Bond. A continuing partnership, team, marriage, co-ownership arrangement, or project can become one.

## Global rate data

The marketplace can publish aggregate price statistics while protecting individual privacy. The canonical public statistics should include, at minimum:

- transaction count;
- hours offered and purchased;
- median hourly rate;
- weighted average hourly rate;
- rate distribution percentiles;
- asset and currency normalization method;
- time window;
- category and geography only where the cohort is large enough;
- methodology and excluded transactions.

“Global average” must be defined precisely. The default should be the **hours-weighted average accepted hourly rate** over a stated period, with a median and percentile range displayed alongside it. A simple average of rates would allow a large number of tiny offers to distort the result.

```text
weighted_average_rate = Σ(purchase_hours × accepted_hourly_rate)
                       / Σ(purchase_hours)
```

The protocol should not expose an individual’s rate history by default. Statistics should use thresholded cohorts, delayed publication, aggregation, and privacy-preserving computation where needed. Buyers and sellers may opt out of inclusion in public statistics while their transaction remains recorded for the parties.

The global rate is descriptive, not prescriptive. TIME should never become a centralized wage-setting authority.

## Settlement and cancellation

The TimePurchase contract records:

- accepted offer and purchase intent hashes;
- seller and buyer accounts;
- accepted hours and hourly rate;
- payment asset and amount;
- escrow status;
- cancellation and expiry terms;
- optional external agreement reference;
- receipt status.

It does not record whether the seller performed the work. Refunds or cancellation follow the terms accepted by the parties; TIME does not decide whether a deliverable was satisfactory.

## Contract boundaries

- `TimeIntentRegistry`: publish, update, expire, cancel, and discover TimeOffers and PurchaseIntents.
- `TimeMatcher`: optional permissionless matching and solver settlement interface; it does not alter seller constraints.
- `TimePurchase`: bilateral purchase record, escrow, cancellation, and payment settlement.
- `TimeReceipt`: receipt for purchased time, not proof of work.
- `RateStatistics`: privacy-preserving aggregate statistics and methodology commitments.
- `HumanRegistry`: verifies the seller by default; application policy may require buyer verification.

NEAR Intents provides the intent discovery and solver interface. TIME contracts remain authoritative for seller constraints, accepted purchases, payment status, and aggregate-statistics commitments.
