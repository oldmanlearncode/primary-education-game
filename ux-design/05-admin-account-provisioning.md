# 05 — Admin Account Provisioning UX & Parent Activation

> **Phase 2.4 · 2026-11-24 · ✅ CONFIRMED:** AP-D01…AP-D05 và AP-01…AP-10 (nguyên tắc UX, phương án xử lý).  
> **IN PROGRESS:** Wireframe và tương tác chi tiết. Chưa quyết định công nghệ xác thực, địa chỉ trang, email provider hay cách triển khai backend.

## 1. Phạm vi

Admin Login → Dashboard → Parent Account List → Create Parent Account → Send/Manage Invitation → Parent Activation → Parent Login → Parent Onboarding. **Không có đăng ký công khai** và không có Guest Preview trong đợt vận hành ban đầu. Các tài khoản phụ huynh do Admin cấp; phụ huynh tự quản lý hồ sơ con trong tài khoản được cấp.

## 2. Quyết định chính thức — CONFIRMED

| ID | Quyết định | Trạng thái |
|---|---|---|
| **AP-D01** | **Tách Account Lifecycle và Invitation Lifecycle.** Account không bị tạo lại chỉ vì invitation hết hạn/gửi lỗi. | **CONFIRMED** |
| **AP-D02** | **Dashboard theo permission:** widget và dữ liệu khác nhau tùy role và scope, không bắt buộc tạo nhiều dashboard riêng. | **CONFIRMED** |
| **AP-D03** | **Create Parent Account:** email là dữ liệu bắt buộc duy nhất đề xuất; display name/admin note có thể tùy chọn; Admin không nhập thông tin trẻ, khối lớp, Mastery hay mật khẩu phụ huynh. | **CONFIRMED** |
| **AP-D04** | **Invitation hết hạn mặc định sau 72 giờ**, có thể cấu hình; **single-use**. Gửi lại phải tuân thủ chính sách vô hiệu hóa/hiệu lực token để tránh nhiều lời mời cạnh tranh. | **CONFIRMED** |
| **AP-D05** | **MFA bắt buộc cho Super Admin**; đối với Admin khác, MFA ít nhất khi thực hiện thao tác nhạy cảm. | **CONFIRMED** |

Phạm vi **72 giờ là mặc định thiết kế đã được chọn**, có thể điều chỉnh qua cấu hình, không phải thời hạn cố định trong mọi tình huống.

## 3. State machines

### 3.1 Parent Account Status
```text
CREATE → PENDING_ACTIVATION → ACTIVE
                              ├→ SUSPENDED → ACTIVE (restore)
                              ├→ DISABLED  → ACTIVE (authorized reactivate)
                              └→ CLOSED (closing/data workflow)
```
Không đánh đồng `CLOSED` với xóa ngay mọi dữ liệu cá nhân. Khôi phục, đóng, vô hiệu hóa phải theo quyền và policy.

### 3.2 Invitation: Token Status và Delivery Status phải tách riêng
```text
Invitation token: PENDING → ACCEPTED | EXPIRED | REVOKED
Delivery status: QUEUED → SENT | FAILED (retry possible)
```
Ví dụ: Account `PENDING_ACTIVATION`, Invitation `EXPIRED`, Delivery `SENT`. Lời mời hết hạn không tạo thêm Parent Account.

## 4. User flow đầu-cuối

```text
A-01 Admin Login → MFA theo vai trò/risk policy
  ↓
A-02 Dashboard (permission-aware widgets)
  ↓
A-03 Parent Account List / search / filter
  ↓
A-04 Create Parent Account (email required, optional display name)
  ├─ Existing email → đưa về account đã có (nếu có quyền)
  └─ New email → PENDING_ACTIVATION
         ↓
A-07 Invitation Management → Send
  ├─ Delivery failed → giữ account pending; resend có kiểm soát
  └─ Delivery sent → Parent opens link
                ↓
E-07 Accept Invitation
  ├─ Invalid / expired / revoked / already used → E-09 recovery instructions
  └─ Valid + account eligible → parent chooses credentials
                      ↓
                 Account ACTIVE
                      ↓
E-08 Parent Sign-in → Parent Onboarding
                      ↓
Child profile → progressive parent assessment → goals → Child World
```

## 5. Screen UX requirements

| Screen | Hiển thị | Actions / states |
|---|---|---|
| **A-01 Admin Sign-in** | Admin identifier, sign-in, MFA prompt, recovery | wrong password, disabled, expired session, insufficient permission, rate limiting |
| **A-02 Dashboard** | Parent count, active/pending/suspended, invitation alerts, recent actions **theo quyền** | loading, empty, partial permission, error |
| **A-03 Parent Accounts** | email, account status, linked child count, created time, detail action | search/filter/sort/pagination; avoid risky one-click suspend |
| **A-04 Create Parent** | email required; display name optional; option send invitation | duplicate email, validation, submission pending, delivery failed, retry |
| **A-07 Invitations** | token status, delivery status, expiry time, history | resend/revoke with permission; no raw token exposure |
| **E-07 Parent Activation** | invitation status, read-only recipient identifier, set credentials | expiry/invalid/revoked, activation success, already activated |
| **E-08 Parent Sign-in** | parent login/recovery; **no public signup** | wrong credentials, expired session, suspended parent account |
| **E-09 Invitation Error** | thông báo thân thiện | hướng dẫn liên hệ bộ phận quản trị để được cấp lại, không lộ token hay lỗi hệ thống |

## 6. Edge cases — AP-01…AP-10 ✅ CONFIRMED

| ID | Tình huống | Cách xử lý đã chốt | Trạng thái |
|---|---|---|---|
| **AP-01** | Email phụ huynh đã có tài khoản | Không tạo trùng; dẫn đến hồ sơ đã có nếu Admin có quyền. | **CONFIRMED** |
| **AP-02** | Account tạo thành công nhưng gửi mail lỗi | Giữ account ở trạng thái chờ kích hoạt; cho phép gửi lại. | **CONFIRMED** |
| **AP-03** | Admin nhấn Create nhiều lần | Ngăn request trùng/idempotency để không nhân bản account/invite. | **CONFIRMED** |
| **AP-04** | Phụ huynh mở các invitation khác nhau | Chỉ chấp nhận lời mời hợp lệ theo chính sách hiệu lực hiện hành. | **CONFIRMED** |
| **AP-05** | Kích hoạt thành công nhưng đăng nhập lỗi | Không tạo account lại; hỗ trợ retry/recovery. | **CONFIRMED** |
| **AP-06** | Account bị khóa sau khi phát lời mời | Chặn kích hoạt khi trạng thái account không cho phép. | **CONFIRMED** |
| **AP-07** | Admin mất quyền trong khi đang mở form | Re-check permission tại hành động phía server; thông báo quyền thay đổi. | **CONFIRMED** |
| **AP-08** | Link kích hoạt được mở trên thiết bị khác | Cho phép nếu invitation và các điều kiện xác thực hợp lệ. | **CONFIRMED** |
| **AP-09** | Hai Admin đồng thời gửi lại lời mời | Tránh nhiều token cạnh tranh vượt chính sách; xử lý concurrency. | **CONFIRMED** |
| **AP-10** | Email gửi nhưng phụ huynh không nhận được | Kiểm tra trạng thái, hỗ trợ resend có giới hạn và xử lý hỗ trợ. | **CONFIRMED** |

## 7. Chi tiết vẫn OPEN (không thay đổi các quyết định đã xác nhận)

- Provider gửi email và delivery tracking; mức tin cậy của trạng thái `SENT` (không đồng nghĩa đã đọc/đã nhận).
- Thời gian và cách hết hạn của **invitation được cấu hình**; thời hạn phiên Admin, MFA method, cách backup/recovery.
- Form validation, copy, responsive states, retry/rate limits, session behavior sau suspend.
- Kiến trúc hiện thực và bảo vệ token ở backend; quyền cụ thể của những ô 🔒 trong Permission Matrix đã chốt.
- Chi tiết bảo vệ privacy, lưu trữ dữ liệu và các yêu cầu pháp lý áp dụng.

## 8. Liên kết
- [Admin Portal – Role/Permission Matrix & AD edge cases](./04-admin-portal.md)
- [Core User Flows](./02-user-flows.md)
- [Screen Inventory](./03-screen-inventory.md)
- [Decision Log](../idea-summarize/06-decisions-and-open-questions.md)

**Trạng thái Phase 2:** UX Design tiếp tục **IN PROGRESS**; chưa đánh dấu wireframe đã hoàn thiện.
