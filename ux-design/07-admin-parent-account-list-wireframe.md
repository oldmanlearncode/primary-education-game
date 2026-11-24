# 07 — A-03 Parent Account List: UX Wireframe & Interaction Spec

> **2026-11-24 · ✅ LOW-FIDELITY HTML WIREFRAME APPROVED**  
> Figma hiện không thể cập nhật vì công cụ thông báo **Starter plan MCP tool-call limit**. Không tuyên bố đã tạo frame Figma.  
> Đã tạo bản demo HTML độc lập có filter/search/pagination và quick-detail panel để review; không phải giao diện sản phẩm đã triển khai.

## 1. Mục đích

**A-03 – Parent Account List** là điểm quản trị danh sách tài khoản phụ huynh đã được cấp phát. Thực hiện được việc tìm kiếm, lọc và truy cập chi tiết (A-05), không mở public self-registration, không có thao tác khóa trực tiếp tại mỗi dòng.

**Các quyết định kế thừa đã CONFIRMED**: ADM-D01…04, permission matrix, AP-D01 account vs invitation state, AP-D02 permission-aware dashboard, AP-D03 create parent by email, AD-01…12, AP-01…10.

## 2. Bố cục màn hình đề xuất

```text
┌───────────────────┬────────────────────────────────────────────────────────────┐
│ Admin Sidebar     │ A-03 / Tài khoản phụ huynh                  ACCOUNT_ADMIN    │
│ ┌───────────────┐ │ Chỉ hiển thị metadata cần thiết — không có data học tập trẻ │
│ │ Dashboard     │ ├────────────────────────────────────────────────────────────┤
│ │ Parent        │ │ [Tìm email / mã] [Status▼] [Sort▼] [Xóa lọc] [+ Tạo TK] │
│ │ Accounts  ●   │ ├────────────────────────────────────────────────────────────┤
│ │ Invitations   │ │ Email / ID          Status        # Bé   Created   Action │
│ │ Admin Users   │ │ parent1@example... ACTIVE          2    24/11    [View]  │
│ │ Audit         │ │ parent2@example... PENDING         0    23/11    [View]  │
│ │ Settings      │ │ parent3@example... SUSPENDED       1    22/11    [View]  │
│ └───────────────┘ │ ├────────────────────────────────────────────────────────────┤
│                   │ │ Hiển thị 1–5 / 50                    [Trước] [Tiếp]      │
└───────────────────┴────────────────────────────────────────────────────────────┘
```

### Table columns
| Column | Hành vi | Quyền / privacy |
|---|---|---|
| Email / Account ID | Tìm kiếm; là định danh quản trị | Hiện chỉ trong phạm vi role/scope hợp lệ |
| Account Status | `PENDING_ACTIVATION`, `ACTIVE`, `SUSPENDED`, `DISABLED`, `CLOSED` | Không trộn với Invitation Status |
| Linked Child Profile Count | **Chỉ số lượng**, không hiển thị tên, lớp, learning records | Tuân thủ permission matrix / scope |
| Created At | Mốc tạo | Có sort |
| Action | View account detail → A-05 | Không khóa/khôi phục trực tiếp ở danh sách |

### Toolbar
- Search theo email hoặc mã tài khoản; phải kiểm tra server-side permissions, không suy diễn search có quyền toàn hệ thống.
- Filter status: All / Active / Pending Activation / Suspended / Disabled / Closed.
- Sort: newest/oldest created, email A–Z.
- Clear filters.
- CTA `+ Tạo tài khoản` → **A-04** theo quyền `parent_account:create`.
- Pagination (kích thước demo HTML là 5 chỉ để dễ test; sản phẩm thật còn OPEN).

## 3. Interaction Flow

```text
A-02 Dashboard → A-03 Parent Account List
  ├─ Search / filter / sort → update list (preserve filter state as appropriate)
  ├─ Row → View detail (A-05, permission checked)
  ├─ + Create → A-04 (permission checked)
  └─ No result → helpful empty state → clear filters
```

**Ghi chú prototype:** bản HTML độc lập cho phép tìm kiếm, filter, sort, phân trang và mở panel xem nhanh với dữ liệu giả. Nút `Tạo tài khoản` hiển thị thông báo vì A-04 chưa thiết kế; các menu điều hướng không được nối app thực.

## 4. Required states (proposed)

| State | UX |
|---|---|
| Loading | Table skeleton/placeholder, tránh layout jump |
| Empty account list | Empty state: mời tạo parent account nếu có quyền |
| No filter results | Nhắc thử đổi bộ lọc hoặc xóa lọc |
| Invalid search | Validation input, không truy vấn quá rộng |
| Permission denied | Chặn bảng/action nếu thiếu permission hoặc out-of-scope |
| Account changed concurrently | Refresh chi tiết, tránh hiển thị trạng thái cũ |
| Failed list request | Thông báo lỗi + retry |
| Session expired | Sign-in again; restore intended navigation if still authorized |
| Long list | Pagination (server-backed trong sản phẩm), sort/filter |
| Responsive | Table horizontal scroll / layout cô đọng không cắt dữ liệu |
| No access to child data | Chỉ số lượng child profile nếu quyền cho phép |
| Multi-role admin | Render actions theo permission kết hợp scope/context, không role-label cố định |

## 5. Edge-case mapping

- **AD-04:** hai admin thao tác đồng thời → list/detail có thể lệch tạm thời, xử lý stale state.
- **AD-08:** Support chỉ nhìn thấy account thuộc ticket được cấp; không được dùng search để bypass scope.
- **AD-10:** revoke quyền trong phiên → kiểm tra lại khi search/click.
- **AP-01:** tạo parent email trùng xử lý ở A-04, không tạo trùng ở A-03.
- **AP-D01:** filter status account khác trạng thái delivery/invitation.

## 6. AW-05…AW-08 — ✅ CONFIRMED (A-03 wireframe approved 2026-11-24)

| ID | Quyết định đề xuất |
|---|---|
| **AW-05** | Chọn layout **Admin Sidebar + Table + top filter toolbar** cho A-03, nhất quán A-02 đã duyệt. |
| **AW-06** | Tập trung thao tác nguy hiểm tại A-05; không hỗ trợ one-click suspend/restore tại A-03. |
| **AW-07** | Dữ liệu bảng tối thiểu: email/account ID, trạng thái account, số hồ sơ con, ngày tạo, link chi tiết. |
| **AW-08** | Tìm kiếm + lọc trạng thái + sort + phân trang; giữ tuân thủ resource scope và permission. |

**Chưa chốt:** table column cuối cùng, batch actions, saved filter state, mặc định page size, lựa chọn date format trong UI, A-05 detail, A-04 create, A-07 invites.

## 7. Deliverable status

- **A-01 / A-02**: Figma low-fi **APPROVED**.
- **A-03**: HTML interactive wireframe **APPROVED (2026-11-24)**; **Figma frame NOT CREATED** vì tool limit.
- **A-04**: HTML interactive draft created, awaiting review; **A-05 / A-07**: NOT STARTED. See [08 — A-04](./08-admin-create-parent-account-wireframe.md).

Sau khi có khả năng ghi Figma trở lại, cần chuyển A-03 sang các layer Figma chỉnh sửa được, liên kết frame vào [Screen Inventory](./03-screen-inventory.md), rồi review trực quan.


## 8. Approval record

**D-059 / AW-APP-02 CONFIRMED (2026-11-24):** Người dùng: “Okay tôi nghĩ như vậy ổn rồi. Tiếp tục thôi.” — phê duyệt **A-03 HTML low-fi** và bốn đề xuất **AW-05…AW-08** vừa được đưa ra để review. **Không đồng nghĩa Figma A-03 đã được tạo**, và không duyệt trước A-04.
