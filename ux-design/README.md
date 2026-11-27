# Giai đoạn 2 — UX Design

> **IN PROGRESS · Bắt đầu 2026-11-24**  
> Mục tiêu: thiết kế **đầy đủ kiến trúc thông tin, user flow, wireframe tất cả màn hình** của Little Explorers trước khi bước sang Visual Design.

**GLOBAL UX RULE — CONFIRMED D-062:** toàn bộ các màn cần chủ động hạn chế **Unexpected Layout Shift**, chọn giải pháp theo ngữ cảnh, không áp đặt một CSS technique. [Đọc guideline + checklist](./11-global-layout-stability-guidelines.md). Đây là rule áp dụng cho mọi wireframe và implementation, bao gồm những màn đã duyệt.

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

**A-07 standalone interactive HTML low-fi CREATED — DRAFT / AWAITING REVIEW.** Search and filter separate token/delivery states, role-aware resend/revoke, confirmation reason, audit history, simulator for email delivery failure/concurrency/permission revocation/network. [A-07 UX specification](./10-admin-invitation-management-wireframe.md). **AW-17…AW-20 CONFIRMED on 2026-11-24 (D-063)**. Linked A-03/A-04/A-05 HTML demos now navigate to A-07. **Figma frame A-07 NOT CREATED**; previous Starter MCP tool quota issue remains unresolved. A-01…A-05 approvals unchanged.


## Global UX rule — layout stability (2026-11-24)

**D-062 / UX-GLOBAL-01 + AW-21 CONFIRMED.** Avoid unexpected Layout Shift across Child World, Parent Portal and Admin Portal. A-07/A-03 HTML table demos updated with fixed-size icon button and stable columns. [Full guidance and acceptance criteria](./11-global-layout-stability-guidelines.md). **A-07 HTML low-fi APPROVED; AW-17…AW-20 CONFIRMED (D-063).**


## Phase 2.4 — A-06 Confirmation wireframe (2026-11-24)

**A-06 standalone HTML interactive draft created**, accessible from A-05 demo; [UX specification](./12-admin-suspend-restore-confirmation-wireframe.md). Test suspend/restore, required reason and acknowledgment, concurrent edit, revoked permission, network unknown, active/offline child session. **AW-22…AW-25 CONFIRMED on 2026-11-24 (D-064)**; underlying permission/security decisions unchanged. **No Figma frame or production backend.**

**User reviewed and accepted A-03/A-07 layout-shift corrections** in the most recent response. This was **only a limited correction approval at the time**; a later explicit user message approved **all A-07** and **AW-17…AW-20** on 2026-11-24.


## Phase 2.4 — A-06 and A-07 approvals (2026-11-24)

**A-06 and A-07 HTML low-fi wireframes APPROVED.** A-07 **AW-17…AW-20 CONFIRMED** (D-063); A-06 **AW-22…AW-25 CONFIRMED** (D-064). User-approved Layout Stability rule D-062 / AW-21 remains global. **Offline unsynced-session operational handling is OPEN**, as are production email/token mechanics. Both screens still lack Figma frames; neither is implemented in backend. Next planned UX screen: **A-08 Admin Users & Role Management**.


## Phase 2.4 — A-08 Admin User & Role Management (2026-11-24)

**A-08 HTML LOW-FI APPROVED (2026-11-25).** Super Admin-only role/account management demo: searchable admin table, multi-role, pending activation, explicit confirmation+reason, MFA/error scenarios, last-Super protection, and stable table layout. [Specification 13](./13-admin-user-role-management-wireframe.md). **AW-26…AW-29 CONFIRMED (D-065)**, no Figma A-08 frame and no production backend/authorization. A-01…A-07 remain approved as previously recorded.


## Phase 2.4 — A-08 approval (2026-11-25)

**A-08 Admin User & Role Management APPROVED at HTML low-fi level**; **AW-26…AW-29 CONFIRMED** per D-065. [UX spec](./13-admin-user-role-management-wireframe.md). Figma A-08 not created; backend role enforcement, invitation activation, MFA provider and Super Admin emergency recovery not yet implemented/fully defined. Next: **A-09 Permission Change Confirmation**.


## Phase 2.4 — A-09 Permission Change Confirmation (2026-11-25)

**A-09 HTML LOW-FI APPROVED (2026-11-25).** Includes before/after role diff, modal confirmation with mandatory reason + acknowledgement + simulated MFA, last Super Admin guard, conflict/revoked permissions/network/MFA-expired scenarios. [A-09 specification](./14-admin-permission-change-confirmation-wireframe.md). **AW-30…AW-33 CONFIRMED (D-066)**. **Figma A-09 NOT CREATED**, no real backend/authorization/MFA. A-01…A-08 approval statuses unchanged. Next candidate: A-10 Audit History.


## Phase 2.4 — A-09 approval (2026-11-25)

**A-09 Permission Change Confirmation HTML low-fi APPROVED; AW-30…AW-33 CONFIRMED** as decision **D-066**. [Specification](./14-admin-permission-change-confirmation-wireframe.md). A-09 still lacks Figma frame; backend MFA, session invalidation, audit and conflict validation remain implementation work. **Next UX screen: A-10 Admin Audit History.**


## Phase 2.4 — A-10 Admin Audit History (2026-11-25)

**A-10 HTML LOW-FI APPROVED (2026-11-27).** Mock event table, before/after event detail, filter/date/search/pagination, role+scope+ticket simulation, explicit denied/network states and globally approved Layout Shift prevention. [UX specification](./15-admin-audit-history-wireframe.md). **AW-34…AW-37 CONFIRMED (D-067)**. The 🔒 audit permissions are still conditioned on role/scope/context policy; demo fixtures must not be mistaken for the final authorization matrix. **Figma A-10 NOT CREATED**, no real audit backend or immutable storage. A-01…A-09 approvals unchanged.


## Phase 2.4 — A-10 approval (2026-11-27)

**A-10 Admin Audit History HTML low-fi APPROVED; AW-34…AW-37 CONFIRMED** per decision **D-067**. [A-10 UX spec](./15-admin-audit-history-wireframe.md). Permission scope details for 🔒, audit retention, immutable storage, data redaction/export remain OPEN. Figma A-10 not created, no backend integration. **Next: A-11 Access Recovery & Support.**


## Phase 2.4 — A-11 Access Recovery & Support (2026-11-27)

**A-11 HTML interactive low-fi DRAFT created — awaiting review.** Includes ticket list and details, access/scope simulator, safe guidance/resolve mock, delivery failure, expired invite, account suspension and Admin MFA recovery escalation. [UX specification](./16-admin-access-recovery-support-wireframe.md). **AW-38…AW-41 CONFIRMED (D-068).** Recovery-provider settings, self-service password reset, delegated Support permissions and Super Admin emergency recovery remain OPEN. **Figma A-11 NOT CREATED, no backend/email delivery.** A-01…A-10 approvals unchanged.


## Phase 2.4 — A-11 approval (2026-11-27)

**A-11 Access Recovery & Support HTML low-fi APPROVED; AW-38…AW-41 CONFIRMED** (D-068). [Specification](./16-admin-access-recovery-support-wireframe.md). Figma A-11 remains not created; recovery infrastructure, conditional support scopes and Super Admin MFA recovery remain OPEN. **Next UX screen: A-12 Content Quality Operations**, previously marked FUTURE/scope review; do not assume it is MVP.


## Phase 2.4 — A-12 Content Quality Operations (2026-11-27)

**A-12 HTML low-fi DRAFT created; awaiting user review.** Review queue, source/answer detail, risk severity, triage/quarantine/correction status flow, aggregated session impact and bulk-error warning, role/scope simulation and mock audit. [UX specification](./17-admin-content-quality-operations-wireframe.md). **AW-42…AW-45 PROPOSED, NOT APPROVED.** A-12 remains **FUTURE / scope review**, so drawing it does not add it to MVP. Child raw attempts/mastery are not edited; no real recomputation/notification happens. Figma A-12 NOT CREATED; no backend. A-01…A-11 remain approved. After A-12 review, review all 12 Admin low-fi screens, outstanding policies and Figma sync backlog.


## A-12 V3 review iteration (2026-11-27)

User requested a reason/justification view **at each state transition**, without inspecting global audit, and a way to browse **all older audit events**, beyond the six-item preview, with paging, subject/severity filters and search by IDs/question/topic/message. New HTML low-fi `A-12-content-quality-operations-v3.html` provides both. **AW-47 and AW-48 PROPOSED, awaiting explicit user approval**; prior AW-42…AW-46 and A-12 remain DRAFT. [Specification 17](./17-admin-content-quality-operations-wireframe.md). No backend/persistent audit or scope policy implementation.


## Current Admin Portal approval (2026-11-27)

**A-12 V5 HTML low-fi APPROVED; AW-42…AW-48 CONFIRMED (D-069). All 12/12 Admin Portal low-fi screens A-01…A-12 APPROVED.** This supersedes historical draft notes above. V5 includes corrected-answer editor and separate result impact preview, on-demand processing history and per-transition details, six recent audit records and full searchable/filterable/paginated audit. [Spec A-12](./17-admin-content-quality-operations-wireframe.md). **A-12 remains FUTURE/scope review, not automatically MVP**; Figma and production implementation remain undone. Next: Admin Portal UX Final Review; this is not completion of Phase 2 globally.


## Admin Portal UX Final Review (2026-11-27)

[18 — Admin Portal UX Final Review](./18-admin-portal-final-review.md): review findings, integration and QA gaps, open policy gates, proposed common UI and progressive disclosure, Figma backlog. **REVIEW DRAFT / awaiting user approval**. All 12 existing low-fi approvals remain unchanged; no new decisions confirmed. Phase 2 remains IN PROGRESS.
