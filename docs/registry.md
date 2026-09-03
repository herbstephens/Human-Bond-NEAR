# Human Bond Registry

The Human Bond Registry is a consent-based, paid verification service for third parties that need to know whether a person has an active Human Bond of a particular type. The Partnership Agent may prepare a response, but cannot grant disclosure consent or broaden the claim beyond the Agreement’s policy.

A service such as Tinder may query the registry—for example, to determine whether a consenting user has an active exclusive marriage-type Bond. The registry does not publish a global list of relationships and does not reveal private charter contents.

## Registry principle

> A third party pays for an authorized answer about a specific subject and claim. It does not buy unrestricted access to the identity graph.

The registry returns a minimal, signed result such as:

```text
claim: subject has an active exclusive marriage-type Human Bond
subject: authorized identifier or privacy-preserving commitment
status: true | false | unknown
as_of: block height / timestamp
expires: response expiry
policy: registry policy version
proof: verifiable registry response
```

The result should not disclose the other member’s identity, the charter, wallet balances, location, messages, or private terms unless every affected person has separately authorized that disclosure.

## Query flow

1. The subject explicitly authorizes a third party and defines the permitted claim, scope, and duration.
2. The third party submits a query and payment in an accepted NEAR asset.
3. The Registry verifies the authorization, payment, purpose/scope, and query limits.
4. The Registry returns a minimal answer or a privacy-preserving proof.
5. The subject may revoke future queries; previously issued answers remain attributable to their issue time and expiry.
6. The third party can verify the response without trusting a private API operator.

For Human Bond’s two-human application, a query about a relationship status should require the subject’s consent and the Bond’s disclosure policy. The default answer is `unknown` when the request is unauthorized, expired, ambiguous, or outside scope—not a data leak.

## Query classes

- **Subject-authorized status:** a user authorizes a specific service to check a named claim.
- **Bond-authorized disclosure:** the Human Bond’s policy authorizes a defined disclosure to approved service classes.
- **Aggregate analytics:** only privacy-preserving aggregate statistics; no individual lookup.
- **Public registry:** limited to data that all affected members deliberately made public.

An application may require both Human Bond members to authorize disclosure. A platform must not infer consent merely because one member connected a wallet or owns an NFT.

## Contract boundary

`BondRegistry` should manage:

- Bond status and template classification commitments;
- disclosure policies and consent records;
- third-party query credentials or service identifiers;
- query payments and fee splits;
- signed responses, expiries, and nonces;
- revocation and emergency pause;
- rate limits and anti-enumeration controls.

It should not store the private charter or create a public member-to-member graph. Sensitive details remain encrypted off-chain, with only commitments and minimum status data on NEAR.

## Economic model

The query fee is a protocol payment, not a license to resell personal data. The design must specify:

- accepted payment asset;
- fee amount or pricing schedule;
- protocol/operator/subject allocation, if any;
- whether failed or unauthorized queries are charged;
- settlement and refund behavior;
- abuse and dispute handling.

Paid queries should be metered and auditable while query contents remain private where possible.

## Tinder example

A user chooses to connect a Tinder account to Human Bond and authorizes Tinder to request one claim:

```text
“Is this user currently a member of an active exclusive marriage-type Bond?”
```

Tinder pays the registry, receives a short-lived signed `true`, `false`, or `unknown` response, and verifies the proof. Tinder does not receive the partner’s identity or the Bond charter.

This is an example of a registry client, not a protocol-specific dependency. Other clients could query business-partnership, co-ownership, caregiving, or project-agreement claims under their own user-consent and policy rules.

## Non-goals

- no unrestricted people search;
- no sale of raw World ID data or nullifiers;
- no public relationship graph by default;
- no assumption that an active Bond proves fidelity, safety, compatibility, solvency, or legal marital status;
- no claim that an on-chain status is current beyond its stated block/time and expiry.
