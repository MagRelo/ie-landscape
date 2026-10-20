# Agent and x402 attribution

Referral/attribution for machine-to-machine payments. This is where LightForest's "Work for Agents" framing competes most directly: these projects move agent payments, LightForest publishes the terms agents work under and records the outcome.

### Split402
- **What:** referral commissions for x402-paid APIs. <https://github.com/split402protocol/splitx402>
- **Mechanism:** an agent attaches a signed referral claim to a normal x402 USDC payment; the merchant receives the gross payment; Split402 records commission liability (campaign bps, optional protocol fee as % of commission), verifies settlement on-chain, then pays accrued commissions later in batches from a merchant-controlled wallet. Its README says the MVP does **not** split the x402 payment atomically.
- **Traction:** none public.
- **vs referralTree:** single-level, deferred, off-chain ledger of liabilities; referralTree pays a multilevel chain atomically in one call with on-chain receipts.

### IETF AREF draft (draft-stone-aref-00)
- **What:** *Agent Referral and Escrow Framework*, individual Internet-Draft by B. Stone (SwarmSync.AI), published 2026-09-04, expires 2027-03-08, intended status Informational, not IETF-endorsed. <https://datatracker.ietf.org/doc/draft-stone-aref/>
- **Mechanism:** Ed25519-signed attribution proofs for referral chains of arbitrary depth; a `SwarmSync-Referrer` HTTP header binding a referrer to an escrow at hold time; commission vests only when escrow is RELEASED (not on enrollment); a unified settlement-finality signal across Stripe Connect and x402; `swarm_meta` JSON for propagating referral codes between agents.
- **Traction:** still at -00 as of 2026-10-12.
- **vs referralTree:** a protocol spec for the same problem space (multi-hop agent referral) with escrow-based vesting. referralTree has a deployed, audited contract and a fixed split rule; AREF leaves the split to the platform. Watch for -01 and adopters.

### x402 builder codes (ERC-8021) and PR #3666
- **What:** ERC-8021 "Transaction Attribution" appends a data suffix to calldata identifying the builder/app (Base Builder Codes: <https://docs.base.org/specifications/builder-codes/overview>; EIP text <https://eip.tools/eip/8021>). The x402 `builder-code` extension uses ERC-8021 Schema 2.
- **PR #3666** (<https://github.com/x402-foundation/x402/pull/3666>), merged 2026-10-06: adds facilitator-authored settlement metadata `m` to the builder-code extension: only the facilitator writes it (client-supplied `m` is ignored), keys prefixed `x402`, deterministic CBOR ≤ 65,535 bytes; TS and Go SDK support. No scheme emits metadata yet; a follow-up will move batch-settlement charge counts into `m.x402ChargeCounts`.
- **Traction:** x402 is a Coinbase-originated standard; adoption figures not verified here.
- **vs referralTree:** attribution *tagging* (who drove this tx), not payout. Complementary: an ERC-8021 code could be the evidence an oracle uses to sign `rewardRoots`, and facilitator metadata gives a trusted place to carry it.

### Related x402 affiliate experiments (not tracked in depth)
- x402aff (<https://github.com/MiroShark/x402aff>): routes x402 `payTo` to a per-builder 0xSplits contract (default 10% builder share).
- Toll402 bounty (<https://toll402.dev/bounty>): 30% of referred agent spend paid on-chain at settlement.
