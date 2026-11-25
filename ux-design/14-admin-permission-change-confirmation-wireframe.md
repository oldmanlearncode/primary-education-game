# 14 — A-09 Permission Change Confirmation: UX Wireframe

> **2026-11-25 · ✅ HTML LOW-FIDELITY APPROVED — AW-30…AW-33 CONFIRMED**
>
> Bản HTML tương tác độc lập: `A-09-permission-change-confirmation.html` đính kèm cuộc trò chuyện. **Chưa có A-09 Figma frame; chưa tích hợp với A-08 bằng route/real API.** Đây là bước xác nhận thay đổi role của Admin từ A-08, không phải trang cấu hình quyền mới.

## 1. Nguyên tắc đã CONFIRMED được kế thừa

- **ADM-D01…04 / D-046…049:** Bốn role `SUPER_ADMIN`, `ACCOUNT_ADMIN`, `CONTENT_REVIEWER`, `SUPPORT_OPERATOR`; multi-role; RBAC kết hợp scope/context; chỉ Super Admin quản lý tài khoản/role Admin khác.
- **D-051:** Permission Matrix; không mặc định quyền xem dữ liệu học tập trẻ.
- **AD-01/02/03/04/10:** bảo vệ Super Admin cuối cùng; không tự nâng quyền; role theo scope/context; tránh ghi đè đồng thời; revalidate quyền bị thu hồi.
- **D-056 / AP-D05:** MFA bắt buộc Super Admin.
- **D-065 / AW-28/29:** thay đổi role/status cần review target, lý do, acknowledgment và MFA; không tự sửa role tại A-08.
- **D-062:** luôn chủ động tránh Layout Shift trên toàn dự án.

## 2. Information architecture (PROPOSED)

```text
A-08 Admin User & Role Management
  └─ Select Admin → Edit Roles → A-09 Confirmation overlay
         ├─ Target: email, Admin ID, account version (read only)
         ├─ Side-by-side: Existing Roles vs Proposed Roles
         │    ├─ Added roles highlighted
         │    └─ Removed roles highlighted
         ├─ Impact warning and active-session consequences
         ├─ Reason (required) + explicit acknowledgement
         ├─ MFA step-up check (mandatory for Super Admin)
         ├─ Server permission/scope/context and version check
         ├─ Failure → separate reason and safe recovery
         └─ Success → updated admin roles + audit + revalidation of sessions
```

A-09 is best implemented as **dialog/overlay launched from A-08** with a readable diff; the standalone HTML demo includes Admin shell and a side-by-side preview for inspection, then opens a modal for confirmation.

## 3. Role-diff and action model

- Scope of A-09 is **role assignment/revocation**; account status changes are a different action and require an equivalent confirmation flow.
- Comparison uses a snapshot of the target's account ID, role set and version. It should not expose unrelated protected data.
- Selected example operations: add SUPER_ADMIN to ACCOUNT_ADMIN, revoke SUPER_ADMIN from second Super Admin, or replace multi-role set with ACCOUNT_ADMIN + SUPPORT_OPERATOR.
- Explicit labels: **Thêm role**, **Thu hồi role**; visually distinguish each. Use text as well as color to support accessibility.
- **No-change** or **empty role set** is blocked in demo. Empty role-set acceptance is **not yet a finalized product policy**.
- **Last active Super Admin protection** is both UI hint and server-side transactional invariant; never rely on a frontend count.
- Demo blocks self-role changes at A-08/A-09 per AW-29.

## 4. State/error matrix

| State | UX behavior | Backend reality required |
|---|---|---|
| Valid diff, Super Admin | Show confirm + mandatory reason + acknowledge + MFA | AuthN/AuthZ, scope/context, server-side commit |
| No-op diff | Explain no change; disable confirmation | Compare normalized role sets |
| Removing last active Super Admin | Block and explain | Transactional check across accounts |
| Self-change | Block | Reject server-side |
| Role revoked mid-form | Explicit forbidden feedback | Recheck actor permissions at commit time |
| Concurrent change | 409 Conflict, ask to reload diff | Version/ETag or equivalent |
| MFA expired/incomplete | Ask to re-verify | MFA verified server-side, not mock input |
| Network result unknown | Do not blindly retry; verify status/idempotency | Idempotency and authoritative server state |
| Target has active session | Warn that access may change; revalidate/invalidate appropriate sessions | Session handling policy OPEN |
| Successful change | Success feedback, refresh roles, audit record | Atomic change + audit persistence |

## 5. Interactive HTML demo

- Choose one of four fixture Admin accounts, role operations (grant/revoke/replace) and see before/after role comparison.
- Confirm modal shows target, version, added/removed roles, mandatory reason, acknowledgement and **FAKE MFA input**. It accepts any 6 digits, deliberately does **not** perform real MFA. **Do not enter real MFA code**.
- Test lab: viewer role, revoked permission, conflict, uncertain network, expired MFA, active target session, last-active-Super scenario.
- Successful operation updates only in-memory fixture and appends a mock audit entry.
- **No actual authorization, session invalidation, persistence, MFA or backend change.**
- Layout stability: reserved notification region; stable side-by-side panels; overlay doesn't push page content; responsive stacking.

## 6. Approved UX proposals — CONFIRMED (2026-11-25)

| ID | Proposal | Status |
|---|---|---|
| **AW-30** | A-09 is an **explicit confirmation overlay** from A-08, with target identity and side-by-side role diff: Added vs Removed. | **CONFIRMED** |
| **AW-31** | Require **reason, target-impact acknowledgement and MFA** before role change; preserve a stable, informative failure state. | **CONFIRMED** UX (core AW-28/AP-D05 CONFIRMED) |
| **AW-32** | Show distinct recovery UI for **permission revoked, concurrency conflict, MFA expiry, unknown network result**; no blind retry. | **CONFIRMED** (underlying AD-04/AD-10 CONFIRMED) |
| **AW-33** | Warn about **active-session access impact** and highlight last-Super-Admin protection and no-op/self-edit invalid states before confirmation. | **CONFIRMED** UX (underlying AD-01/02 CONFIRMED) |

## 7. Open questions and limits

- Exact MFA provider, challenge layout, step-up interval, session invalidation policy.
- Whether role changes can be scheduled, approval-by-second-admin required for highly sensitive role grants, and maximum Super Admin count.
- Atomicity of role updates and last-Super-Admin protection, immutable audit implementation and request idempotency.
- Empty role set policy; account-state workflow is not approved by A-09.
- Responsive and accessibility QA in real browsers, keyboard focus trapping and measured CLS are not yet completed.

## 8. Progress

- A-01…A-08: approved low-fi (Figma for A-01/02; standalone HTML for A-03…A-08).
- **A-09:** standalone HTML low-fi **APPROVED**; no Figma frame, no production feature.
- A-10 Audit History: next planned screen.

**References:** [A-08](./13-admin-user-role-management-wireframe.md), [Admin Permission Matrix](./04-admin-portal.md), [Layout Stability](./11-global-layout-stability-guidelines.md), [Decision Log](../idea-summarize/06-decisions-and-open-questions.md).


## 9. Approval record — CONFIRMED (2026-11-25)

**D-066 / AW-APP-08:** Người dùng: “Tốt, tôi đồng ý và xác nhận tất cả các đề xuất mới của ông”. Chấp thuận **toàn bộ wireframe HTML low-fi A-09** và bốn đề xuất **AW-30…AW-33**: dialog xác nhận mở từ A-08 hiển thị role diff, xác nhận lý do/tác động/MFA, phản hồi lỗi theo loại và cảnh báo session/last Super Admin. **Figma A-09 chưa tạo**, chưa có backend / MFA thật / audit persistence. Những chính sách chi tiết về provider MFA, session invalidation và transaction vẫn OPEN; không tự coi bản demo đã vượt qua kiểm thử bảo mật thực tế.
