# Partner program v2 — local implementation evidence

Date: **4 November 2026**. Recorded synthetic local verification only. **Implementation/test acceptance, fallback approval, release authorization and payout authorization remain OPEN and separate.** See the [fallback plan and historical baseline summary](README.md). Local implementation claims below are not live capabilities.

Application repository: [iceman-vici/konvoy](https://github.com/iceman-vici/konvoy); branch `main` remains at
`a53817a906dc6b6913aaeb651689fb4b2ac4297a`, with uncommitted local implementation.
No application Git staging, commit or push; no production configuration change or real transfer. Documentation-only commits in this review repository are separate.

## Isolation and preservation

Tests used a disposable local WordPress/MariaDB environment, separate from live and the user's existing preview. Outbound HTTP/mail were blocked. The existing preview was not seeded/reset; its recorded schema was 1.4.0 with zero orders and one inactive gym.

All 15 pre-existing changed files retained their recorded hashes; no application files were staged. See [preservation result](results/preservation.json). Live inspection was read-only; schema1.4.0 plus manual fixes is not one clean Git release.

**Public export boundary:** only reviewed assertion/result extracts, aggregate numeric results and hashes are published. Full raw logs, credentials, tokens, SQL backups, receiving/payout details and screenshots are excluded. These extracts are not a complete reproducible source package or an independently witnessed acceptance run. No tests were rerun to create this publication.

## Completed executable checks

Executable names below refer to the local application test suite. They are identifiers, not published source links. Every log link points to a sanitized result extract in this repository.

| Evidence | Result | Executable / log |
|---|---:|---|
| Existing gym/pricing/database workflow before behavior changes | 61 passed | `tests/partners.integration.py`; [results](logs/baseline-integration.log) |
| Existing gym journey in real WordPress before behavior changes | 15 passed | `tests/partners.wordpress.browser.mjs`; [results](logs/baseline-browser.log) |
| Existing direct-public journey before behavior changes | 8 passed | `tests/program.baseline.browser.mjs`; [results](logs/direct-baseline-browser.log) |
| Upgraded core HTTP checkout/payment safety, final source | 30 passed | `tests/program.integration.py`; [results](logs/program-integration.log) |
| Upgraded existing gym/database/pricing regression | 61 passed | `tests/partners.integration.py`; [results](logs/upgrade-partners-integration.log) |
| Upgraded gym journey in real WordPress | 15 passed | `tests/partners.wordpress.browser.mjs`; [results](logs/upgrade-gym-browser.log) |
| Upgraded direct-public saved payment journey | 9 passed | `tests/program.wordpress.browser.mjs`; [results](logs/upgrade-direct-browser.log) |
| Real private invitation, login, terms, enrollment, share QR, paid-credit recovery, private tax review and exit | 29 passed | `tests/program.portal.wordpress.browser.mjs`; [results](logs/program-portal-browser.log) |
| Program database services, final source | 183 passed | `tests/program.services.php`; [results](logs/program-services.log) |
| Concrete TOTP/crypto/strict commercial rules, final source | 49 passed | `tests/program.crypto.php`; [results](logs/program-crypto.log) |
| Checkout/payment interface fixtures | 26 passed | `tests/program.checkout.browser.mjs`; [results](logs/program.checkout.browser.mjs.log) |
| Partner/admin interface fixtures | 81 passed | `tests/program.browser.mjs`; [results](logs/program.browser.mjs.log) |
| Existing partner interface fixtures | 49 passed | `tests/partners.browser.mjs`; [results](logs/partners.browser.mjs.log) |
| Existing gym unit assertions | 53 passed | `tests/partners.php`; [results](logs/partners.php.log) |
| Early-bird boundaries | 17 passed | `tests/pricing.php`; [results](logs/pricing.php.log) |
| Existing tracking assertions | 114 passed | `tests/tracking.php`; [results](logs/tracking.php.log) |
| Automatic six-platform attribution assertions | 588 passed | `tests/automatic-referrals.php`; [results](logs/automatic-referrals.php.log) |
| Tracking JavaScript unit tests | 16 passed | `tests/tracking.test.mjs`; [results](logs/tracking.test.mjs.log) |
| Tracking browser regression, actual PHP/SQLite, desktop/mobile | 324 passed | `tests/tracking.browser.mjs`; [results](logs/tracking.browser.mjs.log) |
| Exact amounts and Unicode reference replay normalization | 22 passed | `tests/program.payments.php`; [results](logs/program-payments.log) |
| Shared Vite CSS import traversal and final manifest entries | Passed | `tests/program.assets.php`; [results](logs/program-assets.log) |
| Backup restoration, migration and bounded performance | 17 passed | `tests/program.restore.py`; [results](logs/program-performance.log) |
| Final PHP syntax | 144 files passed | [results](logs/php-lint.log) |

Service checks include encrypted tax records, explicit exits, extended reports,
retained-fee settlement, synthetic remittance-confirmation evidence, recovery debt and simultaneous
payout reservation. Settings-mutating suites ran serially. The final receipt
rejection/cancellation fixes were followed by the 30-check HTTP run and a rerun
of the 61-check existing gym/database suite. Earlier browser runs remain valid
evidence of their exercised paths; they were not all repeated after unrelated
last edits. No aggregation of assertion counts establishes that all 20 acceptance
scenarios or human operating procedures have been accepted.

## Implemented local controls

These controls are in the local upgrade, **not on live**. They extend the existing
gym directory, authentication, booking QR, checkout, receipt review and tickets.
The local module contract documents supported actions, configuration and permissions; it is not part of this documentation-only publication.

| Area | Enforced local behavior |
|---|---|
| Partner access | Bound, expiring, one-time invitations; partner accepts current terms; event enrollment and private partner-scoped portal. |
| Sharing/materials | Stable legacy gym booking routing is preserved; optional referral code/token has separately approved precedence. Only approved, versioned static packs are available. Event changes invalidate materials. AI is deferred. |
| Payment truth | Book first; freeze receiving options and QR bytes; receipt alone earns nothing. Staff confirms actual received amount, currency, original receiver and unique bank reference. Payment, proof review and tickets commit atomically. |
| Commission | Original approved line rates, discount interaction, acquisition cap and eligibility rules freeze at booking. Immutable movements preserve pending, eligible, reserved, paid, held and recovery history. Unconfigured rules remain unconfigured. |
| Refunds/disputes | Stable operation and allocation keys prevent replay/overlap deductions. Money-only refunds preserve admission; quantity/full unused-ticket refunds void the correct unused tickets and release capacity once. Used history and prior paid payouts remain recorded. Recording a confirmed refund requires external evidence; the app does not send the bank refund. |
| Retained fees/remittance | Referrer, ticket-money receiver and payout destination remain independent. Verified retention consumes commission liability once. Gym-held proceeds otherwise stay blocked until evidenced approved reconciliation/remittance; the same retained fee cannot also enter a cash payout. |
| Payout approval | Atomic reservation; different preparer/approver even with multiple roles; approval binds exact amounts, destination/tax versions and export checksum. Exports are not payment. Durable row attempts and unique bank evidence protect manual transfer confirmation. Unknown results remain reserved. |
| Private readiness | Encrypted, versioned payout and tax details; recent password plus TOTP for sensitive Finance access; distinct verification; destination/contact changes hold payment and invalidate stale approvals. Support and partners cannot inspect others' private records. |
| Reconciliation/exit | Rebuild from original financial events; assigned exceptions and missing-credit claims; protected reports/CSV; exact gross/tax/net settlement; explicit exit and incoming debt recovery preserve history. Late original transactions reopen settlement without allowing new referrals. |

All five flags—portal, attribution, earnings, payouts and materials—are currently
**off** in disposable staging. Test users, program records and events created by
the service suite were removed: [cleanup extract](logs/program-cleanup.log).
No commercial rate, destination, tax interpretation or real-money policy was activated.

## What the HTTP evidence establishes

The actual HTTP tests show that buyer-supplied internal flags cannot issue
tickets; receipt upload alone produces neither verified money nor commission;
staff must explicitly confirm the exact amount, currency, saved receiving account
and bank reference; reused bank evidence leaves proof/order/tickets unchanged;
failed offsite verification rolls back the new order and capacity; concurrent
approval issues one admission and sends one privacy-safe paid event; optional
projection final-write failure leaves verified payment and its durable recovery
marker committed. Public receiving options and original QR bytes remain frozen.
Receipt-review write failure leaves both proof and order awaiting review;
capacity-release failure leaves the order and held seats intact; concurrent
cancellations report one winner and release one reservation. A paid order cannot
be cancelled through the unpaid-order endpoint.

An independent code review caught and corrected four core defects: a missing
notification variable, premature savepoint release, mutable bank-label replay
identity and unchecked payment-selection transaction results. It also caught
destination recovery clearing unrelated holds, transfer-reference formatting
replay and plan-window readiness inconsistencies in the optional module. A fixed
commission above discounted revenue now fails the explicit approved acquisition
cap rather than silently reducing the agreed fee; historical recovery follows
the same rule and assigns an exception.

An actual simultaneous-process test found a repeatable-read snapshot defect in
payout reservation. Balance reads now use current locking reads. The final test
produced exactly one 16,000-centavo reservation and one 409 refusal, with exact
liability conservation; cancelling the winner restored the original eligible
balance. Safe transaction conflicts can still return a retryable failure.

The bank-reference identity deliberately ignores mutable bank labels and
normalizes case/Unicode formatting. Identical account numbers and references in
different banks may be conservatively blocked for Finance review; there is no
silent bypass to accept ambiguous duplicate evidence.

Real WordPress browser testing additionally exposed missing transitive Vite CSS.
The loader now collects styles from static imported chunks; the native scoped
checkbox remains visible and user-operable. Fixture tests alone had not exposed
this integration issue.

## Restoration and performance limits

The rehearsal restores frozen1.4 application/SQL backups into a **new** disposable
database; restores synthetic upload files byte for byte; applies schema1.5;
compares original order/ticket/gym/proof totals, states and hashes; repeats the
migration; then exports/restores the upgraded SQL and compares again. It drops
only its rehearsal database and copied directory. Primary staging remains intact.

Identical ordinary bank checkout workloads, with2 warmups excluded:

| Warm service latency | Frozen1.4 | Current1.5 |
|---|---:|---:|
| 24 sequential orders, p50 / p95 | 1.536 / 2.305ms | 1.689 / 2.077ms |
| 4 concurrent workers ×8 orders, p50 / p95 | 3.928 / 29.135ms | 6.067 / 60.211ms |

No workload failures; exact counts, charged amounts, reservations and cleanup
passed. The concurrent p95 increased. These figures exclude WordPress/CLI
startup, HTTP/auth/rate limits, approved-referral traffic and external mail.
They do not establish production throughput or a production load ceiling.

## Remaining acceptance gates

- **Open, including for the fallback:** accept demonstrated atomic reservation
  before batch approval and through transfer/reconciliation; exact recipient,
  amount and destination-version binding; invalidation after relevant changes;
  no release/retry of an uncertain transfer; replay-safe settlement and
  authoritative reconciliation. Manual registers/checklists alone are insufficient.
- **Refund acceptance remains open:** demonstrate that affected original ticket
  QRs are refused by the actual check-in path under the approved refund policy,
  with exact capacity handling, used-history preservation and replay protection.
  Existing service assertions and manual refund records do not alone close this
  end-to-end acceptance gate.
- These open gates imply **no payout, scope reduction or pilot/release approval**.
- Physical phone/bank-wallet QR tests, printed stock readability, named operating
  owners, Finance/Marketing sign-off and a supervised first real settlement remain
  human acceptance gates. No real funds or messages were used by these tests.
- All real rates, tax requirements, commercial rules, settlement timing, terms,
  retention and payout permissions require explicit approval/configuration.
  Money feature flags remain off by default.
- Before any separately authorized rollout, create the `/partner/` WordPress
  page using **Private Partner Program** template, check for an existing slug
  collision, provision managed encryption/MFA, assign independent operators and
  rehearse the deployment-specific backups. Existing `/partners/` stays separate.

## Full acceptance mapping and result artifacts

- [All 20 scenarios — every acceptance gate OPEN](ACCEPTANCE.md)
- [Sanitized assertion/result index](logs/README.md)
- [HTTP result](results/program-integration-result.json)
- [Real portal browser result](results/program-portal-wordpress-result.json)
- [Restore/performance result](results/restore-performance.json)
- [Original/export log hashes and provenance](results/manifest.json)

All five program flags were restored off. No real financial operations, external messages or deployments were performed. The earlier discovery dates are not current release commitments. See the fallback plan for unconfirmed owners, dependencies and dates.
