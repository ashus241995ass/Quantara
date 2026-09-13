# Quantara Phases 1–5 Blocker Matrix — Rechecked

Date: 2026-09-13

This public copy contains status and remediation guidance only. Credentials, customer data, restricted source documents, private URLs, license keys, environment files, generated reports, and release artifacts are excluded.

Status: ~~completed~~ = resolved by in-repo fix and recheck; **OPEN** = still requires external evidence or source-data remediation.

| Phase | Blocker | Reason | Solution | Resolution steps |
|---|---|---|---|---|
| Phase 1 | **OPEN — GitHub Actions access** | Remote workflow access was not previously evidenced. | Authenticate the correct repository and run CI. | Confirm repo; reauthorize GitHub; run workflow; retain URL/artifacts. |
| Phase 1 | **OPEN — Client-owned session and entitlement state** | Browser storage is not the server source of truth; tenant ownership is incomplete. | Make authenticated server records authoritative. | Add tenant ownership/RLS; stop trusting local flags; add cross-user tests. |
| Phase 2 | **OPEN — Financial provenance acceptance** | 19 active default assumptions lack independent metadata; no curated cost-head rows are loaded. | Load reviewed official source metadata and cost heads. | Load IDs/hashes/dates/reviewers; run strict provenance; rerun DPR/CMA smoke. |
| Phase 3 | **OPEN — Production migration verification** | Local migrations 24–35 replayed; staging/production evidence is absent. | Replay and validate migrations in staging and production. | Back up; apply 24–35; check parity; run API/PDF/licensing smoke; retain rollback evidence. |
| Phase 3 | **OPEN — Individual entitlement** | Server status/token/download checks exist, but individual account binding and live verification are incomplete. | Bind paid orders to authenticated users and exact reports. | Verify individual role; test paid/unpaid downloads; test expiry, reuse, cross-user access. |
| Phase 3 | ~~Purchase endpoint abuse throttling~~ | DB-backed IP/email rate limiting and paid-order idempotency are implemented. | Keep the bounded rate and verify in staging. | Set PAYMENT_RATE_LIMIT_PER_MIN; confirm 429; monitor replay behavior. |
| Phase 3 | **OPEN — Local runtime deployment checks** | Docker and PostgreSQL CLIs are unavailable on this host. | Run full checks on CI or a Docker/PostgreSQL host. | Build image; initialize disposable DB; apply migrations/data; run authenticated smoke. |
| Phase 4 | **OPEN — Payment provider configuration** | Provider credentials, webhook secret, and HTTPS webhook are not configured. | Configure Stripe or Razorpay securely. | Set provider secrets/URLs; register webhook; confirm no secret logging. |
| Phase 4 | ~~Customer license delivery/retrieval~~ | One-use hashed completion token and status flow are implemented. | Use the completion flow or connect production mail delivery. | Run sandbox payment; confirm status; consume token once; test replay/wrong token. |
| Phase 4 | **OPEN — Individual payment completion** | Payment/resource storage and checks exist, but live account binding and settlement are unverified. | Complete server-authorized individual entitlement. | Bind user/report; enforce exact document; add refund/expiry tests. |
| Phase 4 | **OPEN — Live provider behavior** | No provider sandbox success, replay, signature, amount, failure, or refund suite is evidenced. | Run the provider acceptance suite. | Test success, duplicate, invalid signature, amount mismatch, failure, refund; retain logs. |
| Phase 5 | **OPEN — Overall recommendation accuracy** | Fresh 115-case run is 75.15%; 62 scenarios failed versus 90% required. | Remediate reviewed mappings and rules. | Group failures; fix approved causes; add regressions; rerun gate. |
| Phase 5 | **OPEN — Central scheme mapping** | Central accuracy is 58.67%, below 90%. | Correct reviewed taxonomy/ranking mappings. | Verify official applicability; update mappings; rerun central cases. |
| Phase 5 | **OPEN — State-scheme mapping** | State accuracy is 74.78%, below 90%; 35 mapping issues remain. | Verify state/district mappings and ranking. | Review affected cases; update approved data; rerun state cases. |
| Phase 5 | **OPEN — Subsidy accuracy and unknown IDs** | Subsidy accuracy is 61.74%; unresolved IDs can skip or miscalculate benefits. | Complete canonical scheme-ID mapping and official subsidy review. | Inventory skips; map IDs; validate caps/stacking; fail unresolved IDs; rerun. |
| Phase 5 | **OPEN — Eligibility rule coverage** | 63 cases record rule issues despite a 100% binary aggregate. | Reconcile expectations with approved rules. | Separate engine defects from expectation defects; add boundary tests; obtain review. |
| Phase 5 | ~~Bank product matching semantics~~ | Fresh bank accuracy is 87.83%, above the 85% threshold. | Monitor residual product/institution mismatches. | Preserve product-level ground truth; add follow-up regression cases. |
| Phase 5 | ~~Stale alpha dashboard~~ | Full 115-case validation regenerated the dashboard on 2026-09-13. | Regenerate after approved data changes. | Record database/source versions; rerun the enforced gate. |
| Phase 5 | **OPEN — Enforced CI gate** | Overall, central, state, and subsidy thresholds still fail. | Keep enforcement enabled and clear underlying data blockers. | Do not bypass; remediate; regenerate; pass all thresholds; rerun CI. |

## Recheck summary

Completed in the latest pass: payment-order throttling, one-use payment completion, alpha dry-run compatibility, local migration replay, current 115-case dashboard generation, and the bank threshold. Remaining blockers are marked OPEN above.
