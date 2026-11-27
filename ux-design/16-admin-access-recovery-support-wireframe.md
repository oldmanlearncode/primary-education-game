# 16 — A-11 Access Recovery & Support: UX Wireframe

> **2026-11-27 · ✅ HTML LOW-FI APPROVED — AW-38…AW-41 CONFIRMED**  
> Local interactive HTML: `A-11-access-recovery-support.html` (conversation artifact). **No Figma frame A-11 created**; no backend, real emails, recovery tokens or MFA implementation.

## 1. Purpose

A-11 gives authorized administrators a ticket-based support view to triage account access problems without seeing passwords, issuing credentials on behalf of users or bypassing existing account suspension/role controls.

**CONFIRMED foundations:** initial accounts provisioned by Admin, no public sign-up; invitation recovery and audit; only Super Admin manages Admin roles/accounts (ADM-D04); Support Operator must stay inside granted ticket scope (AD-08); D-051 audit/view permissions are conditional 🔒; parent account suspend/restore only SUPER_ADMIN and ACCOUNT_ADMIN; global avoid-unexpected-Layout-Shift D-062.

**Unconfirmed:** parent self-service password reset option, full recovery authorization matrix, exact reset token expiry/retry policy, identity verification levels, Admin MFA-loss recovery and emergency Super Admin recovery.

## 2. Proposed UI

- Read-only overview KPI cards: visible tickets, pending, delivery-failed, resolved — counts computed **only inside authorized scope**.
- Search by ticket/email; filters for recovery type and ticket status.
- Width-stable table, 38×38 SVG Eye icon, selected-row highlight. Responsive horizontal scroll.
- Ticket detail shows ticket ID, target account email, incident type, **account status vs recovery token status vs email delivery status separately**. No raw token, secret, password, or child data.
- Safe action buttons: Send guidance and Resolve ticket, subject to permissions; modal requires reason and acknowledgment.
- Mock Audit list and UX test lab simulate role, scope, delivery failure, expired token, permission revoked, concurrency conflict and network uncertainty.

## 3. Safe recovery flows

```text
A-11 queue → view authorized ticket → verify scope/identity and account state
 ├─ PASSWORD_RESET → issue user-controlled reset instructions via authorized service
 ├─ INVITE_EXPIRED → controlled new invitation using A-07 policy; no duplicate account
 ├─ DELIVERY_FAILED → inspect/retry delivery without deleting account
 ├─ ACCOUNT_LOCKED → block normal reset as unlock; refer to authorized A-05/A-06
 └─ ADMIN_RECOVERY / MFA loss → separate high-assurance, Super Admin security flow
       (details OPEN; no bypass of MFA / last Super Admin controls)

Action → reason + acknowledgment → server authorization/state check
 ├─ permitted → send/resolve, audit actor, target, reason, outcome
 ├─ send failure → preserve account, show failed delivery, allow controlled follow-up
 ├─ revoked permission / scope denied → block and hide unauthorized details
 ├─ concurrent update → conflict, reload before retry
 └─ outcome unknown → verify server status/idempotency before retry
```

User-friendly recovery response should avoid account enumeration in public-facing flows; this Admin Portal is authenticated and scope-limited.

## 4. Demo scenarios

The HTML uses synthetic ticket records such as `SUP-203` (forgotten password), `SUP-204` (failed email), `SUP-205` (expired invitation), `SUP-206` (locked account), and `SUP-207` (Admin recovery). Simulated roles: SUPER_ADMIN, ACCOUNT_ADMIN, SUPPORT_OPERATOR, CONTENT_REVIEWER. **This demonstration intentionally prohibits Support Operator from issuing resets or unlocking accounts**, and uses a conservative sample ticket scope; this is not a newly confirmed permission matrix.

Demo action behavior:
- Sending guidance returns mock `SENT` or `FAILED` while preserving account; no email is sent.
- Expired invitation gets `PENDING (MOCK)` in demo to illustrate reissue, **not final token-service implementation**.
- Locked/disabled account and Admin recovery have no self-service action in this page, avoiding privilege bypass.
- Resolve marks only a local ticket status; no real account data is modified.
- Input validation and audit entries are solely JavaScript mock behavior.

## 5. UX states & access control

| State | Requirement |
|---|---|
| No ticket in scope | Clear empty state; do not confuse with permission denied |
| Scope denied or permission revoked | Mask list, totals, details and actions; never leak existence via counters |
| Link expired or already consumed | Explain safe reissue/recovery; no token content |
| Email delivery failed | Partial success; keep account and ticket, retry safely |
| Parent account suspended | Does not get unlocked by password reset |
| Lost Admin MFA | Escalate to policy-controlled identity verification, no support bypass |
| Concurrent modification | Show conflict and refresh |
| Network unknown | Verify authoritative status before retry, idempotent recovery |
| Loading / slow network | Reserve stable skeleton dimensions (future production implementation) |
| Sensitive audit | No plaintext passwords, raw reset tokens, MFA codes or learning records |

## 6. Approved UX proposals — CONFIRMED (2026-11-27)

| ID | Proposal | Status |
|---|---|---|
| **AW-38** | A-11 uses **permission-aware ticket list + filter toolbar + selected ticket detail + scoped audit preview**, with summary counts only in scope. | **CONFIRMED** |
| **AW-39** | Recovery types are **Password Reset, Expired Invite, Delivery Failure, Locked Account, Admin/MFA Recovery**, each with its own safe handling and escalation. | **CONFIRMED** UX categorization |
| **AW-40** | Help actions require **scope authorization, reason and explicit acknowledgment**; never expose/set password or reset/MFA secrets; cannot bypass suspension. | **CONFIRMED** UX (underlying security decisions CONFIRMED) |
| **AW-41** | Display independent feedback for **failed delivery, expired token, permission lost, concurrent edit and unknown network outcome**, preserving account and avoiding repeated issuance. | **CONFIRMED** UX; same principles as prior approved recovery edge cases |

## 7. Still OPEN / implementation boundaries

- Whether Parent Portal offers user-initiated forgot-password flow at MVP, verification UX, provider choice, reset-token duration and rate-limits.
- Exact SUPPORT_OPERATOR ability to send recovery guidance **🔒**, and whether any read-only metadata is visible for delegated roles.
- Administrator MFA recovery, last Super Admin emergency workflow, independent approvals / break-glass access.
- Handling system-generated recovery events and storage, immutable audit, email delivery acknowledgment, idempotent operations, notification templates, PII redaction and retention.
- Figma version of A-11, real API integration, actual authorization/rate limiting and CLS/browser accessibility QA.

## 8. Progress

- **A-01…A-10:** APPROVED low-fidelity.
- **A-11:** HTML interactive low-fi **APPROVED**, no Figma frame.
- **A-12:** Content Quality Operations not yet designed; scope was originally marked FUTURE.
- **D-062/AW-21:** global Layout Stability guideline remains CONFIRMED.

References: [Admin Portal](./04-admin-portal.md), [Account Provisioning](./05-admin-account-provisioning.md), [A-07 Invitations](./10-admin-invitation-management-wireframe.md), [A-10 Audit](./15-admin-audit-history-wireframe.md), [Screen Inventory](./03-screen-inventory.md).


## 9. Approval record — CONFIRMED (2026-11-27)

**D-068 / AW-APP-10:** Người dùng: “Okay, Tôi hoàn toàn đồng ý với các đề xuất và màn hình A-11”. Phê duyệt **A-11 HTML low-fi wireframe** và **AW-38…AW-41**: danh sách ticket với filter, chi tiết, audit theo scope; nhóm nghiệp vụ recovery tách biệt; thao tác có quyền/lý do/acknowledgement, không để lộ credential/token hoặc bỏ qua trạng thái khóa; phản hồi riêng lỗi email/token/permission/concurrency/network, bảo vệ account khi delivery thất bại.

**Giới hạn:** Duyệt UX, không chốt những chính sách kỹ thuật còn OPEN ở mục 7 (quy trình tự phục hồi của parent, quyền SUPPORT_OPERATOR có điều kiện, Admin/MFA emergency recovery, token thời hạn, rate-limit, audit/backend). Chưa có Figma A-11 hay dịch vụ thực.
