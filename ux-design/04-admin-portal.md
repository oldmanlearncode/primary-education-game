# 04 — Admin Portal: Information Architecture, User Flows & Screen Inventory

> **Phase 2 UX Design · 2026-11-24 · DRAFT**  
> **CONFIRMED:** Có Admin Portal; giai đoạn đầu tài khoản phụ huynh do admin cấp phát/quản lý; không mở tự đăng ký công khai.  
> **✅ CONFIRMED 2026-11-24:** Super Admin + Admin có phân quyền; least privilege đối với dữ liệu học sinh; audit thay đổi tài khoản/quyền; hướng kích hoạt bằng lời mời an toàn thay vì gửi mật khẩu; tách quyền account administration và content review.  
> **PROPOSED:** Permission matrix cụ thể, kênh và vòng đời lời mời, UI chi tiết và triển khai xác thực vẫn cần review.

## 0. Admin decisions — CONFIRMED

| ID | Quyết định | Trạng thái |
|---|---|---|
| ADM-01 | **Super Admin + Admin có phân quyền**: có vai trò quản trị cao nhất và vai trò quản trị được cấp quyền theo nhiệm vụ. Số lượng Super Admin và quyền từng vai trò chưa chốt. | **CONFIRMED** |
| ADM-02 | **Least privilege / tách quyền truy cập dữ liệu trẻ**: quản trị tài khoản không mặc nhiên đọc toàn bộ thông tin học tập của học sinh. | **CONFIRMED** |
| ADM-03 | **Audit trail**: ghi nhận ai tạo, khóa, khôi phục tài khoản hoặc thay đổi quyền, cùng thời điểm và đối tượng tác động. | **CONFIRMED** |
| ADM-04 | **Secure account activation bằng lời mời thay vì gửi mật khẩu** là hướng UX đã được chọn. Kênh gửi, expiry, token design và recovery vẫn cần quyết định. | **CONFIRMED — direction** |
| ADM-05 | **Tách account admin và content reviewer**: quyền quản lý người dùng không tự động kèm quyền duyệt câu hỏi/chương trình học. | **CONFIRMED** |

## 1. Product boundaries

Little Explorers gồm ba trải nghiệm:

```text
ADMIN PORTAL (quản trị / cấp phát)
      │ tạo tài khoản / lời mời phụ huynh
      ▼
PARENT PORTAL (quản lý con / học tập)
      │ tạo child profiles / mục tiêu / parent assessment
      ▼
CHILD WORLD (học / khám phá)
```

- Admin **quản lý tài khoản và truy cập**, không tự động được quyền xem toàn bộ lịch sử học tập nhạy cảm của trẻ nếu không có mục đích/quyền phù hợp.
- Parent vẫn có quyền tạo/sửa child profiles **trong tài khoản đã được cấp phát**, trừ trường hợp quản trị viên thu hồi quyền hoặc chính sách đã đặt.
- **Không public self-registration, không guest preview** trong phạm vi vận hành ban đầu; nghiên cứu mở lại khi sản phẩm/hạ tầng sẵn sàng.
- Có thể dùng cùng hệ thống backend nhưng **khác giao diện và ranh giới quyền**. Không chốt kiến trúc deploy.

## 2. Admin sitemap (đề xuất)

```text
ADMIN PORTAL
├── Admin Sign-in / Session / Account Recovery
├── Dashboard & Operations
│   ├── Total parent accounts / statuses
│   ├── Pending invitations / access requests
│   └── Operational notices (không hiển thị PII trẻ không cần thiết)
├── Account Management
│   ├── List/search/filter parent accounts
│   ├── Create parent account / send invitation
│   ├── Parent account details / linked child count
│   ├── Activate / suspend / restore (permission controlled)
│   ├── Resend / revoke invitation
│   └── Access recovery (không xem mật khẩu)
├── Roles & Access Policies
│   ├── Admin user accounts and roles
│   ├── Role permissions / least privilege
│   └── Access changes & audit
├── Support & Audit
│   ├── Activity / change history
│   ├── Failed invitations / blocked users
│   └── Support actions (sensitive data requires separate approval)
├── Content Quality Operations (tích hợp sau / scope pending)
│   ├── Question reports / triage / quarantine
│   └── Content reviewers / status
└── Admin Settings
    ├── Security (MFA/session policy – proposal)
    └── Notification / operational preferences
```

**CONFIRMED:** Không gộp quyền tạo tài khoản với quyền duyệt kiến thức; **Super Admin + delegated Admin** là cấu trúc role cơ bản. **PROPOSED:** cụ thể hóa Account Admin / Content Reviewer / Support Operator, phân quyền đến từng action và giới hạn truy cập dữ liệu trẻ.

## 3. Admin flows (draft)

### A-F01 — Admin provision parent account
```text
Admin sign-in → Parent accounts → New parent
→ Nhập email/kênh liên hệ tối thiểu → Kiểm tra trùng
→ Tạo trạng thái INVITED/PENDING_ACTIVATION
→ Gửi lời mời kích hoạt an toàn (đề xuất)
→ Parent activate credentials → Login → Parent Onboarding
→ Child Profile → General Assessment [optional] → Goals → Child World
```
**Edge:** email đã dùng, lỗi gửi lời mời, lời mời hết hạn, kích hoạt trùng, người dùng chưa nhận được mail. Không gửi mật khẩu plaintext.

### A-F02 — Admin search, view, suspend / reactivate
```text
Admin sign-in → Search/filter account → Detail
→ Choose permitted action → Reason / confirm
→ Apply → Audit record → Notify parent if appropriate
```
**Edge:** suspend account khi trẻ đang chơi, account có nhiều child profiles, lệnh bị gửi trùng, admin tự khóa chính mình, phản hồi yêu cầu truy cập dữ liệu.

### A-F03 — Invitation recovery
```text
Pending invitation → Resend / revoke / renew
→ Previous token invalidated if needed → Audit
→ parent activates only latest valid invitation
```

### A-F04 — Admin roles and access changes
```text
Authorized admin → Admin users → Select user
→ Request role change → Confirm authorization
→ Apply → Re-evaluate permissions / sessions → Audit
```
**Edge:** người quản trị cuối cùng mất quyền; quyền hỗ trợ xem dữ liệu trẻ không được cấp ngầm.

### A-F05 — Account support without changing learning evidence
```text
Admin → Parent account issue → Verify request
→ Restricted support action → Audit / notify
```
Admin thao tác khắc phục truy cập **không tự sửa mastery / classification / answer events**; parent correction và content-incident đã có luồng riêng.

## 4. Screen inventory (new, proposed)

| ID | Screen / Overlay | UX priority | Wireframe |
|---|---|---|---|
| A-01 | Admin Sign-in / session expired | CORE | Chưa |
| A-02 | Admin Dashboard | CORE | Chưa |
| A-03 | Parent Account List / Search / Filters | CORE | Chưa |
| A-04 | Create Parent Account / Invitation | CORE | Chưa |
| A-05 | Parent Account Detail | CORE | Chưa |
| A-06 | Suspend / Restore Confirmation | CORE | Chưa |
| A-07 | Invitation Status / Resend / Revoke | CORE | Chưa |
| A-08 | Admin Users / Roles | SUPPORT | Chưa |
| A-09 | Permission Change Detail / Confirmation | SUPPORT | Chưa |
| A-10 | Audit History / Activity | CORE | Chưa |
| A-11 | Access Recovery / Support | SUPPORT | Chưa |
| A-12 | Content Quality Operations entry | FUTURE / scope review | Chưa |

**Entry/invite screens to add for parent**:
- `E-07` — Parent Invitation Acceptance / Activation
- `E-08` — Parent Sign-in / Session Recovery (no public sign-up)
- `E-09` — Invalid / Expired / Already Used Invitation

## 5. Access & UX safety (CONFIRMED principles; details proposed)
- Server-side role enforcement; hide buttons alone does not protect access.
- No public registration endpoint in initial phase.
- Admin's invitation token expires, single use and revocable; never expose account credentials in logs/emails.
- Prefer MFA and extra verification for privilege changes.
- **CONFIRMED:** audit ai tạo/khóa/khôi phục/thay quyền tài khoản (actor, timestamp, target; lý do đề xuất). Tối thiểu hóa PII của trẻ.
- Rate limits, idempotency, and retry for invitation creation.
- Suspend/revoke semantics and handling in-progress child sessions need policy.
- Distinguish parent vs admin access and data permissions, including later guardian roles.
- Plan transition for public registration **without** re-creating existing parent accounts.

## 6. OPEN for detailed admin UX (principles ADM-01…05 already CONFIRMED)
1. Đã chốt Super Admin + Admin có phân quyền. Còn OPEN: số lượng Super Admin, cách bootstrap, ai được cấp/thu hồi role, quy tắc bảo vệ quản trị viên cuối cùng; ma trận permissions.
2. Đã chọn nguyên tắc **lời mời kích hoạt an toàn, không gửi password**. Còn OPEN: kênh gửi (email/private link), hạn sử dụng, lời mời hết hạn/thu hồi và resend.
3. Whether parent can recover password independently after admin provisioning.
4. Who can link a child profile to another guardian?
5. Account suspension behavior for ongoing child session and offline device.
6. How much support visibility admin has into child learning data, subject to legal/privacy safeguards.
7. Whether Content Reviewer belongs inside same admin app or separate console.

These questions do **not** reopen the confirmed decision: **admin-provisioned accounts first, no open sign-up at launch**.
