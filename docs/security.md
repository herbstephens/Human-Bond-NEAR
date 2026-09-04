# Security and privacy

## Required threat areas

- compromised participant wallet;
- compromised or malicious Partner Agent or Partnership Agent;
- forged or replayed World ID attestation;
- unauthorized or overbroad registry queries;
- consent forgery, replay, or revocation failure;
- relationship-graph enumeration through query patterns;
- unauthorized charter amendment;
- unauthorized treasury spending, savings transfer, or investment allocation;
- false institutional or legal-status claims;
- treasury drain or distribution manipulation;
- oracle/evidence failure;
- cross-chain route failure;
- denial of service and storage abuse;
- private charter, relationship, or query-history disclosure;
- payment abuse, query flooding, and third-party response resale;
- inference of undisclosed relationship status from `false` responses or query behavior.

## Design requirements

- use commitments and selective disclosure instead of public personal data;
- separate identity verification from any external work-verification system;
- use explicit consent, claim scope, nonces, expiries, replay protection, and capability limits;
- return minimal signed claims and default to `unknown` when authorization is absent or ambiguous;
- prevent query enumeration through rate limits, batching controls, privacy-preserving proofs, and query confidentiality;
- require human or multisig authorization for consequential actions;
- implement dispute windows and emergency pause/recovery paths;
- publish an event and monitoring specification before mainnet;
- test agent replacement, relayer failure, and external settlement expiry.
