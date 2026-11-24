# 08 — A-04 Create Parent Account: Wireframe & Interaction Spec

> **2026-11-24 · LOW-FI HTML DRAFT / NEEDS USER REVIEW**  
> Bản HTML tương tác: `A-04-create-parent-account.html` được cung cấp dưới dạng tệp đính kèm trong cuộc trò chuyện; chưa commit thành product code. **Figma frame A-04 CHƯA TẠO** do Figma MCP tool-call limit của gói Starter.  
> **CONFIRMED trước đó:** AP-D03 chỉ yêu cầu email bắt buộc, display name optional, phụ huynh tự thiết lập mật khẩu; AP-D04 invitation 72 giờ cấu hình được, single-use; account status và invitation/delivery status tách biệt; AP-01…AP-10.

## 1. Mục tiêu
Account Admin hoặc Super Admin hợp lệ cấp tài khoản phụ huynh mới; không tạo child profile, không chọn môn, không thiết lập điểm học tập hoặc mật khẩu thay phụ huynh. Không có public self-registration.

## 2. Bố cục A-04 (PROPOSED, chưa duyệt wireframe)

- Sidebar nhất quán A-02/A-03; breadcrumb Admin / Parent Accounts / A-04.
- Form trung tâm: **Email phụ huynh** (bắt buộc), **Tên hiển thị** (tùy chọn).
- Checkbox **Gửi lời mời kích hoạt ngay** (mặc định checked trong bản demo; cần duyệt UX).
- Hai nút: **Hủy** và **Tạo tài khoản**.
- Khung bên phải hiển thị 4 bước: create → invite → activate → parent onboarding.
- Feedback panel thể hiện account status và invitation token/delivery status **riêng biệt**.
- Phần giả lập lỗi dành riêng cho review: delivery failed, permission revoked, network failure.

## 3. Tương tác đề xuất
```text
A-03 Parent Account List → A-04 Create Parent Account
 ├─ email invalid → inline validation; không submit
 ├─ email exists → ngăn tạo trùng (AP-01), liên kết xem account nếu có quyền
 ├─ permission revoked → server rejects (AP-07)
 ├─ network uncertain → inspect request status before retry (AP-03)
 └─ create success → parent account PENDING_ACTIVATION
      ├─ unchecked send invitation → no invitation yet; admin can send later in A-07
      ├─ send success → Invitation PENDING; Delivery SENT
      └─ send fails → account persists pending; Delivery FAILED; admin can retry A-07 (AP-02)
```

Demo hiển thị kết quả bằng dữ liệu giả; chưa gọi API thật và chưa gửi email thật.

## 4. Account vs Invitation lifecycle

| Object | Ví dụ state | Ý nghĩa |
|---|---|---|
| Parent Account | `PENDING_ACTIVATION` | Account được tạo nhưng chưa kích hoạt |
| Invitation Token | `PENDING` | Token còn hiệu lực, một lần, mặc định 72 giờ |
| Invitation Delivery | `SENT` / `FAILED` | Trạng thái gửi độc lập; SENT không chứng minh email đã được đọc |

Khi email gửi thất bại, **không xóa account và không tạo lại account**. Nguyên tắc này **CONFIRMED** bởi AP-02.

## 5. UX state matrix

| State | Hiển thị | Ghi chú |
|---|---|---|
| Default | Form trống, invite checkbox checked | Checkbox default là PROPOSED |
| Email empty | Inline required error | Không gửi request |
| Invalid email | Inline format error | Server validation vẫn cần thiết |
| Duplicate email | Existing account notice | Không leak account ngoài scope; policy server |
| Submitting | Disable duplicate submit | Idempotency AP-03 |
| Created; invitation SENT | Success summary, new account ID | Token data không hiển thị |
| Created; send FAILED | Partial success warning, resend through A-07 | AP-02 |
| Created; invitation skipped | Success account only, pending | Send later by Admin |
| Permission changed | Reject request, feedback | AD-10/AP-07 |
| Network uncertain | Error + safe retry guidance | Tránh tạo trùng |
| Invitation invalid/expired | Quản lý ở A-07/E-09 | Không thuộc form create |

## 6. Edge-case cross references
- **AP-01** existing email, **AP-02** send failure without losing account, **AP-03** idempotent repeated create, **AP-07** authorization revoked; **AP-09** concurrent resend addressed at A-07.
- **ADM-PM-01:** only authorized account-management roles may create parent account.
- **ADM-03:** audit actor, target, time and action; never log plaintext invitation tokens or passwords.

## 7. Các lựa chọn UI mới cần review

| ID | Đề xuất | Status |
|---|---|---|
| **AW-09** | A-04 bố cục form chính và aside tóm tắt onboarding, nhất quán sidebar Admin | **PROPOSED** |
| **AW-10** | Checkbox gửi invitation **bật mặc định**, được tắt để tạo account chờ và gửi sau | **PROPOSED** |
| **AW-11** | Form chỉ cần email và tên hiển thị optional; feedback trạng thái create/send tách biệt | **Nội dung dữ liệu CONFIRMED AP-D03; bố cục/UI PROPOSED** |
| **AW-12** | Với lỗi gửi invitation, hiển thị **partial success** và đường đến A-07 để retry, tránh tạo lại account | **Nguyên tắc CONFIRMED AP-02; UX copy/layout PROPOSED** |

## 8. Hạn chế bản demo và bước tiếp theo

- Standalone HTML chỉ có mock state tại browser. Data giả, không có persistence hoặc bảo mật thật.
- A-03 được nối từ nút **Tạo tài khoản** sang A-04 trong hai file HTML local.
- A-04 **chưa phải frame Figma** và **chưa được user approve**.
- Cần review UI, sau đó A-05 Parent Account Detail và A-07 Invitation Management; cập nhật Figma khi hạn mức công cụ cho phép.
