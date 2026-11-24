# Giai đoạn 2 — UX Design

> **IN PROGRESS · Bắt đầu 2026-11-24**  
> Mục tiêu: thiết kế **đầy đủ kiến trúc thông tin, user flow, wireframe tất cả màn hình** của Little Explorers trước khi bước sang Visual Design.

## Đầu vào đã có

- [Product Discovery & confirmed decisions](../idea-summarize/README.md)
- [Decision Log](../idea-summarize/06-decisions-and-open-questions.md)
- [Figma hiện có](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ) — 5 child flows screens (wireframe + hi-fi concept) và 4 parent portal wireframes; các phần còn lại chưa được thiết kế đầy đủ.
- [Roadmap](../ROADMAP.md)

## Tài liệu bước đầu (draft để review)

1. [01 — Sitemap & Information Architecture](./01-sitemap-information-architecture.md) — phân vùng Child World, Parent Portal, hệ thống thông báo, sự cố.
2. [02 — User Flows](./02-user-flows.md) — onboarding, chọn môn, học, ôn, phụ huynh, corrections.
3. [03 — Screen Inventory & UX States](./03-screen-inventory.md) — danh sách các màn/overlay và trạng thái để không sót edge case.
4. [04 — Admin Portal](./04-admin-portal.md) — sitemap, flow, 12 màn admin; đăng ký do admin cấp phát.
5. [05 — Admin Account Provisioning & Parent Activation](./05-admin-account-provisioning.md) — AP-D01…05 và AP-01…10 đã **CONFIRMED**; vòng đời account/invitation, kích hoạt và trạng thái UX.
6. [06 — Admin Login & Dashboard Wireframes](./06-admin-login-dashboard-wireframes.md) — **đã dựng low-fi A-01 và A-02 trong Figma**, chờ review layout và bổ sung state.

**✅ UX-01…UX-05 đã CONFIRMED**: hub-based Child World, bản đồ nhiều tầng, Parent Portal năm khu, truy cập hybrid và chuyển hồ sơ có xác nhận. [Chi tiết tại sitemap](./01-sitemap-information-architecture.md).

## Nguyên tắc UX

- **Platform đa môn** (Toán, Tiếng Việt, TN&XH...), không giả định vào là màn Phép nhân.
- **Child UX:** ít chữ, nút đủ lớn, có audio khi cần, điều hướng có định hướng nhưng không ép trẻ vào một môn.
- **Parent UX:** dashboard đa môn; adult gate, profile/approval/question review/learn together; ghi nhận tác động thay đổi.
- **Admin UX:** quản lý tài khoản/phân quyền/audit; initial rollout **chỉ cấp phát tài khoản qua admin**, không self-registration; chỉ truy cập thông tin trẻ theo đúng quyền.
- **Dùng trạng thái hiển thị rõ:** loading, offline, permission, pending approval, error, no-content, invalidated result, version correction.
- **Phân biệt trạng thái đã có Figma và chưa có Figma.** Tài liệu mới chỉ là baseline để review, không mặc nhiên là wireframe đã vẽ.

## Gợi ý trình tự công việc trong giai đoạn 2

1. Review sitemap + screen inventory, đánh dấu `REQUIRED / OPTIONAL / LATER` trong phạm vi UX đầy đủ.
2. Review các user flow và happy path/edge cases quan trọng.
3. Hoàn thiện các sơ đồ flow và màn thiếu ở Figma, link từng screen tới inventory.
4. Review interaction và UX states với nhóm tuổi 1–2, 3, 4–5.
5. Chốt baseline UX để bắt đầu Visual Design.

**Status:** **Information Architecture – năm quyết định điều hướng đã CONFIRMED**; sitemap thực tế vẫn cần tinh chỉnh, user flow/wireframe là **INITIAL DRAFT**. Phase 2 tiếp tục **IN PROGRESS**.


## Phase 2.2 — Parent Onboarding & Admin Scope (2026-11-24)

**CONFIRMED:** UX-06 onboarding ngắn và optional skip; UX-07 progressive parent assessment; UX-09 family-owned child profiles; **UX-10/11** initial admin-provisioned accounts và bổ sung Admin Portal; ON-01…ON-12 theo hướng xử lý đã đề xuất, điều chỉnh cho mô hình cấp phát. **UX-08 DEFERRED**: không mở Guest Preview hoặc public sign-up lúc đầu. **ADM-01…ADM-05 CONFIRMED:** Super Admin + delegated Admin; hạn chế quyền xem dữ liệu trẻ; audit; lời mời kích hoạt an toàn; tách content review. Chi tiết permission matrix, invitation, recovery **vẫn PROPOSED / needs UX review**.


## Phase 2.3 — Admin Permission Architecture (2026-11-24)

**ADM-D01…ADM-D04 CONFIRMED:** bốn vai trò ban đầu (Super Admin / Account Admin / Content Reviewer / Support Operator); RBAC + Resource Scope + Context Policy; multi-role; chỉ Super Admin quản lý vai trò quản trị và kiểm soát truy cập nhạy cảm theo chính sách riêng. **AD-01…AD-12 đã CONFIRMED** ở mức hướng xử lý; **permission matrix đã CONFIRMED** với từng ô ✅/❌/🔒; chi tiết policy triển khai ô 🔒 vẫn OPEN. [Admin Portal](./04-admin-portal.md).


## Phase 2.3 — Permission Matrix approved (2026-11-24)

**ADM-PM-01 / D-051 CONFIRMED:** toàn bộ matrix 4 role đã được phê duyệt, bao gồm các giá trị ✅/❌/🔒. Các ô 🔒 đòi hỏi scope/context/authorization riêng, không được coi là quyền truy cập mặc định. [Bảng đầy đủ tại Admin Portal](./04-admin-portal.md). Giai đoạn UX Design vẫn **IN PROGRESS**.


## Phase 2.4 — Account Provisioning (2026-11-24)

**AP-D01…AP-D05 và AP-01…AP-10 CONFIRMED**: account/invitation/delivery lifecycle tách biệt; dashboard theo permission; email bắt buộc duy nhất; invitation mặc định 72 giờ, có thể cấu hình và single-use; MFA bắt buộc Super Admin, Admin khác ít nhất cho thao tác nhạy cảm. Edge cases AP-01…10 được chốt hướng xử lý. [Tài liệu 05](./05-admin-account-provisioning.md). **Wireframes chưa triển khai**.


## Phase 2.4 — Wireframe progress (2026-11-24)

**A-01 Admin Login, A-02 Admin Dashboard: LOW-FI WIREFRAMES APPROVED (2026-11-24)**, [mở bản vẽ](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ?node-id=13-4). Đã duyệt bố cục hai màn hình; vẫn cần bổ sung MFA/error/permission variants, responsive và interaction states. **Chưa coi Phase 2 hoàn tất.**


## Phase 2.4 — A-03 Parent Account List (2026-11-24)

**A-03 HTML LOW-FI APPROVED (2026-11-24):** đã có đặc tả và bản HTML low-fi tương tác để review (tìm kiếm/lọc/sắp xếp/phân trang/xem nhanh). [Đặc tả A-03](./07-admin-parent-account-list-wireframe.md). **Chưa có frame Figma A-03** vì Figma Starter MCP tool-call limit; sẽ đồng bộ khi có thể thao tác Figma. **A-01/A-02 và A-03 (HTML) đã APPROVED**; chỉ A-03 chưa đưa lên Figma.


## Phase 2.4 — A-04 Create Parent Account (2026-11-24)

**A-04 HTML LOW-FI APPROVED (2026-11-24).** Form email required + display name optional, checkbox gửi lời mời, các trạng thái duplicate/send failure/permission/network. [Specification](./08-admin-create-parent-account-wireframe.md). [A-03](./07-admin-parent-account-list-wireframe.md) đã được xác nhận AW-05…AW-08. **Figma A-03/A-04 chưa tạo vì Starter MCP call limit.** **AW-09…AW-12 CONFIRMED**; A-04 HTML low-fi approved, Figma frame vẫn chưa có.


## Phase 2.4 — A-05 Parent Account Detail (2026-11-24)

**A-05 HTML LOW-FI APPROVED (2026-11-24).** Demo linked from A-03, includes account states, confirmation reason, conditional action buttons, audit activity and in-progress child session alert. [A-05 UX Specification](./09-admin-parent-account-detail-wireframe.md). **AW-13…AW-16 CONFIRMED**; A-05 has no Figma frame yet due to tool limit. A-01…A-04 approval status unchanged.


### A-05 approval follow-up (2026-11-24)

**A-05 Parent Account Detail approved at HTML low-fi level; AW-13…AW-16 CONFIRMED.** See [09 — A-05](./09-admin-parent-account-detail-wireframe.md) and decision **D-061**. **Next:** A-07 Invitation Management. Figma A-03/A-04/A-05 frames are still not created; prototype and backend remain future tasks.


## Phase 2.4 — A-07 Invitation Management (2026-11-24)

**A-07 standalone interactive HTML low-fi CREATED — DRAFT / AWAITING REVIEW.** Search and filter separate token/delivery states, role-aware resend/revoke, confirmation reason, audit history, simulator for email delivery failure/concurrency/permission revocation/network. [A-07 UX specification](./10-admin-invitation-management-wireframe.md). **AW-17…AW-20 PROPOSED, not CONFIRMED**. Linked A-03/A-04/A-05 HTML demos now navigate to A-07. **Figma frame A-07 NOT CREATED**; previous Starter MCP tool quota issue remains unresolved. A-01…A-05 approvals unchanged.
