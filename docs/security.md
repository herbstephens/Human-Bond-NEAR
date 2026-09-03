# Security and privacy

## Required threat areas

- compromised participant wallet;
- compromised or malicious agent;
- forged or replayed World ID attestation;
- collusive work receipts;
- unauthorized charter amendment;
- treasury drain or distribution manipulation;
- oracle/evidence failure;
- cross-chain route failure;
- denial of service and storage abuse;
- private charter or work-evidence disclosure.

## Design requirements

- use commitments and selective disclosure instead of public personal data;
- separate identity verification from work verification;
- use explicit nonces, expiries, replay protection, and capability limits;
- require human or multisig authorization for consequential actions;
- implement dispute windows and emergency pause/recovery paths;
- publish an event and monitoring specification before mainnet;
- test agent replacement, relayer failure, and external settlement expiry.
