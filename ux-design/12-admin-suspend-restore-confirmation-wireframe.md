# 12 — A-06 Suspend / Restore Confirmation: UX Wireframe

> **Phase 2 — 2026-11-24 · ✅ HTML LOW-FI APPROVED — AW-22…AW-25 CONFIRMED**  
> A-06 is an explicit **confirmation interaction for actions initiated at A-05**, not a new full administrator workflow. Local interactive demo: `A-06-suspend-restore-confirmation.html` (conversation file). **Figma frame NOT CREATED**; no real backend, authorization or audit persistence.

## 1. Established decisions, not reopened

- **ADM Permission Matrix / D-051:** `SUPER_ADMIN` and `ACCOUNT_ADMIN` can suspend/reactivate parents (subject to regular scope/context/security); `CONTENT_REVIEWER` and `SUPPORT_OPERATOR` cannot.
- **AD-04:** concurrent edits require conflict handling. **AD-05:** preserve child learning progress and checkpoint-safe session termination, implementation details **OPEN**.
- **AD-10:** revoked admin privileges must be revalidated during action submission.
- **AD-11:** mistaken suspension should be reversible with reason/audit.
- **AW-14 / D-061:** A-05 dangerous actions require confirmation and mandatory reason — **CONFIRMED**.
- **AW-16 / D-061:** `DISABLED` and `CLOSED` are **not** directly restored on A-05; separate authorized workflow required.
- **D-062 / UX-GLOBAL-01:** avoid unexpected layout shift throughout the project.

## 2. User journey

```text
A-05 Parent Account Detail
    ├─ ACTIVE / PENDING_ACTIVATION → Suspend action → A-06 confirmation
    ├─ SUSPENDED → Restore action → A-06 confirmation
    └─ DISABLED / CLOSED → no immediate restore; separate workflow

A-06:
  1. Show target email, account ID, original → target status.
  2. Warn if child session active / device offline.
  3. Require nonempty substantive reason (demo min length 8).
  4. Require acknowledge checkbox that account/impact was reviewed (PROPOSED).
  5. On confirm, revalidate role/scope/status/session and record version at server.
  6. If authorized + safe, transition state and add audit record; otherwise block with actionable message.
  7. Return to updated A-05 details or remain on confirmation when correction needed.
```

## 3. A-06 wireframe layout

A compact account summary and dedicated confirmation panel within the existing Admin shell; side explanatory checklist for security. The browser demo presents the confirmation as a **modal** with stable spacing and an action-specific confirm label. For a production integration, the action may be a modal/dialog within A-05, not necessarily a routed page (screen ID A-06 refers to the UX state).

### Required inputs
- Target identity **read-only**.
- Current account status → action target status **read-only**.
- **Reason** required; logged on successful update; never auto-fill sensitive information.
- **Impact acknowledgement checkbox** (new UX proposal).
- Cancel and Confirm controls with stable dimensions.

### Behavioral matrix

| Case | UI outcome | Backend requirement |
|---|---|---|
| ACTIVE → Suspend | Confirm with reason; warn active session | Preserve progress, checkpoint-safe termination |
| PENDING_ACTIVATION → Suspend | Confirm; prevent activation while suspended | Re-check invitation and account state |
| SUSPENDED → Restore | Confirm with reason; update account to ACTIVE if authorized | Validate policy and audit |
| DISABLED / CLOSED | No immediate Restore | Separate workflow (AW-16 already confirmed) |
| SUPPORT_OPERATOR / CONTENT_REVIEWER | Suspend/restore denied | Enforce permission and scope server-side |
| Permission revoked after modal opened | Reject and explain | Revalidate role at commit time |
| Another Admin updated account | Conflict; refresh and retry | Optimistic concurrency/version check |
| Network result uncertain | No blind retry | Query status/idempotency before re-submit |
| Child in an active learning session | Show checkpoint warning | Safe end-of-session policy |
| Child device offline/un-synced | Demo blocks immediate suspend; notes **policy OPEN** | Requires explicit offline/risk policy |

## 4. Demo coverage and limitations

User can choose account states, admin roles and scenarios (normal, active child session, permission revoked, concurrent change, uncertain network outcome and offline unsynced session). Confirm modal includes mandatory reason and acknowledgement, role-sensitive enabled actions, mock audit entries, and stable-sized controls. HTML has no API, storage or token operations. **Mock role gating is not production authorization.**

The demo takes a **conservative illustrative choice** to block when offline data is unsynced. **This is not a confirmed product rule:** precise offline suspension semantics remain OPEN under AD-05.

## 5. Approved UX decisions — CONFIRMED (2026-11-24)

| ID | Proposal | Status |
|---|---|---|
| **AW-22** | A-06 is a dedicated **modal confirmation state reachable from A-05**, with an unambiguous account target, state transition and reason field; no unnecessary page navigation in production. | **CONFIRMED** |
| **AW-23** | In addition to mandatory reason, require an explicit **“I checked the correct account and understand the impact”** acknowledgement. | **CONFIRMED** |
| **AW-24** | Provide distinct feedback for **permission revoked / concurrent update / uncertain network result**, with safe recovery instead of auto-retrying. | **CONFIRMED** UI (underlying AD-04/AD-10 CONFIRMED) |
| **AW-25** | When a child session is active or offline, show **checkpoint/sync risk warning** and prevent implying immediate safe termination; offline resolution strategy stays OPEN. | **CONFIRMED** UI (underlying AD-05 CONFIRMED) |

## 6. Existing approval states

- **A-01/A-02:** Figma low-fi approved.
- **A-03/A-04/A-05:** HTML low-fi approved; Figma frames not created.
- **A-06:** **HTML low-fi APPROVED**, Figma frame not created.
- **A-07:** **HTML low-fi APPROVED** by the user's later explicit approval; **AW-17…AW-20 CONFIRMED**. The earlier limited approval of Layout Shift corrections was superseded by a full A-07 UX approval.
- Global layout stability **D-062 + AW-21** confirmed.

## 7. Links

- [A-05 — Parent Account Detail](./09-admin-parent-account-detail-wireframe.md)
- [A-07 — Invitation Management](./10-admin-invitation-management-wireframe.md)
- [Admin Portal & permissions](./04-admin-portal.md)
- [Global layout-stability guideline](./11-global-layout-stability-guidelines.md)
- [Decision log](../idea-summarize/06-decisions-and-open-questions.md)


## 8. Final approval record — 2026-11-24

**D-064 / AW-APP-06 — CONFIRMED:** User explicitly approves **all A-06 HTML wireframe and AW-22…AW-25**. A-06 will remain a confirmation/modal state within A-05; account identity and state are explicit; reason and acknowledgement required; separate feedback for permission/concurrency/network; warnings for active/offline child sessions. **Precise policy for offline unsynced child progress remains OPEN**—confirmation of the warning UX does not mean the illustrative demo blocking behavior is product policy.

**Not implemented:** Figma A-06, production server permissions, locking, session protection or audit persistence.
