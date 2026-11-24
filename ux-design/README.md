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

**CONFIRMED:** UX-06 onboarding ngắn và optional skip; UX-07 progressive parent assessment; UX-09 family-owned child profiles; **UX-10/11** initial admin-provisioned accounts và bổ sung Admin Portal; ON-01…ON-12 theo hướng xử lý đã đề xuất, điều chỉnh cho mô hình cấp phát. **UX-08 DEFERRED**: không mở Guest Preview hoặc public sign-up lúc đầu. Details của roles/invite/recovery là **PROPOSED / needs UX review**.
