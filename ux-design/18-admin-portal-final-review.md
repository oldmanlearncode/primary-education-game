# 18 — Admin Portal UX Final Review
> 2026-11-27 · REVIEW DRAFT / awaiting user approval. All 12 low-fi screens remain approved (D-058…D-069); this review does not reopen approvals or finalize Phase 2/MVP.

## Evidence and limitations
Reviewed screen inventory 03, admin architecture 04, provisioning 05, specs 07–17, README and decision log. Inspected ten actual HTML files A-03…A-12 (A-12 V5); node --check passed all ten inline scripts. Static link inspection found six broken relative links in A-08/A-10/A-11 to A-03 and A-07 because files are split between directories. No full browser interaction regression, measured CLS, accessibility audit or live Figma inspection was performed in this review. A-01/02 approval and limitations are documented in inventory, not independently visually verified. No backend security claims.

## Findings and proposed backlog
| ID | Priority | Finding / proposed work |
|---|---|---|
| AFR-01 | P1 | Standardize common admin shell, terminology, status badges, fixed Eye action and confirmation/error states; preserve D-062/AW-21. |
| AFR-02 | P1 | Package approved HTML in one directory with working routes and a common index; A-08→A-09 handoff needs shared selected target/role draft; A-05→A-06 modal is intended production interaction, not independent account workflow. No claim of shared persistent demo state. |
| AFR-03 | P1 | Complete A-01 MFA/session/error variants and A-02 dashboard variants for the other three roles (inventory explicitly incomplete). |
| AFR-04 | P1 | Verify exact conditional permissions before implementation: list, counts, detail, actions and audit must all use scope/context. Preserve D-051; no automatic Super Admin content approval or child data access. |
| AFR-05 | P1 | Reconcile current documentation: admin architecture table still says Chưa for all 12; historical PROPOSED labels coexist with later approvals; A-12 header links original HTML instead of V5. Preserve dated history, make current status explicit. |
| AFR-06 | P2 | Standardize progressive disclosure (on-demand history/detail dialogs; audit preview plus full scoped history); proposed global rule, not yet confirmed. |
| AFR-07 | P1 | Browser regression: narrow viewport, keyboard/focus, dialogs, long Vietnamese labels, loading/error/selection, CLS; no blanket pass yet. |
| AFR-08 | P2 | Figma backlog A-03…A-12; A-01/02 variants; previous MCP limit documented, current quota not tested. |

## Cross-screen flow review
- A-01 → A-02 → A-03 → A-04 → A-07; partial send failure must preserve account; activate via E-09 (separate).
- A-03 → A-05 → A-06; state changes require reason/acknowledgement; offline sync policy OPEN. DISABLED/CLOSED separate workflow.
- A-08 → A-09; role diff, MFA, conflict, last Super Admin protection; admin lifecycle and recovery OPEN.
- A-10 scoped read-only audit across operations; A-11 recovery distinct from unlocking; full audit history must preserve filters and scope.
- A-12 V5 → P-13 parent correction status; question version vs learning evidence amendment distinct; future scope not MVP. A-12 review/serving state separated; actual recomputation not implemented.

## Open decision gates
Before detailed implementation: conditional authorization policies, last Super Admin bootstrap/recovery, admin MFA recovery, parent self-service password reset, offline/active child session behavior, audit retention/redaction/export, admin invitation/state policy, content quarantine/severity/batch correction, learning amendments and notification policies. A-12 FUTURE requires separate scope decision; EC-03 confirmed correction obligation must have a viable operational path even if A-12 not MVP. Do not infer policies from mock fixtures.

## New proposals (PROPOSED)
- AFR-D01: Standardize common Admin UI patterns and progressive disclosure; propose generalizing on-demand detail/history across product when appropriate.
- AFR-D02: Consolidated prototype package and cross-screen regression before Admin UX handoff.
- AFR-D03: Maintain a current-status register separate from historical review notes and prioritize security/business policy gates before backend.
- AFR-D04: Figma sync and accessibility/layout QA backlog; no premature full Phase 2 completion.

## Handoff gate
12/12 approved layouts, but consolidated prototype and review findings remain OPEN. No product code or approved decision changed. Next: user review of priorities and proposals, then remediation and remaining product UX screens.
