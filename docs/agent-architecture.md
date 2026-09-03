# Human Bond agents on NEAR

## Purpose

Agents are the coordination interface for agreements. They make it easier for humans to state what they want, compare terms, negotiate, understand obligations, and operate an agreement over time.

## Capabilities

- capture participant intent;
- draft and explain charter terms;
- negotiate with other participants’ agents within bounded constraints;
- prepare signed settlement proposals;
- monitor deadlines, milestones, and policy conditions;
- request human approval for consequential actions.

## Prohibitions

Agents may not:

- claim proof of humanity;
- unilaterally add or remove members;
- change a charter;
- release treasury funds outside the authorized policy;
- make an irreversible external-chain transaction without an approved obligation;
- expose private charter or evidence data.

## Security model

Use NEAR agent contracts and, where appropriate, Shade Agent attestations/TEE execution. Agent identities must be whitelisted or attested, rate-limited, revocable, and replaceable. Multiple independent agent instances should be supported for liveness and provider diversity.
