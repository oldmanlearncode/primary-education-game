# 10 — A-07 Invitation Management: UX Wireframe & Interactions

> **2026-11-24 · HTML LOW-FI DRAFT / AWAITING REVIEW**  
> Standalone interactive demo: `A-07-invitation-management.html` (conversation attachment). No server, no real email, no persistent audit. **Figma A-07 NOT CREATED**; A-03/A-04/A-05 remain HTML-only because of the Figma tool-call limit previously reported.

## 1. Scope and confirmed foundations

This screen handles invitation discovery, token and delivery lifecycle, resend/revoke, audit preview, and permission-aware actions. It is distinct from creating a parent account (A-04) or changing account state (A-05).

Previously **CONFIRMED**:
- **AP-D01:** separate Parent Account Status vs Invitation Token Status vs Delivery Status.
- **AP-D04:** default invitation lifespan **72 hours**, configurable, **single-use**.
- **ADM-PM-01:** `SUPER_ADMIN` and `ACCOUNT_ADMIN` may resend invitations; `SUPPORT_OPERATOR` may do so **only conditionally 🔒**; `CONTENT_REVIEWER` cannot.
- **AD-06/AD-07:** used/expired tokens cannot activate; issue new invite under policy.
- **AP-02/AP-04/AP-06/AP-09/AP-10:** sending failure does not delete parent account; account state must permit activation; concurrency and controlled resend.
- **AD-03/AD-04/AD-08/AD-10:** audit, concurrency conflict, support ticket scope, revalidate current permission.

## 2. A-07 HTML wireframe layout — PROPOSED

```text
[Admin sidebar]  [A-07 Invitation Management / heading]
                 [Pending] [Accepted] [Expired] [Send failed]
                 [Search email/account ID] [Token filter] [Delivery filter] [Sort] [Clear]
                 --------------------------------------------------------------
                 Parent account | Account status | Token status | Delivery | Expires | Actions
                 --------------------------------------------------------------
                 [pagination]
                 [Selected Invitation Details] [Audit activity]
                 [UX test lab: role / support-scope / failures]
```

**Information architecture:** status cards; search and two **independent** status filters; paginated table; selected invitation detail; recent audit events; confirmation dialog. Raw token and activation URLs are **never shown**.

Table entries show account ID, email, account status, invitation token status, delivery status, expiry timestamp, update timestamp. UI feedback always distinguishes success of invitation issuance from success of email delivery.

## 3. Invitation action rules — PROPOSED UX on top of confirmed policies

| Case | Resend | Revoke | Explanation |
|---|---|---|---|
| Parent `PENDING_ACTIVATION`, invite `PENDING` | Eligible with permission | Eligible with permission | Resend supersedes old active token to avoid parallel valid tokens |
| `EXPIRED` invite | Eligible with permission | No need | Create fresh token; do not recreate parent account |
| `REVOKED` invite | Eligible with permission | N/A | New invitation after an explicit admin action |
| `ACCEPTED` invite | Not for that invite | No | Already consumed; use account recovery flow where needed |
| Parent `ACTIVE` | Not applicable | Not applicable here | Activation no longer required |
| Parent `SUSPENDED/DISABLED/CLOSED` | Block by default | Separate policy/workflow | Prevent activating ineligible accounts |
| Delivery `FAILED` with still-pending token | Controlled resend | Permission-dependent | Do not confuse token validity with delivery result |

**Resend vs retry:** The demo treats a resend as replacing the active invitation token. Whether the backend retries *delivery of the same still-valid token* versus *reissues a fresh token* remains a technical/security implementation decision. The UI should label and audit the actual operation consistently.

## 4. Confirmation & error states

```text
A-07 list → select invitation → resend / revoke
  → Permission + resource scope + current account and token state checked
  → Confirmation dialog (target + reason required)
       ├─ Cancel / invalid reason → no action
       ├─ Session permission revoked → deny
       ├─ Concurrent update → conflict, refresh; never overwrite
       ├─ Network outcome unknown → status lookup before retry
       ├─ Resend success → replacement invite pending, 72h default, audit
       ├─ Delivery fails → account PENDING_ACTIVATION remains, delivery FAILED
       └─ Revoke success → token REVOKED, account state unchanged, audit
```

**UX states:** loading, empty list, no filter results, permission denied, disabled actions, token just expired, delivery failed, stale selection, double submission, rate limits and generic connectivity error. Accessible focus/labels and readable mobile table scroll are part of review, not finished product acceptance.

## 5. Interactive HTML demo coverage

- 7 invitation mock records across `PENDING`, `ACCEPTED`, `EXPIRED`, `REVOKED`, delivery `SENT/FAILED/QUEUED`, and ineligible parent statuses.
- KPI cards, text search, separate token/delivery filters, sorting and five-row pagination.
- Selected invitation detail with `resend`, `revoke`, `View parent account`.
- Confirmation modal, required reason (demo validation ≥8 characters), mock audit trail.
- Role simulation (`SUPER_ADMIN/ACCOUNT_ADMIN/SUPPORT_OPERATOR/CONTENT_REVIEWER`), ticket-scoped resend checkbox for support (mock only).
- Error simulator: delivery failure, concurrent update, revoked permission, uncertain network outcome, reset fixture.
- Link navigation to A-03/A-04/A-05; no real API, email, persistence or authorization enforcement.

**Limitations:** Mock support permission checkbox is **not** a grant of production access. All access control and action idempotency must be enforced on the server. The demo replaces invitation state in place for ease of review; a production audit/history model must preserve prior invitation events.

## 6. Decisions for review — NOT CONFIRMED

| ID | Proposal | Status |
|---|---|---|
| **AW-17** | Layout **KPI overview + searchable invitation table + selected detail + audit**, consistent with A-02/A-03/A-05. | **PROPOSED** |
| **AW-18** | **Separate filters and badges** for Account Status, Token Status, Delivery Status; do not infer acceptance from a sent email. | **PROPOSED** UI (underlying AP-D01 CONFIRMED) |
| **AW-19** | Resend and Revoke require **confirmation + reason**, visible only when permission, account status and token state permit. | **PROPOSED** UI (underlying scope/audit rules CONFIRMED) |
| **AW-20** | Resend explicitly supersedes any still-valid activation token; send failures show **partial success** and preserve account; UI links back to A-05. | **PROPOSED** detail (underlying AP-02/AP-09 CONFIRMED) |

**Still OPEN:** exact retry-vs-reissue semantics, resend frequency limits, notification provider delivery acknowledgments, token issuance/revocation transaction strategy, multi-channel support, and responsive state-specific frames.

## 7. Phase 2 status

- **A-01/A-02:** Figma low-fi **APPROVED**.
- **A-03/A-04/A-05:** HTML low-fi **APPROVED**; Figma frames **not created**.
- **A-07:** HTML interactive **DRAFT / NEEDS REVIEW**, Figma frame **not created**.
- No product code, production authorization, or backend/email service delivered.

Links: [Account Provisioning](./05-admin-account-provisioning.md), [A-05](./09-admin-parent-account-detail-wireframe.md), [Admin Permission Matrix](./04-admin-portal.md), [Screen Inventory](./03-screen-inventory.md).


## 8. Global layout stability rule applied (2026-11-24)

**D-062 / UX-GLOBAL-01 and AW-21 CONFIRMED** by the user. A-07 demo fixed the `Xem` → `Đang xem` text expansion bug: fixed-size SVG Eye icon with accessible label/title and `aria-pressed`; selected row highlighted without changing column width; colgroup + fixed table layout with horizontal overflow for narrow viewports. See [11 — Global Layout Stability Guidelines](./11-global-layout-stability-guidelines.md). **AW-17…AW-20 remain PROPOSED**, and A-07 is still a draft pending layout/interaction approval.


## 9. Review feedback: layout-shift correction accepted (2026-11-24)

User: “Okay tôi thấy 2 bản chỉnh sửa đã ổn rồi. Tiếp tục thôi.” The **AW-21-based stabilization edits for A-03 and A-07 HTML demos are accepted** (fixed-size Eye button/selection state and stable table columns). This accepts the **specific refinements**, not necessarily the complete A-07 layout or **AW-17…AW-20**, which remain PROPOSED pending explicit review.
