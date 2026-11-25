# 15 — A-10 Admin Audit History: UX Wireframe & Interactions

> **2026-11-25 · HTML LOW-FI DRAFT / AWAITING USER REVIEW**  
> Interactive HTML supplied in conversation as `A-10-admin-audit-history.html`. **No Figma A-10 frame created, no backend audit/log access, no product code.** Demo has entirely synthetic records.

## 1. Confirmed foundations

- **ADM-03 / AD-03:** audit actions that create, suspend, restore accounts or change permissions, including actor/time/target; reason for sensitive operations already approved in A-05…A-09.
- **D-051 permission matrix:** **all four Admin roles have conditional `🔒` audit access**, **not unconditional access**. Server checks authorization, resource scope and context before every query and event detail.
- **AD-08:** Support Operator restricted to authorized ticket/resource scope.
- **D-062 / AW-21:** proactive prevention of unexpected Layout Shift with stable columns, icon buttons and selected-row styling.
- **ADM-D04:** managing Admin accounts/roles is Super Admin-only, but **viewing audit is a distinct conditional permission**; Super Admin role alone does not justify inspecting children’s sensitive learning records.
- **D-066 / A-09:** role change records need reason/actor/diff and failure feedback; exact backend persistence remains future implementation.

## 2. A-10 information architecture — PROPOSED

```text
Admin shell
  A-10 Admin Audit History [READ ONLY]
  ├─ Permission-aware summary cards (Total, Success, Denied, Failed)
  ├─ Search: actor / target / event ID / request ID
  ├─ Filters: Action / Outcome / From-Date / To-Date / Clear
  ├─ Stable-width audit table: Time / Actor / Action+Target / Outcome / Eye
  │  └─ Pagination (5 entries/page in demo)
  ├─ Selected Event Detail
  │  ├─ eventId, timestamp, actor, action, target, result, requestId
  │  ├─ reason, optional ticket
  │  └─ before/after metadata, sanitized
  ├─ Security explanation & access-denied / network states
  └─ UX Test Lab: simulated role + resource scope + fault
```

**No edit/delete buttons**, because audit is for investigation, not modification. No secret/token values; content must be redacted/field-filtered server-side. Details and list must share the **same** authorization/scope policy.

## 3. Filters, scopes and permissions

| Role / context in demo | Visible events |
|---|---|
| SUPER_ADMIN + allowed scope | Admin, parent, content, support sample events; **only an illustrative pre-authorized scope** |
| ACCOUNT_ADMIN + allowed scope | Parent account management events |
| CONTENT_REVIEWER + allowed scope | Content review events |
| SUPPORT_OPERATOR + assigned ticket | Support events tied to `SUP-203` fixture |
| Any role + no scope / permission revoked | Access denied, no event details |
| Request failure | Error and safe retry messaging, no misleading empty-list claim |

**Important:** These slices are **proposed illustrative UX fixtures**, **not final permission policy** for the matrix's 🔒 cells. Server-side scope checks must apply **before** counting, searching, paginating or returning details; otherwise totals and filters can leak unauthorized information. For audit access recording, implement a policy that avoids recursive or excessive audit-of-audit events.

## 4. Interaction states in standalone HTML

- 12 synthetic audit events, including successful account creation, suspension/restoration, invitation resend/revoke, role changes, content review, denied access and failed delivery.
- Text search, action filter, result filter, from/to dates, clear filters; no results state; five-row pagination.
- One fixed-size SVG Eye action per row, `aria-pressed`, selected-row background; width-stable table columns, responsive horizontal scroll.
- Selected event metadata and **before/after sanitized diff**; no raw child question/attempt data or credentials.
- UX test lab role: Super Admin / Account Admin / Content Reviewer / Support Operator; scope: permitted / none / assigned ticket; fault: normal / network failure / revoked access.
- Independent result feedback when access fails; hide data when unauthorized.
- Entirely local: changing a simulated role changes mock visibility; **not** a real authentication or authorization system.

## 5. UX states and security edge cases

| Condition | Expected UX |
|---|---|
| No events exist | Clear empty state, not a role failure |
| Filters yield zero | Filter-specific no-results state, clear reset |
| Scope denied / permission revoked | No sensitive totals, rows or details; explicit access-denied message |
| Loading / slow network | Sized placeholder to avoid unexpected layout shift (**production requirement; not yet demoed with async loading**) |
| Request error | Error feedback with retry concept; no claim there are no audit logs |
| Long audit history | Pagination + stable table layout; server-side filtering/sorting in real product |
| Sensitive event detail | Sanitized before/after; redact email/PII as required by policy |
| Target outside scope | Server rejects even if event ID is guessed |
| Download / export | Not exposed in low-fi; permission, redaction and policy OPEN |
| Immutable retention | Real storage/retention and tamper-evidence design OPEN |
| Browser zoom / narrow viewport | Horizontal scrolling without hiding action column, accessible full value details |
| Same actor with multiple roles | Effective scope must be computed using permissions + resource/context, not mere role label |

## 6. Proposed decisions — NOT CONFIRMED

| ID | Proposal | Status |
|---|---|---|
| **AW-34** | A-10 uses **read-only Audit Table + Filters + Selected Event Detail**, with summary counters only for authorized scope. | **PROPOSED** |
| **AW-35** | Search and filter by actor/target/action/outcome/time; before/after **sanitized metadata** in detail; no edit/delete action on audit. | **PROPOSED** (audit principle already confirmed) |
| **AW-36** | Permission-aware **role + resource scope + context** filtering for event list **and totals and details**, explicit denial/error states and support ticket scoping. | **PROPOSED** UI (D-051/AD-08 underlying decisions CONFIRMED) |
| **AW-37** | Stable fixed-width icon action and table sizing; clear accessible selection; keep event details from causing reflow in the table. | **PROPOSED** A-10 application of globally CONFIRMED D-062 / AW-21 |

## 7. Not yet decided

- Who can read which audit event categories under each conditional `🔒` cell, exact resource scope and use-case access policy.
- Retention duration, tamper evidence and integrity checks, system-level immutability strategy.
- Download/export permissions, PII masking/redaction policy and legal/operational retention requirements.
- Audit event taxonomy/schema; high-volume archival and indexes; correlation IDs and pseudonymization.
- Server integration, actual permission enforcement, backend search and event-detail API.
- Figma A-10, true responsive/browser QA and measured CLS.

## 8. Approval boundary

**A-01…A-09: low-fi APPROVED** (A-01/A-02 have Figma; A-03…A-09 approved HTML).  
**A-10: HTML LOW-FI DRAFT, pending user review**. No actual data, no live auth, no audit backend, no Figma frame. Next planned UX: **A-11 Access Recovery & Support**.

References: [Admin Portal Permission Matrix](./04-admin-portal.md), [Global Layout Stability](./11-global-layout-stability-guidelines.md), [A-09](./14-admin-permission-change-confirmation-wireframe.md), [Screen Inventory](./03-screen-inventory.md), [Decision Log](../idea-summarize/06-decisions-and-open-questions.md).
