# Konvoy fallback plan — review copy

**4 November 2026 — proposed scope; not approved for release or payouts**

## 1. Scope and current status

The fallback reuses the existing gym/direct-public booking, booking QR, reservation, receipt review and ticket-issuance flows. The proposed operational pilot covers one event and 5–10 invited partners.

It does not waive the v2 financial safeguards or replace them with spreadsheets or manual registers. AI generation, automatic posting and payout-provider APIs remain deferred.

The new partner portal and financial controls have been implemented and tested locally. They are uncommitted and undeployed; all five program switches remain off. Local implementation is not implementation acceptance, fallback approval or release approval. This repository publishes documentation only; it does not publish or deploy the application changes.

## 2. Mandatory financial gates — OPEN

**Payout reservation and approval**

- Funds must be reserved atomically **before batch approval**. Simultaneous batches cannot reserve the same entitlement.
- Reservations persist through approval, export, transfer and reconciliation. Confirmed settlement consumes the reservation once.
- Independent approval binds the exact recipient identity/version, source entitlements, gross/withholding/net amounts, destination and tax versions, and export checksum.
- Relevant changes invalidate approval and prevent stale instructions from being used.
- Approval invalidation must not release an in-flight or uncertain transfer. Unknown transfers remain reserved; they cannot be retried without authoritative resolution. Release requires evidence that the transfer was unsent, definitively failed or safely cancelled.

**Refund acceptance**

Demonstrate that affected original ticket QRs are refused by the actual check-in path under the approved refund policy. Evidence must also show correct capacity handling, preserved used-ticket history and replay without additional deduction or seat release. A refund record or order-status edit alone is insufficient.

**Settlement and reconciliation**

Keep three identities separate: referring partner, ticket-money receiver and commission payout destination. Approved fees retained by a gym must settle the corresponding liability once and cannot also enter a cash payout.

Reconcile orders/refunds, receiving-account statements/remittances and commission/payout records. Assign every mismatch to an owner and hold affected payouts.

Manual records support these controls; they do not establish application locking, replay protection or reconciliation safeguards.

## 3. Owners and dependencies

Named operational owners have **not been confirmed**. Ivan is a requested reviewer; this document does not assign him approval authority.

| Responsibility | Required owner | Dependency |
|---|---|---|
| Build, staging and defect evidence | Engineering lead — name unconfirmed | Reviewable source and reproducible test package |
| Independent acceptance | QA lead — name unconfirmed | Witnessed journeys and all 20 scenario results |
| Rates, retained fees, refunds, tax and settlement | Finance owner — name unconfirmed | Written approved commercial rules |
| Batch preparation | Authorized preparer — name unconfirmed | Verified eligibility and atomic reservations |
| Batch approval | Different authorized approver — name unconfirmed | Exact version-bound batch review |
| Transfers and statement matching | Authorized Finance operators — names unconfirmed | Bank evidence and unknown-result procedure |
| Materials and partner communications | Marketing/partner-operations owners — names unconfirmed | Approved packs, terms and partner enrollment |
| Recovery, alerts, backups and access | Operations/security owners and backups — names unconfirmed | Managed keys/MFA, monitoring and restore rehearsal |
| Production release | Release authority — name unconfirmed | Separate acceptance and deployment authorization |

No real commercial defaults are approved. Rates, discounts, attribution rules, settlement treatment, refund/debt/exit rules, timing/minimums, tax, terms/privacy and retention remain dependencies.

## 4. Dates

- **4 November 2026:** live baseline recorded and local test evidence produced.
- **12 November 2026:** earlier conditional fallback-pilot estimate; **not a confirmed or approved launch date**.
- **28 November 2026, 5–10 p.m. Philippine time:** reported KONVOY 04 event at NUSTAR Grand Ballroom. This is not a software acceptance deadline or permission to bypass gates.
- **Acceptance review, fallback pilot, production rollout and first settlement:** dates remain **unconfirmed**, pending named owners, evidence review and dependencies above.

The earlier full-v2 January–March planning windows were discovery estimates, not current release commitments. No revised launch date is promised here.

## 5. Evidence available and its limits

Repository: https://github.com/iceman-vici/konvoy  
Baseline main commit: `a53817a906dc6b6913aaeb651689fb4b2ac4297a`

**Recorded live baseline:** schema 1.4.0 plus manual patches; ten audited gym/payment source files matched the frozen baseline. This does not establish that every live file matches one Git commit. No new program deployment occurred.

**Recorded synthetic test results:**

| Evidence | Result |
|---|---:|
| Existing baseline database/gym/direct journeys | 61 / 15 / 8 checks passed |
| Upgraded database/gym/direct journeys | 61 / 15 / 9 checks passed |
| Partner and financial services | 183 checks passed |
| Security and commercial-rule checks | 49 checks passed |
| Payment HTTP safeguards | 30 checks passed |
| Real WordPress private-portal browser journey | 29 checks passed |
| Partner/admin interface fixtures | 81 checks passed |
| Restoration and migration rehearsal | 17 checks passed |

The simultaneous payout test produced one 16,000-centavo reservation and one refusal, with exact balance conservation. HTTP tests demonstrated approval replay protection and rollback after receipt-review or capacity-release failures.

All tests used disposable local environments and synthetic evidence. No real bank refund, transfer, statement reconciliation or external notification delivery was exercised. Refund rejection through actual QR check-in remains an open acceptance gate.

Bounded performance testing completed without failures, but concurrent service p95 increased from approximately 29 ms to 60 ms. It does not establish production capacity.

The raw logs, screenshots and full 20-scenario mapping currently remain local. The counts above are a review summary, not a substitute for an accessible evidence package or witnessed acceptance.

## 6. Separate decisions

1. **Implementation/test acceptance:** review source, demonstrations, failures/recovery and the 20 scenarios; explicitly close or retain each gate.
2. **Fallback approval:** separately approve its exact scope, named owners, dependencies, procedures and dates.
3. **Production release authorization:** separately authorize the reviewed deployment and rollback plan.
4. **Payout authorization:** separately approve a specific eligible, reserved, independently reviewed batch.

None of these decisions is implied by another, by this document, or by passing test counts. **No payout, scope reduction or release approval is granted.**
