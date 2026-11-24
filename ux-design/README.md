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

## Nguyên tắc UX

- **Platform đa môn** (Toán, Tiếng Việt, TN&XH...), không giả định vào là màn Phép nhân.
- **Child UX:** ít chữ, nút đủ lớn, có audio khi cần, điều hướng có định hướng nhưng không ép trẻ vào một môn.
- **Parent UX:** dashboard đa môn; adult gate, profile/approval/question review/learn together; ghi nhận tác động thay đổi.
- **Dùng trạng thái hiển thị rõ:** loading, offline, permission, pending approval, error, no-content, invalidated result, version correction.
- **Phân biệt trạng thái đã có Figma và chưa có Figma.** Tài liệu mới chỉ là baseline để review, không mặc nhiên là wireframe đã vẽ.

## Gợi ý trình tự công việc trong giai đoạn 2

1. Review sitemap + screen inventory, đánh dấu `REQUIRED / OPTIONAL / LATER` trong phạm vi UX đầy đủ.
2. Review các user flow và happy path/edge cases quan trọng.
3. Hoàn thiện các sơ đồ flow và màn thiếu ở Figma, link từng screen tới inventory.
4. Review interaction và UX states với nhóm tuổi 1–2, 3, 4–5.
5. Chốt baseline UX để bắt đầu Visual Design.

**Status:** Các tài liệu UX là **INITIAL DRAFT** — chờ chủ dự án review; chỉ **giai đoạn UX Design đã bắt đầu** là được ghi IN PROGRESS.
