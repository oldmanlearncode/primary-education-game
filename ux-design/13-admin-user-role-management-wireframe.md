# 13 — A-08 Admin User & Role Management: UX Wireframe

> **Phase 2 UX · 2026-11-24 · ✅ HTML LOW-FI APPROVED — AW-26…AW-29 CONFIRMED**  
> Interactive standalone artifact: `A-08-admin-user-role-management.html` in the conversation. **No Figma frame A-08 created.** Demo only: no real API, invitations, MFA, user authorization, session invalidation or persistent audit.

## 1. Confirmed principles and guardrails

From [Admin Portal Permission Matrix](./04-admin-portal.md):

- **ADM-D01:** Initial roles `SUPER_ADMIN`, `ACCOUNT_ADMIN`, `CONTENT_REVIEWER`, `SUPPORT_OPERATOR`.
- **ADM-D02/D03:** Multi-role with resource scope + context policy; role membership alone is insufficient for child-sensitive data.
- **ADM-D04:** **Only `SUPER_ADMIN`** creates/disables Admin accounts and grants/revokes Admin roles. This cannot be delegated to `ACCOUNT_ADMIN`.
- **AD-01:** protect the last active Super Admin; controlled recovery remains open.
- **AD-02:** prevent self-escalation. **AD-03:** multi-role without bypassing scope/context.
- **AD-04/AD-10:** concurrent modification and permission revocation during session must be validated server-side.
- **AP-D05:** mandatory MFA for Super Admin and MFA for other Admins at least on sensitive actions.
- **D-062:** minimize unexpected Layout Shift across the entire project.

**A-08 is for Admin identities and Admin-role assignments, not for parent users or raw children learning data.**

## 2. Proposed screen structure (AW-26)

```text
Admin Sidebar | A-08 Admin Users & Roles                  [+ Invite Admin]
              | [Total] [Active] [Pending activation] [Active Super Admin]
              | [Search email/ID] [Filter account status] [Filter role]
              | ----------------------------------------------------------
              | Email / ID        Roles                  Status     [Eye]
              | ----------------------------------------------------------
              |                               Details / permitted actions
              |                               Mock scoped audit preview
              | [UX lab: viewer role + MFA/concurrency/revoke/network scenarios]
```

The action button is a **38×38 SVG Eye icon**; row selection uses a background highlight and does not change button dimensions or table column widths. Feedback is in a reserved region. Modal is overlay. Responsive tables have a horizontal scroll container rather than clipping permissions/identities.

## 3. Actions and UX states

| Action/state | Intended UX behavior | Status |
|---|---|---|
| View Admin list | Super Admin-only in demo; other roles receive access denied | **PROPOSED UI boundary**, consistent with ADM-D04 management authority; eventual read-only access policy remains to be specified |
| Create Admin | Email, optional display name, multi-role selection; account `PENDING_ACTIVATION` | **PROPOSED UX**; real onboarding token/email mechanism OPEN |
| Assign/remove roles | Per-role checkboxes; confirmation, reason, account identity; MFA required | **PROPOSED UI**; only Super Admin can manage roles CONFIRMED |
| Disable/restore Admin | Requires confirmation + reason; not allowed for last active Super Admin | **PROPOSED UI**; last-Super protection CONFIRMED |
| Self-change | Demo blocks editing currently signed-in Super Admin account entirely | **PROPOSED conservative UX choice**, not an automatically approved universal account policy |
| Multi-role | Roles are not exclusive; scope/context still required | **CONFIRMED principle** |
| Revoked rights | Reject action and explain | **CONFIRMED policy**, UX copy PROPOSED |
| Concurrent modification | Conflict feedback, no silent overwrite | **CONFIRMED policy**, UX copy PROPOSED |
| MFA not completed | Block action until verification | **CONFIRMED requirement**, UX mock only |
| Network uncertainty | Show uncertain result; require server status check before retry | **PROPOSED UX** |
| Final Super Admin | Block role removal or disable if it leaves no active Super Admin | **CONFIRMED AD-01** |
| Audit | Mock actor/target/action/reason list | **CONFIRMED audit direction**, production scope and immutable storage OPEN |

The demo does not grant permission to manage Admin by changing a dropdown. Actual authorization must be enforced on every server request and must recheck target resource version and context.

## 4. UX test lab scenarios

Select simulated viewer role: `SUPER_ADMIN` / `ACCOUNT_ADMIN` / `CONTENT_REVIEWER` / `SUPPORT_OPERATOR`. Choose an Admin row and attempt role editing, disable/restore, or create.

Simulated fault modes: permission revoked before submit, concurrency conflict, network unknown, MFA incomplete. Creation checks simple email syntax and duplicate email in mock records; form requires role selection, reason and acknowledgment.

**Data lifecycle choice OPEN:** Demo starts new Admin as `PENDING_ACTIVATION`, without implementing invitation dispatch. No plaintext passwords or activation tokens are shown. Whether Admin Invitation is shared with or separate from Parent Invitation is an implementation/product decision still OPEN.

## 5. Edge cases

- **Super Admin last-active protection:** compute count of active Super Admin accounts; fail any operation that would reduce this to zero (server transactional enforcement required).
- **Self-escalation prevention:** role editing of the signed-in Admin is blocked in this draft; full self-service personal profile editing remains a separate topic.
- **Privilege revocation:** after role removal, active sessions should be revalidated and invalidated if necessary.
- **Audit and account state:** `DISABLED`, `SUSPENDED`, `PENDING_ACTIVATION` have distinct meanings. This demo's Admin-specific state transitions are **not production-lifecycle decisions**.
- **Scope/privacy:** Admin-management permissions do not imply permission to inspect child records, raw attempts, mastery or family data.

## 6. Approved AW items — CONFIRMED (2026-11-25)

| ID | Proposal | Status |
|---|---|---|
| **AW-26** | Use a permission-aware **Admin list + detail panel** with role/status filters, stable icon actions, and scoped audit preview. | **CONFIRMED** |
| **AW-27** | New Admin UX: required email + multi-role selection + optional name; initial pending activation, no direct password entry. | **CONFIRMED** |
| **AW-28** | Changes to Admin roles or account status require target review, reason, explicit acknowledgment and MFA; present conflicts/revoked permissions separately. | **CONFIRMED** UX (MFA/permissions/audit principles CONFIRMED) |
| **AW-29** | Protect the last active Super Admin in UI; avoid self-editing Admin roles in A-08; explain disabled actions. | **CONFIRMED** UX (AD-01/AD-02 principles CONFIRMED) |

## 7. Items not decided by this wireframe

- Read-only Admin directory visibility for delegated administrators; demo denies it by default, a conservative choice.
- Admin account activation and recovery email workflow (separate from Parent activation).
- Detailed Admin statuses, restore rules and permission-set versioning.
- Exact MFA provider, reauthentication UX and policy-driven step-up interval.
- Last Super Admin bootstrap/recovery, number of Super Admins allowed, and emergency recovery.
- Actual audit scope filtering; A-10 is pending.
- A-09 Permission Change Confirmation is not designed yet. The modal in this demo is illustrative, not final A-09 approval.

## 8. Current status

- **A-01…A-07 HTML/Figma low-fi approved**, Figma for A-03…A-07 not created.
- **A-08 APPROVED** (HTML low-fi); **AW-26…AW-29 CONFIRMED**.
- **Global Layout Shift minimization D-062 CONFIRMED**.
- Next UX screen: **A-09 Permission Change Confirmation** after A-08 review.

Sources: [A-06](./12-admin-suspend-restore-confirmation-wireframe.md), [Permission Matrix](./04-admin-portal.md), [Decision Log](../idea-summarize/06-decisions-and-open-questions.md).


## 9. Approval record — CONFIRMED (2026-11-25)

**D-065 / AW-APP-07:** Người dùng: “Tốt rồi, tôi đồng ý với màn hình và các đề xuất của ông.” — xác nhận **toàn bộ HTML low-fi A-08** và **AW-26…AW-29** (danh sách + panel, tạo Admin email/đa role, xác nhận + lý do + MFA, bảo vệ Super Admin cuối cùng và không tự sửa role ở A-08).

**Ranh giới:** chỉ duyệt bố cục/tương tác wireframe; chưa có A-08 Figma frame, production API, email activation, MFA thật hoặc audit bền vững. **Không coi việc duyệt AW-27 là chốt hạ tầng invitation Admin hoặc quy trình khôi phục Super Admin cuối cùng.** Các vấn đề OPEN mục 7 vẫn còn mở. Màn tiếp theo: **A-09 Permission Change Confirmation**.
