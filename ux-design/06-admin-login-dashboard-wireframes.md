# 06 — Admin Wireframes: A-01 Login & A-02 Dashboard

> **Phase 2 UX Design — 2026-11-24 · ✅ WIREFRAME BASELINE APPROVED**  
> **Người dùng đã phê duyệt 2 wireframe A-01 và A-02** (2026-11-24) ở mức bố cục low-fidelity hiện có. **Chưa** đồng nghĩa phê duyệt tất cả trạng thái MFA/error, responsive/role variants, prototype tương tác hoặc code.

**Figma:** [Admin Portal low-fi A-01 + A-02](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ?node-id=13-4)  
**Figma frame ID:** Group `13:4`, `A-01 = 13:8`, `A-02 = 13:28`.  
**Inventory mapping:** `A-01 Admin Sign-in`, `A-02 Admin Operations Dashboard`.

## 1. A-01 — Admin Login

### Mục tiêu
Cho phép Super Admin / Admin được cấp quyền đăng nhập. Không dùng luồng đăng ký công khai. Admin Login khác Parent Login về quyền và bước bảo mật.

### Nội dung wireframe
- Nhận diện `Little Explorers / Admin Portal`.
- Email, password, quên mật khẩu, nút `Đăng nhập`.
- Chú thích MFA cho Super Admin.

### Interaction proposal

```text
Admin opens Login
 → Enter email + password
 → Submit
    ├─ Invalid input → inline validation
    ├─ Wrong credentials → generic error + retry policy
    ├─ Account suspended/disabled → deny + support path
    ├─ Missing admin permission → deny, no admin access
    └─ Password accepted
          ├─ Super Admin → mandatory MFA
          ├─ Other Admin → MFA as required, at least sensitive actions
          └─ Authorized → A-02 dashboard
```

### Trạng thái cần thiết kế tiếp
| State | Điều kiện | UX yêu cầu |
|---|---|---|
| Default | Chưa nhập | Input labels rõ, password masked |
| Input error | Email trống/sai định dạng | Inline validation, giữ input |
| Credentials error | Sai mật khẩu/email | Thông báo chung, không tiết lộ account có tồn tại |
| MFA challenge | Cần bước thứ hai | Màn/bottom-sheet MFA riêng; cách xác thực cụ thể **OPEN** |
| MFA failed / timeout | Mã không đúng/hết hạn | Retry hoặc recovery an toàn |
| Session expired | Phiên hết hạn | Quay lại login, giữ đường dẫn trở lại sau xác thực nếu hợp lệ |
| Permission denied | Không có role admin | Không hiển thị Admin Portal |
| Rate limited | Thử quá nhiều | Trạng thái tạm khóa thử, không công bố thông tin nhạy cảm |
| Network error | Kết nối thất bại | Cho retry có kiểm soát |

### Quy tắc được CONFIRMED
- **AP-D05:** Super Admin bắt buộc MFA; Admin khác MFA ít nhất khi thao tác nhạy cảm.
- **ADM-D04:** chỉ Super Admin thay đổi quyền quản trị.
- Không mở self-registration.
- Kiểm tra permission ở phía server, không dựa vào ẩn UI.

## 2. A-02 — Permission-Aware Admin Dashboard

### Mục tiêu
Tập trung thông tin vận hành tương ứng với permission và resource scope của người đăng nhập.

### Nội dung wireframe
- Sidebar: Tổng quan, Tài khoản phụ huynh, Lời mời kích hoạt, Quản trị viên, Audit Logs, Cài đặt.
- Header: Tên trang, role context, sign out.
- KPI: tổng phụ huynh, active, pending activation, suspended (**dữ liệu minh họa**).
- CTA tạo tài khoản phụ huynh và quản lý lời mời.
- Alerts: invitation lỗi/hết hạn.
- Recent admin activity theo phạm vi audit.
- Ghi chú hạn chế dữ liệu cá nhân trẻ.

### Permission behavior
| Role | Widget / action trọng tâm | Phạm vi |
|---|---|---|
| SUPER_ADMIN | Tổng quan vận hành + quản lý role/admin | Không mặc nhiên được xem hồ sơ học tập trẻ |
| ACCOUNT_ADMIN | Parent account KPIs, Pending Invitations, Create Parent | Chỉ các account trong scope được cấp |
| CONTENT_REVIEWER | Nội dung chờ review, question incidents | Không mặc định được tạo/sửa parent accounts |
| SUPPORT_OPERATOR | Ticket được phân công, invitation support nếu có quyền 🔒 | Không truy cập dữ liệu ngoài scope/case |

**Quan trọng:** Figma A-02 đang minh họa trạng thái **ACCOUNT_ADMIN**, chưa vẽ các biến thể cho 3 vai trò còn lại. Sidebar chỉ là khung điều hướng: trong phiên thực, nút không đủ quyền phải ẩn hoặc disabled, còn backend tiếp tục enforce.

### UX states cần làm tiếp
- Empty accounts / first-time operation.
- Permission-dependent widgets (including mixed-role).
- Invitation delivery failure, expired tokens.
- Dashboard slow loading / partial failures.
- Expired admin session / permission revoked while open.
- Audit information out of scope.
- Responsiveness (desktop/tablet), keyboard navigation, accessibility.

## 3. Figma deliverable

Frame group: `05 — ADMIN PORTAL / WIREFRAMES · A-01 + A-02` ở vị trí riêng, không sửa Child World/Parent Portal hiện có.

**Đã có:** 2 editable layout frames, input/button/cards/sidebar, role-specific content, annotations.

**Chưa có:** full set of error-state frames, MFA interaction screen, mobile responsive frames, hi-fi design system, functioning navigation and prototype hotspots. Những phần này nằm trong công việc UX tiếp theo, không đánh dấu completed.

## 4. Quyết định wireframe đã được duyệt và các phần còn mở

| ID | Đề xuất | Trạng thái |
|---|---|---|
| AW-01 | Bố cục desktop-first trong 2 frame: A-01 login tập trung, A-02 sidebar trái và nội dung phải | **APPROVED as drawn** |
| AW-02 | Bố cục A-02 Account Admin minh họa, shell dashboard theo permission | **APPROVED as drawn**; hướng permission-aware **CONFIRMED (AP-D02)**; các role variant chưa thiết kế |
| AW-03 | A-01 email/password, không có self-sign-up; MFA được nhắc trong khung hiện có | **APPROVED as drawn**; màn MFA chi tiết chưa thiết kế; MFA requirement **CONFIRMED** |
| AW-04 | Hai CTA trong A-02: tạo tài khoản phụ huynh và quản lý lời mời | **APPROVED as drawn** |

## 5. Các màn tiếp theo

A-03 Parent Account List → A-04 Create Parent Account → A-07 Invitation Management → E-07 Parent Activation.

**Nguồn quyết định:** [05 — Admin Account Provisioning](./05-admin-account-provisioning.md), [04 — Permission Matrix & Roles](./04-admin-portal.md), [06 — Product Decision Log](../idea-summarize/06-decisions-and-open-questions.md).

## 6. UX approval record

**D-058 / AW-APP-01 — CONFIRMED (2026-11-24):** Chủ dự án xác nhận: “Okay đồng ý với 2 wireframe đã vẽ.” Hai layout Figma **A-01 (13:8)** và **A-02 (13:28)** được phê duyệt theo bản low-fi hiện tại. Những trạng thái/chế độ chưa vẽ và interaction spec chưa duyệt riêng vẫn được giữ **IN PROGRESS**. Tiếp theo: A-03, A-04, A-07.
