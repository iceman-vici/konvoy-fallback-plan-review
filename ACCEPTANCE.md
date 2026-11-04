# Full 20-scenario acceptance mapping

Recorded evidence: **4 November 2026**. **All 20 acceptance rows remain OPEN.**

Passing synthetic assertions describe observed test coverage. They are not signed acceptance, fallback approval, release approval or payout authorization. Named reviewers/owners and acceptance dates remain unconfirmed. No scenario is marked accepted by this publication.

Mandatory open gates include atomic reservation **before** batch approval and through transfer/reconciliation; approval bound to recipient identity/version, exact amounts and destination/tax versions; stale-approval rejection after relevant changes without releasing uncertain transfers; and demonstrated refund invalidation through actual QR check-in. Manual registers cannot substitute for locking, replay protection or reconciliation safeguards.

| Scenario | Acceptance status | Executable coverage | Open gate / limitation |
|---|---|---|---|
| T01 Existing journeys | **OPEN** | Baseline 61 DB +15 gym +8 direct; upgraded 61 DB +15 gym +9 direct; 17 price checks; service refund checks. | Actual bank/wallet and physical admission rehearsal. Baseline refund assertion alone was report-state simulation; new refund evidence comes from upgraded services. |
| T02 Link/code rules | **OPEN** | Service precedence, tamper, invalid/cross-event tests; real portal and HTTP fallback. | Approve actual precedence/window and commercial interaction. |
| T03 Verified payment | **OPEN** | HTTP 30; real portal paid-credit flow; service upload/replay checks. | Staff verifies real receiving statements; synthetic receipt/confirmation is not bank verification. |
| T04 Resolver/recovery | **OPEN** | Real SQL timeout preserves purchase/raw intent; original-history recovery once; unprovable intent becomes assigned exception. | Named recovery owners and real operational escalation. |
| T05 Replay lifecycle | **OPEN** | Duplicate/concurrent approvals, immutable payment evidence, refund/dispute/restoration replays. | No external payment-provider webhook integration was added. |
| T06 Partial losses | **OPEN** | Money-only, exact unused quantity, cumulative limits, shared/disjoint allocation and won-dispute restoration. | Demonstrate refunded original QRs are rejected by actual check-in, exact capacity changes, preserved used history and replay safety. Finance must approve allocation/refund rules; bank refund execution remains manual. |
| T07 Frozen rules | **OPEN** | Immutable plans/lines, original recovery rules, early-bird/stack/cap tests and strict approval validation. | Actual rates/discounts/caps/minimums need approval. |
| T08 Event changes | **OPEN** | Postponement/reschedule eligibility holds; event/material fingerprint invalidation. | Finance/Marketing approve cancellation, replacement-material and buyer-support procedures. |
| T09 Corrections | **OPEN** | Append-only unpaid correction, replay and old-owner preservation; paid corrections held for independent review. | Complex paid/settled reassignment is an exception, not automatic entitlement movement. |
| T10 Permissions | **OPEN** | Partner isolation; support/private-data/export denials; distinct preparer/approver and tax verifier; no administrator-label bypass. | Provision real independent operators and approve access matrix. |
| T11 Reservations | **OPEN** | Synchronized real WP processes, one reservation winner, conservation, stale destination/tax approval invalidation. | Accept atomic reservation BEFORE approval through transfer/reconciliation, recipient/amount/destination version binding and invalidation after changes. Unknown transfers must remain reserved. Concurrency checks alone do not close this gate; safe retries may be needed. |
| T12 Unknown transfers | **OPEN** | Durable attempts, checksum export, row result isolation, duplicate references, unknown reservations and proven failure release. | No real bank submission or process-kill-at-bank-boundary test; accept unknown-outcome runbook before transfers. |
| T13 Destinations | **OPEN** | Password/TOTP replay protection, original trusted-contact preservation, independent recovery, unrelated-hold preservation. | Managed production key/MFA provisioning, recovery owners and real contact-alert delivery. |
| T14 Settlement | **OPEN** | Gross/tax/net, retained liability consumption, separate collector remittance, original minimum/debt, encrypted tax versions, exits/reopening/recovery. | Approve settlement/tax/exit policies; supervised first real settlement. |
| T15 Rebuild | **OPEN** | Immutable-source reconstruction, missing movement detection, repair once and replay; protected accounting reports. | Finance accepts real statement-to-ledger sign-off. |
| T16 Phone/QR | **OPEN** | Real 390px portal, ordinary direct/gym journeys, approved download and QR rendering, interface fixtures and screenshots. | Physical device sharing/scanning, actual bank-wallet QR, printed stock and lighting checks remain. |
| T17 Operations | **OPEN** | Bounded round-robin queue, assigned claim/due time, retry/recovery marker, flags, local restore and browser error checks. | Named primary/backup owners, monitored scheduler and external alerts delivery; simulated failures are not all possible crash points. |
| T18 Performance | **OPEN** | Local 24 sequential +4×8 concurrent service comparison, zero failures; existing tracking browser 324. | Increased concurrent p95 documented above; HTTP/enabled-referral/production capacity not established. |
| T19 Migration | **OPEN** | 17 restore checks;1.4→1.5 repeatable migration; original totals/states/hashes, QR/account snapshots and final 15-file preservation. | Production-specific fresh backup/restore and historical backfill dry run; never invent old referral entitlement. |
| T20 Materials/privacy | **OPEN** | Approval-only downloads, changed-event invalidation, encrypted private assets/tax, masked partner sales, private MFA/no-store retrieval and formula-safe CSV. | Approve actual packs/captions, terms/privacy, retention and secret-access ownership. |

## Evidence navigation

- [Recorded test evidence, limits and artifact links](EVIDENCE.md)
- [Sanitized assertion/result extracts](logs/README.md)
- [Source/export hashes](results/manifest.json)
- [Fallback scope, owners, dependencies and dates](README.md)

Implementation/test acceptance, fallback approval, production release authorization and approval of a specific payout batch are four separate decisions. This repository records none of those approvals.
