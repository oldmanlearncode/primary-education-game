# 09 — A-05 Parent Account Detail: HTML wireframe & interactions

> **Phase 2 UX · 2026-11-24 · DRAFT FOR REVIEW (NOT APPROVED).**
>
> Bản HTML độc lập: `A-05-parent-account-detail.html`, liên kết từ A-03. Có dữ liệu giả và các thao tác mô phỏng thuần trình duyệt; **không phải giao diện sản phẩm hay backend thật**. Chưa tạo Figma frame A-05.

## 1. Mục tiêu và phạm vi

Từ **A-03 Parent Account List → A-05 Parent Account Detail**, Admin có quyền xem metadata cần thiết của tài khoản phụ huynh, kiểm tra trạng thái, lời mời, hoạt động audit và thực hiện hành động có kiểm soát. Không hiển thị dữ liệu học tập chi tiết của trẻ. Không cấp quyền cho Admin thông qua UI đơn thuần.

### Bố cục màn hình A-05 (PROPOSED)

- Header/breadcrumb có đường quay lại A-03; email, account ID, ngày tạo, status badge.
- **Account Information:** email, mã, tên hiển thị, trạng thái account, **số** hồ sơ trẻ liên kết, dấu mốc đăng nhập.
- **Invitation Summary:** token status, delivery status, expiry **tách biệt**; CTA sang A-07 (chưa triển khai).
- **Administrative Actions:** Tạm khóa, Khôi phục, Vô hiệu hóa và Tải lại; chỉ hiện/enable khi permission, resource scope và account state cho phép.
- **Recent Audit Activity:** thao tác gần đây theo quyền, ai tác động và lý do khi thực hiện thay đổi.
- **Confirmation dialog:** hành động, target email, lý do bắt buộc, cảnh báo phiên học đang hoạt động.

## 2. State/permission behavior

| Account Status | Hành động hợp lệ đề xuất | Điểm cần lưu ý |
|---|---|---|
| `PENDING_ACTIVATION` | Tạm khóa, vô hiệu hóa | Invitation vẫn là entity độc lập; không kích hoạt account bị khóa |
| `ACTIVE` | Tạm khóa, vô hiệu hóa | Nếu bé đang học cần kết thúc phiên an toàn theo AD-05 |
| `SUSPENDED` | Khôi phục, vô hiệu hóa | Lưu actor, target, reason |
| `DISABLED` | Chưa cho reactivation ngay trong draft; cần quy trình riêng | Tránh khôi phục nhầm account bị vô hiệu hóa dài hạn |
| `CLOSED` | Read-only | Không tự xóa dữ liệu trẻ |

Các điều kiện permission ở trên là **cách trình bày UI đề xuất** dựa trên Permission Matrix đã CONFIRMED, không tự tạo thêm role/quyền.

## 3. Confirmation flow

```text
A-05 view
  → Admin clicks Suspend/Restore/Disable
  → Verify permission + scope/context (server in production)
  → Confirm dialog: affected account + required reason
      ├─ Cancel / empty reason → no change
      ├─ Concurrent change → refresh and re-evaluate (AD-04)
      ├─ In-progress child session → checkpoint-safe handling (AD-05)
      ├─ Permission revoked → deny (AD-10)
      └─ Authorized → state transition → audit record → feedback
```

**Không thay đổi trực tiếp** mastery, learning evidence hoặc raw answer attempts. Lý do thao tác phải được ghi audit khi backend xử lý thành công.

## 4. Các tình huống kiểm thử trong HTML

Panel **Phòng thử nghiệm UX** cho chọn 5 account statuses, 4 role mẫu và 5 conditions (`normal`, `session`, `revoked`, `conflict`, `network`). Trên bản HTML có thể:

- ACTIVE → Suspend → confirmation + required reason → status badge đổi → audit entry giả lập.
- SUSPENDED → Restore → confirmation + audit giả lập.
- ACTIVE/PENDING/SUSPENDED → Disable, cần lý do.
- SUPPORT_OPERATOR/CONTENT_REVIEWER → suspend/restore/disable buttons bị khóa.
- Thiếu quyền, conflict hoặc network error → feedback riêng.
- Trẻ đang học → cảnh báo checkpoint trước thao tác suspend.
- Invitation state không bị đổi tự động khi account state chuyển.
- A-03 quick drawer → link sang A-05 theo account ID. (Dữ liệu vẫn là fixtures.)

**Giới hạn quan trọng:** HTML chỉ kiểm tra UI và thay đổi dữ liệu trong RAM của trình duyệt; không có session security, MFA, resource authorization, optimistic locking, email sending hay audit persistence. Mọi server policy còn cần triển khai riêng.

## 5. UX states cần review

| UX State | Yêu cầu |
|---|---|
| Default | Thông tin metadata cần thiết, action phụ thuộc permission |
| Loading/Error | Skeleton/loading, retry có kiểm soát; thông báo mất mạng |
| Unauthorized | Hide/block detail ngoài scope, không leak dữ liệu |
| Concurrent update | Yêu cầu refresh; không ghi đè tài khoản |
| Suspend with child session | Thông báo checkpoint và chỉ ra chính sách an toàn |
| Suspended/Disabled/Closed | Button thích hợp theo state, giải thích vì sao bị khóa |
| Invitation expired/failed | Không tạo lại parent account; xử lý lời mời ở A-07 |
| Audit empty/failed | Empty/error state, không tiết lộ audit ngoài quyền |
| Mobile/tablet | Thẻ thông tin xếp dọc, thao tác rõ ràng |

## 6. Các quyết định UI mới — CHƯA CONFIRMED

| ID | Đề xuất | Trạng thái |
|---|---|---|
| **AW-13** | A-05 chia thành **Account Overview + Invitation Summary + Audit Activity + Actions**, đồng bộ sidebar A-02/A-03/A-04. | **PROPOSED** |
| **AW-14** | Khóa/khôi phục/vô hiệu hóa **chỉ tại A-05**, mỗi thao tác cần **dialog xác nhận + lý do bắt buộc**. | **PROPOSED** (audit và không one-click ở A-03 đã CONFIRMED) |
| **AW-15** | Chỉ số lượng hồ sơ trẻ, không đưa chi tiết học tập vào A-05; dữ liệu lời mời hiển thị status token/delivery riêng. | **PROPOSED** về layout; privacy/AP-D01 đã CONFIRMED |
| **AW-16** | Tài khoản `DISABLED` và `CLOSED` không khôi phục tức thì trên A-05; cần workflow riêng, tránh thao tác nhầm. | **PROPOSED** |

## 7. Tiến độ

- **A-01/A-02:** Figma low-fi approved.
- **A-03/A-04:** HTML low-fi approved, Figma frames chưa tạo.
- **A-05:** HTML interactive draft **đang chờ review**, chưa có Figma frame.
- **A-07:** Invocation/Invitation Management chưa thiết kế chi tiết; button trong A-05 hiển thị placeholder.

Liên kết: [A-03](./07-admin-parent-account-list-wireframe.md), [A-04](./08-admin-create-parent-account-wireframe.md), [Permission Matrix](./04-admin-portal.md), [Account Lifecycle](./05-admin-account-provisioning.md).
