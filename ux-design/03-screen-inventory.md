# 03 — Screen Inventory & UX States

> **INITIAL DRAFT · 2026-11-24**. Danh mục dự kiến **toàn bộ** trải nghiệm UX; chưa phải tất cả đã có wireframe. Ưu tiên `CORE`/`SUPPORT`/`FUTURE` chỉ dùng cho việc thiết kế UX, **không xác định MVP**.

## 1. Entry, profile & onboarding

| Screen ID | Màn hình / overlay | UX priority | Figma | Ghi chú |
|---|---|---|---|---|
| E-01 | Splash / first-time welcome | CORE | Chưa | Độ tuổi + parent entry |
| E-02 | Adult gate / parent verification | CORE | Chưa | Không cho trẻ tự sửa chính sách |
| E-03 | Chọn hồ sơ bé | CORE | Chưa | Nhiều bé dùng chung thiết bị |
| E-04 | Tạo/sửa hồ sơ và Parent Assessment | CORE | Một phần ở parent profiles | Cho skip/cập nhật |
| E-05 | First module Discovery Assessment | CORE | Chưa | Không gọi “thi đầu vào” |
| E-06 | Audio/accessibility preferences cho bé | SUPPORT | Chưa | Tương thích lứa tuổi |
| E-07 | Invitation Acceptance / Parent Activation | CORE | Chưa | Chỉ tài khoản được admin cấp |
| E-08 | Parent Sign-in / Recovery | CORE | Chưa | Không có self-registration công khai |
| E-09 | Invitation Expired / Invalid / Already Used | CORE | Chưa | Hướng xử lý và liên hệ admin |

## 2. Child World

| Screen ID | Màn hình / overlay | UX priority | Figma | Ghi chú |
|---|---|---|---|---|
| C-01 | Child Home / Làng Khởi Đầu | CORE | ✅ Wireframe + concept hi-fi | Hub |
| C-02 | World Map | CORE | ✅ Wireframe + concept hi-fi | Đa môn |
| C-03 | Subject Home / Đảo môn học | CORE | Chưa | Tránh chỉ có Toán |
| C-04 | Module Map / Topic Map | CORE | ✅ Multiplication Map concept | Cần template đa module |
| C-05 | Quest detail / prerequisites | CORE | Chưa | Lộ trình gợi ý/khóa mềm |
| C-06 | Activity intro / hướng dẫn | CORE | Chưa | Mục tiêu nhẹ nhàng |
| C-07 | Mini-game interaction | CORE | ✅ Bridge minigame concept | Multiple activity types |
| C-08 | Hint / feedback / explanation overlay | CORE | Chưa | Đúng/sai/partial |
| C-09 | Completion / reward screen | CORE | Chưa | XP, sao, vật liệu |
| C-10 | Village Builder | CORE | ✅ Wireframe + concept hi-fi | Gắn rewards |
| C-11 | Sổ tay / Journal | SUPPORT | Chưa | Thẻ kỹ năng/huy hiệu, không gây áp lực |
| C-12 | Túi đồ / Inventory | SUPPORT | Chưa | Vật liệu / collectibles |
| C-13 | Nhân vật / Avatar & Milo | SUPPORT | Chưa | Tùy biến |
| C-14 | Recall / review invitation | CORE | Chưa | Review Due độc lập mastery |
| C-15 | Safe pause / checkpoint / resume | CORE | Chưa | Limit/reconnect |
| C-16 | Learn Together indicator / mode | CORE | Chưa | Có người lớn hỗ trợ |
| C-17 | Try higher difficulty / guided mode | SUPPORT | Chưa | Không ép trẻ quá sức |

## 3. Parent Portal

| Screen ID | Màn hình / overlay | UX priority | Figma | Ghi chú |
|---|---|---|---|---|
| P-01 | Overview Dashboard — đa môn | CORE | ✅ Wireframe | Tuyệt đối không KPI phép nhân cấp platform |
| P-02 | Subject detail | CORE | Chưa | Nhiều module |
| P-03 | Module detail / skills | CORE | Chưa | Mastery/confidence/review |
| P-04 | Evidence timeline | SUPPORT | Chưa | Giải thích đề xuất |
| P-05 | Parent Action Center | CORE | Chưa | Need decision / review / suggestion |
| P-06 | Learning path proposal detail & action | CORE | Chưa | Approve/reject/customize |
| P-07 | Child profiles management | CORE | ✅ Wireframe | Multi-profile |
| P-08 | Parent Assessment / edit | CORE | Chưa | Cold start & corrections |
| P-09 | Goals, time & approval settings | CORE | ✅ Wireframe settings | By child/subject/module |
| P-10 | Session History | CORE | Chưa | Filter date/subject |
| P-11 | Session detail with question list | CORE | Chưa | Record & hints |
| P-12 | Question detail / report issue | CORE | Chưa | Feedback types |
| P-13 | Question report status & correction | CORE | Chưa | Before/after impact |
| P-14 | Change participation classification | CORE | Chưa | Independent/assisted/unknown |
| P-15 | Learn Together setup | SUPPORT | Chưa | Parent guidance |
| P-16 | Notifications / correction history | CORE | Chưa | Email + in-app, preferences |
| P-17 | Privacy & Data Rights | CORE | ✅ Wireframe | Export/delete, parental gate |
| P-18 | Guardian roles / permissions | SUPPORT | Chưa | Conflicting guardians |
| P-19 | Parent account/preferences | SUPPORT | Chưa | Accessibility + settings |

## 4. Admin Portal — 12 màn dự kiến

| Screen ID | Màn hình / overlay | UX priority | Figma | Ghi chú |
|---|---|---|---|---|
| A-01 | Admin Sign-in / Session expired | CORE | [Low-fi A-01](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ?node-id=13-8) — APPROVED LOW-FI | Form login đã duyệt; MFA/error states chưa vẽ đủ |
| A-02 | Admin Operations Dashboard | CORE | [Low-fi A-02](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ?node-id=13-28) — APPROVED LOW-FI | Account Admin layout đã duyệt; 3 role variants chưa vẽ |
| A-03 | Parent Accounts: list/search/filter | CORE | [UX spec](./07-admin-parent-account-list-wireframe.md) — **APPROVED HTML LOW-FI; Figma NOT CREATED** | AW-05…AW-08 confirmed; search/filter/sort/pagination/detail preview |
| A-04 | Create Parent Account | CORE | [HTML demo + spec](./08-admin-create-parent-account-wireframe.md) — **APPROVED HTML LOW-FI; Figma NOT CREATED** | AW-09…AW-12 CONFIRMED; email required, display optional, invite toggle, partial success |
| A-05 | Parent Account Detail | CORE | [UX spec + standalone HTML](./09-admin-parent-account-detail-wireframe.md) — **APPROVED HTML LOW-FI; Figma NOT CREATED** | AW-13…AW-16 CONFIRMED: state-aware actions, reason confirmation, audit preview, child data minimization |
| A-06 | Suspend / Restore Confirmation | CORE | [UX spec + HTML demo](./12-admin-suspend-restore-confirmation-wireframe.md) — **APPROVED HTML LOW-FI; Figma NOT CREATED** | AW-22…AW-25 CONFIRMED; offline conflict policy OPEN |
| A-07 | Invitations: status/resend/revoke | CORE | [UX spec + HTML wireframe](./10-admin-invitation-management-wireframe.md) — **APPROVED HTML LOW-FI; Figma NOT CREATED** | AW-17…AW-20 CONFIRMED, AW-21 Layout Stability CONFIRMED |
| A-08 | Admin User & Role Management | SUPPORT | [HTML wireframe + UX spec](./13-admin-user-role-management-wireframe.md) — **APPROVED HTML LOW-FI; Figma NOT CREATED** | AW-26…AW-29 CONFIRMED; multi-role, Super Admin-only management, MFA/conflict/last Super Admin guard |
| A-09 | Permission Change Confirmation | SUPPORT | [HTML wireframe + UX spec](./14-admin-permission-change-confirmation-wireframe.md) — **APPROVED HTML LOW-FI; Figma NOT CREATED** | AW-30…AW-33 CONFIRMED; role diff, reason, acknowledgement, MFA mock, conflict/security states |
| A-10 | Admin Audit History | CORE | [HTML wireframe + UX spec](./15-admin-audit-history-wireframe.md) — **APPROVED HTML LOW-FI; Figma NOT CREATED** | AW-34…AW-37 CONFIRMED: scoped read-only events, filters, sanitized detail, stable table |
| A-11 | Access Recovery & Support | SUPPORT | [HTML wireframe + UX spec](./16-admin-access-recovery-support-wireframe.md) — **APPROVED HTML LOW-FI; Figma NOT CREATED** | AW-38…AW-41 CONFIRMED; scoped recovery tickets, no credential exposure or locked-account bypass |
| A-12 | Content Quality Operations | FUTURE / scope review | [UX spec + V5 HTML](./17-admin-content-quality-operations-wireframe.md) — **APPROVED HTML LOW-FI; Figma NOT CREATED** | AW-42…AW-48 CONFIRMED; correction + impact, report history popup, full audit; not automatically MVP |

**Tổng số màn/overlay được kiểm kê: 57** (9 Entry + 17 Child + 19 Parent + 12 Admin); không đồng nghĩa toàn bộ thuộc MVP.

## 5. UI states/overlays cần cho mọi luồng liên quan

| UX State | Child | Parent | Ghi chú |
|---|---|---|---|
| Initial loading / slow network | ✅ | ✅ | Không gây hiểu nhầm |
| Offline/no connectivity | ✅ | ✅ | Fallback câu đã duyệt |
| Empty/new profile/no evidence | ✅ | ✅ | “Chưa đủ dữ liệu” ≠ “yếu” |
| Permission / adult gate required | ✅ | ✅ | Nội dung chỉ cho người giám hộ |
| Error / retry | ✅ | ✅ | Không mất phiên đã lưu |
| Resume interrupted session | ✅ | ✅ | Không ghi trùng |
| Question under review / invalidated | Ẩn cách phù hợp | ✅ | Trẻ không bị phạt do lỗi hệ thống |
| Learning path approval pending / expired | Nhẹ nhàng | ✅ | Safe alternative khi pending |
| Reward/village update | ✅ | Có thể | Không nhầm game progress với mastery |
| Audio/reduced motion/large touch targets | ✅ | ✅ | Accessibility |
| Content unavailable / curriculum version | ✅ | ✅ | Không tự mở nội dung chưa kiểm duyệt |

## 6. Figma mapping hiện có

**Figma:** https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ

- `01 — WIREFRAMES`: 5 Child World wireframes.
- `02 — HIGH-FIDELITY`: 5 Child World concept screens.
- `03 — DESIGN PRINCIPLES & UI STATES`: tổng hợp UI principles.
- `04 — PARENT PORTAL / WIREFRAMES`: 4 màn phụ huynh (dashboard/settings/profiles/privacy).

**Chưa wireframe** phần lớn màn entry, chi tiết đa môn, question review, adaptive flow, incident handling. Cần hoàn thiện trong giai đoạn 2.

## 7. Những câu hỏi UX cần review

- Màn nào là full-screen, màn nào là modal/overlay? Ít điều hướng đối với bé lớp 1.
- Parent Portal dùng chung ứng dụng hay web riêng?
- Điều hướng quay lại từ mini-game; tránh mất tiến trình; thời gian chờ/giới hạn màn hình.
- Quá nhiều cảnh báo phụ huynh gây overload?
- Multi-profile và parent gate có đủ rõ để tránh dữ liệu sai học sinh?
- Bố trí UI theo nhóm tuổi, giọng nói hỗ trợ và tablet/desktop/mobile responsive.


**GLOBAL UX RULE D-062 (CONFIRMED):** always proactively minimize unexpected Layout Shift across all experiences; context-specific techniques, accessible responsive behavior. [11 — Guideline](./11-global-layout-stability-guidelines.md). **AW-21 CONFIRMED** for stable table action columns; A-07 fully approved as HTML low-fi; AW-17…AW-20 CONFIRMED (D-063).

**Admin-specific UX states:** invitation pending/expired/revoked, account suspended, duplicate email, session expired, insufficient admin permission, audit recorded, send failure/retry, account has in-progress child session. Wireframe chưa có. [Chi tiết Admin Portal](./04-admin-portal.md).


**A-12 V3 (2026-11-27) — DRAFT, NOT APPROVED:** added per-report state transition timeline and on-demand reason modal; full audit browser with 6-event preview, unrestricted historical list, pagination and subject/severity/search filters. **AW-47…AW-48 PROPOSED**, alongside AW-42…AW-46. [Specification](./17-admin-content-quality-operations-wireframe.md). Scope stays FUTURE.


**CURRENT A-12 STATUS (2026-11-27):** V5 HTML LOW-FI **APPROVED**, AW-42…AW-48 **CONFIRMED** under D-069; earlier V3 draft text above is historical. **12/12 Admin Portal low-fi wireframes approved**, Figma A-03…A-12 not yet created. A-12 FUTURE/scope review, no MVP commitment. [Spec](./17-admin-content-quality-operations-wireframe.md).
