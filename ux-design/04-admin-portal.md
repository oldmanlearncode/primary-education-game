# 04 — Admin Portal: Information Architecture, User Flows & Screen Inventory

> **Phase 2 UX Design · 2026-11-24 · DRAFT**  
> **CONFIRMED:** Có Admin Portal; giai đoạn đầu tài khoản phụ huynh do admin cấp phát/quản lý; không mở tự đăng ký công khai.  
> **✅ CONFIRMED 2026-11-24:** Super Admin + Admin có phân quyền; least privilege đối với dữ liệu học sinh; audit thay đổi tài khoản/quyền; hướng kích hoạt bằng lời mời an toàn thay vì gửi mật khẩu; tách quyền account administration và content review.  
> **✅ CONFIRMED:** Hướng xử lý toàn bộ edge case **AD-01…AD-12** (nguyên tắc; chưa chốt exact policy/technical thresholds).  
> **✅ CONFIRMED:** Ma trận phân quyền cụ thể bên dưới được người dùng phê duyệt ngày 2026-11-24, bao gồm các quyền ✅/❌/🔒.  
> **✅ CONFIRMED:** AP-D01…AP-D05 và AP-01…AP-10 cho Account Provisioning UX: phân biệt trạng thái account/invitation, dashboard theo quyền, email bắt buộc duy nhất, invitation mặc định 72 giờ single-use, MFA Super Admin. Xem [05 — Account Provisioning](./05-admin-account-provisioning.md).  
> **OPEN:** Các ô 🔒, kênh gửi lời mời, MFA method, kỹ thuật triển khai và wireframe chi tiết.

## 0. Admin decisions — CONFIRMED

| ID | Quyết định | Trạng thái |
|---|---|---|
| ADM-01 | **Super Admin + Admin có phân quyền**: có vai trò quản trị cao nhất và vai trò quản trị được cấp quyền theo nhiệm vụ. Số lượng Super Admin và quyền từng vai trò chưa chốt. | **CONFIRMED** |
| ADM-02 | **Least privilege / tách quyền truy cập dữ liệu trẻ**: quản trị tài khoản không mặc nhiên đọc toàn bộ thông tin học tập của học sinh. | **CONFIRMED** |
| ADM-03 | **Audit trail**: ghi nhận ai tạo, khóa, khôi phục tài khoản hoặc thay đổi quyền, cùng thời điểm và đối tượng tác động. | **CONFIRMED** |
| ADM-04 | **Secure account activation bằng lời mời thay vì gửi mật khẩu** là hướng UX đã được chọn. Kênh gửi, expiry, token design và recovery vẫn cần quyết định. | **CONFIRMED — direction** |
| ADM-05 | **Tách account admin và content reviewer**: quyền quản lý người dùng không tự động kèm quyền duyệt câu hỏi/chương trình học. | **CONFIRMED** |

## 0.1. Permission Architecture — ADM-D01…ADM-D04 CONFIRMED (2026-11-24)

| ID | Quyết định đã chốt | Trạng thái |
|---|---|---|
| **ADM-D01** | **Bốn role ban đầu:** `SUPER_ADMIN`, `ACCOUNT_ADMIN`, `CONTENT_REVIEWER`, `SUPPORT_OPERATOR`. Role đảm nhiệm nghiệp vụ riêng; role Super Admin không mặc nhiên được đọc dữ liệu học tập nhạy cảm. | **CONFIRMED** |
| **ADM-D02** | **RBAC + Resource Scope + Context Policy**: quyền thao tác còn phụ thuộc tài nguyên cụ thể, phạm vi quản lý và điều kiện nghiệp vụ. | **CONFIRMED** |
| **ADM-D03** | Một tài khoản quản trị **có thể giữ nhiều role**; quyền tổng hợp vẫn phải kiểm tra resource scope, context và giới hạn dữ liệu. | **CONFIRMED** |
| **ADM-D04** | **Chỉ Super Admin được quản lý role/tài khoản Admin**; quyền nhạy cảm với dữ liệu học sinh yêu cầu kiểm tra chính sách riêng, không tự động suy từ role. | **CONFIRMED** |

**Để tránh nhầm:** bốn quyết định là nguyên tắc kiến trúc phân quyền. Các quyền cụ thể theo từng hành động trong các bảng bên dưới là **PROPOSED** cho UX review, chưa được phê duyệt.

### Permission matrix — ✅ CONFIRMED (2026-11-24)

Ký hiệu đã chốt: ✅ được phép theo vai trò (vẫn phải qua kiểm soát bảo mật chung); ❌ không được phép; 🔒 chỉ được phép sau khi thỏa điều kiện authorization/resource scope/context tương ứng. **Không được coi 🔒 là quyền mặc định.**

| Hành động | SUPER_ADMIN | ACCOUNT_ADMIN | CONTENT_REVIEWER | SUPPORT_OPERATOR |
|---|:---:|:---:|:---:|:---:|
| Tạo tài khoản phụ huynh | ✅ | ✅ | ❌ | ❌ |
| Gửi lại lời mời | ✅ | ✅ | ❌ | 🔒 |
| Khóa/khôi phục tài khoản phụ huynh | ✅ | ✅ | ❌ | ❌ |
| Tạo/vô hiệu hóa tài khoản Admin | ✅ | ❌ | ❌ | ❌ |
| Cấp/thu hồi role Admin | ✅ | ❌ | ❌ | ❌ |
| Xem và triage lỗi câu hỏi | 🔒 | ❌ | ✅ | 🔒 |
| Duyệt nội dung giáo dục | 🔒 | ❌ | ✅ | ❌ |
| Xem dữ liệu học tập trẻ | 🔒 | ❌ | 🔒 | 🔒 |
| Sửa trực tiếp raw attempts hoặc mastery | ❌ | ❌ | ❌ | ❌ |
| Xem audit theo phạm vi | 🔒 | 🔒 | 🔒 | 🔒 |

Không được coi vai trò quản trị cao nhất là quyền vượt mọi chính sách đối với dữ liệu trẻ. Việc phê duyệt học liệu cần đúng thẩm quyền chuyên môn. Server cần thực thi permission/scope/context thực sự — ẩn nút trong UI không đủ để bảo vệ.

### Edge cases AD-01…AD-12 — ✅ CONFIRMED (2026-11-24)

| ID | Trường hợp | Phương án đang đề xuất | Trạng thái |
|---|---|---|---|
| AD-01 | Super Admin cuối cùng bị khóa/mất quyền | Bảo vệ hệ thống khỏi mất Super Admin cuối cùng; recovery có kiểm soát | **CONFIRMED** |
| AD-02 | Admin tự nâng role | Không cho tự nâng quyền | **CONFIRMED** |
| AD-03 | Một Admin có nhiều role | Gộp quyền nhưng vẫn kiểm tra scope/context | **CONFIRMED** |
| AD-04 | Hai Admin sửa đồng thời một account | Version check / conflict handling, tránh ghi đè | **CONFIRMED** |
| AD-05 | Account bị khóa khi bé đang chơi | Kết thúc phiên ở checkpoint an toàn theo risk policy | **CONFIRMED** |
| AD-06 | Invitation được sử dụng lần hai | Từ chối dùng lại; hỗ trợ tạo lời mời mới | **CONFIRMED** |
| AD-07 | Invitation hết hạn | Từ chối kích hoạt và cho admin gửi lại | **CONFIRMED** |
| AD-08 | Support xem dữ liệu ngoài ticket | Từ chối theo resource scope; audit truy cập | **CONFIRMED** |
| AD-09 | Reviewer sửa quyền account | Từ chối thao tác ngoài quyền | **CONFIRMED** |
| AD-10 | Admin bị thu quyền trong phiên đăng nhập | Revalidate quyền, vô hiệu session khi cần | **CONFIRMED** |
| AD-11 | Admin khóa nhầm account | Quy trình phục hồi có lý do và audit | **CONFIRMED** |
| AD-12 | Yêu cầu xóa dữ liệu của trẻ | Tách thành privacy workflow có xác minh, không xóa tùy tiện | **CONFIRMED** |

## 1. Product boundaries

Little Explorers gồm ba trải nghiệm:

```text
ADMIN PORTAL (quản trị / cấp phát)
      │ tạo tài khoản / lời mời phụ huynh
      ▼
PARENT PORTAL (quản lý con / học tập)
      │ tạo child profiles / mục tiêu / parent assessment
      ▼
CHILD WORLD (học / khám phá)
```

- Admin **quản lý tài khoản và truy cập**, không tự động được quyền xem toàn bộ lịch sử học tập nhạy cảm của trẻ nếu không có mục đích/quyền phù hợp.
- Parent vẫn có quyền tạo/sửa child profiles **trong tài khoản đã được cấp phát**, trừ trường hợp quản trị viên thu hồi quyền hoặc chính sách đã đặt.
- **Không public self-registration, không guest preview** trong phạm vi vận hành ban đầu; nghiên cứu mở lại khi sản phẩm/hạ tầng sẵn sàng.
- Có thể dùng cùng hệ thống backend nhưng **khác giao diện và ranh giới quyền**. Không chốt kiến trúc deploy.

## 2. Admin sitemap (đề xuất)

```text
ADMIN PORTAL
├── Admin Sign-in / Session / Account Recovery
├── Dashboard & Operations
│   ├── Total parent accounts / statuses
│   ├── Pending invitations / access requests
│   └── Operational notices (không hiển thị PII trẻ không cần thiết)
├── Account Management
│   ├── List/search/filter parent accounts
│   ├── Create parent account / send invitation
│   ├── Parent account details / linked child count
│   ├── Activate / suspend / restore (permission controlled)
│   ├── Resend / revoke invitation
│   └── Access recovery (không xem mật khẩu)
├── Roles & Access Policies
│   ├── Admin user accounts and roles
│   ├── Role permissions / least privilege
│   └── Access changes & audit
├── Support & Audit
│   ├── Activity / change history
│   ├── Failed invitations / blocked users
│   └── Support actions (sensitive data requires separate approval)
├── Content Quality Operations (tích hợp sau / scope pending)
│   ├── Question reports / triage / quarantine
│   └── Content reviewers / status
└── Admin Settings
    ├── Security (MFA/session policy – proposal)
    └── Notification / operational preferences
```

**CONFIRMED:** Không gộp quyền tạo tài khoản với quyền duyệt kiến thức; **Super Admin + delegated Admin** là cấu trúc role cơ bản. **PROPOSED:** cụ thể hóa Account Admin / Content Reviewer / Support Operator, phân quyền đến từng action và giới hạn truy cập dữ liệu trẻ.

## 3. Admin flows (draft)

### A-F01 — Admin provision parent account
```text
Admin sign-in → Parent accounts → New parent
→ Nhập email/kênh liên hệ tối thiểu → Kiểm tra trùng
→ Tạo trạng thái INVITED/PENDING_ACTIVATION
→ Gửi lời mời kích hoạt an toàn (đề xuất)
→ Parent activate credentials → Login → Parent Onboarding
→ Child Profile → General Assessment [optional] → Goals → Child World
```
**Edge:** email đã dùng, lỗi gửi lời mời, lời mời hết hạn, kích hoạt trùng, người dùng chưa nhận được mail. Không gửi mật khẩu plaintext.

### A-F02 — Admin search, view, suspend / reactivate
```text
Admin sign-in → Search/filter account → Detail
→ Choose permitted action → Reason / confirm
→ Apply → Audit record → Notify parent if appropriate
```
**Edge:** suspend account khi trẻ đang chơi, account có nhiều child profiles, lệnh bị gửi trùng, admin tự khóa chính mình, phản hồi yêu cầu truy cập dữ liệu.

### A-F03 — Invitation recovery
```text
Pending invitation → Resend / revoke / renew
→ Previous token invalidated if needed → Audit
→ parent activates only latest valid invitation
```

### A-F04 — Admin roles and access changes
```text
Authorized admin → Admin users → Select user
→ Request role change → Confirm authorization
→ Apply → Re-evaluate permissions / sessions → Audit
```
**Edge:** người quản trị cuối cùng mất quyền; quyền hỗ trợ xem dữ liệu trẻ không được cấp ngầm.

### A-F05 — Account support without changing learning evidence
```text
Admin → Parent account issue → Verify request
→ Restricted support action → Audit / notify
```
Admin thao tác khắc phục truy cập **không tự sửa mastery / classification / answer events**; parent correction và content-incident đã có luồng riêng.

## 4. Screen inventory (new, proposed)

| ID | Screen / Overlay | UX priority | Wireframe |
|---|---|---|---|
| A-01 | Admin Sign-in / session expired | CORE | Chưa |
| A-02 | Admin Dashboard | CORE | Chưa |
| A-03 | Parent Account List / Search / Filters | CORE | Chưa |
| A-04 | Create Parent Account / Invitation | CORE | Chưa |
| A-05 | Parent Account Detail | CORE | Chưa |
| A-06 | Suspend / Restore Confirmation | CORE | Chưa |
| A-07 | Invitation Status / Resend / Revoke | CORE | Chưa |
| A-08 | Admin Users / Roles | SUPPORT | Chưa |
| A-09 | Permission Change Detail / Confirmation | SUPPORT | Chưa |
| A-10 | Audit History / Activity | CORE | Chưa |
| A-11 | Access Recovery / Support | SUPPORT | Chưa |
| A-12 | Content Quality Operations entry | FUTURE / scope review | Chưa |

**Entry/invite screens to add for parent**:
- `E-07` — Parent Invitation Acceptance / Activation
- `E-08` — Parent Sign-in / Session Recovery (no public sign-up)
- `E-09` — Invalid / Expired / Already Used Invitation

## 5. Access & UX safety (CONFIRMED principles; details proposed)
- Server-side role enforcement; hide buttons alone does not protect access.
- No public registration endpoint in initial phase.
- Admin's invitation token expires, single use and revocable; never expose account credentials in logs/emails.
- Prefer MFA and extra verification for privilege changes.
- **CONFIRMED:** audit ai tạo/khóa/khôi phục/thay quyền tài khoản (actor, timestamp, target; lý do đề xuất). Tối thiểu hóa PII của trẻ.
- Rate limits, idempotency, and retry for invitation creation.
- Suspend/revoke semantics and handling in-progress child sessions need policy.
- Distinguish parent vs admin access and data permissions, including later guardian roles.
- Plan transition for public registration **without** re-creating existing parent accounts.

## 6. OPEN for detailed admin UX (principles ADM-01…05 already CONFIRMED)
1. Đã chốt **bốn role**, chỉ Super Admin quản lý role Admin, RBAC + scope/context và hỗ trợ multi-role. Còn OPEN: số lượng Super Admin, bootstrap, cơ chế khôi phục quản trị viên cuối cùng và **điều kiện cụ thể để thực thi từng ô 🔒 của matrix đã CONFIRMED**.
2. **AP-D04 CONFIRMED:** activation invitation mặc định 72 giờ (configurable), single-use; account/invitation/delivery status tách nhau. Còn OPEN: kênh gửi/đơn vị cung cấp, chính sách resend chi tiết và bảo mật triển khai.
3. Whether parent can recover password independently after admin provisioning.
4. Who can link a child profile to another guardian?
5. Đã CONFIRMED hướng kết thúc phiên an toàn khi khóa tài khoản (AD-05); còn OPEN: chi tiết xử lý session đang chạy, offline, đồng bộ và mức độ khẩn cấp.
6. Đã CONFIRMED từ chối truy cập ngoài phạm vi ticket (AD-08); còn OPEN: dữ liệu nào được phép xem trong ticket, thời hạn truy cập, approval và privacy/legal review.
7. Whether Content Reviewer belongs inside same admin app or separate console.

These questions do **not** reopen the confirmed decision: **admin-provisioned accounts first, no open sign-up at launch**.


## 7. Phase 2.4 — Account Provisioning UX decisions

**AP-D01…AP-D05 + AP-01…AP-10 đã CONFIRMED** (2026-11-24). Trạng thái tài khoản và invitation độc lập; form tạo parent account chỉ bắt buộc email; dashboard theo permission; invitation hết hạn mặc định 72 giờ (có thể cấu hình), single-use; MFA bắt buộc cho Super Admin, Admin khác MFA tối thiểu khi thao tác nhạy cảm. Mười trường hợp AP-01…10 có hướng xử lý được chấp thuận. **Nguồn chuẩn:** [05 — Admin Account Provisioning UX & Parent Activation](./05-admin-account-provisioning.md).


## 8. Wireframe update — A-01 & A-02 (2026-11-24)

**Initial editable Figma low-fi frames created:** [A-01 Admin Login + A-02 Admin Dashboard](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ?node-id=13-4). [UX interaction specification](./06-admin-login-dashboard-wireframes.md). **A-01 and A-02 low-fi layouts APPROVED by user 2026-11-24**; MFA, error, and other-role UI variants still pending. No product code/prototype created.


## 9. A-03 Parent Account List (2026-11-24)

[Đặc tả UX A-03](./07-admin-parent-account-list-wireframe.md) và bản HTML độc lập đã được tạo để review. **A-03 HTML low-fi APPROVED 2026-11-24, nhưng không phải Figma frame**. Đã xác định tìm kiếm email/ID, lọc Account Status (khác Invitation Status), sort/pagination, bảng tối thiểu và View Detail. **AW-05…AW-08 CONFIRMED**.


## 10. A-04 Create Parent Account — HTML draft (2026-11-24)

[UX spec](./08-admin-create-parent-account-wireframe.md). HTML interaction wireframe **APPROVED by user 2026-11-24**, not yet in Figma due to MCP call limit. **AW-09…AW-12 CONFIRMED** (with underlying AP-D03/AP-02). No product code or email backend.


## 11. A-05 Parent Account Detail — HTML draft (2026-11-24)

[A-05 UX specification](./09-admin-parent-account-detail-wireframe.md). Standalone HTML interaction draft created with state-aware Account actions, reason confirmation, audit preview, invitation summary and safe-session warning. **AW-13…AW-16 CONFIRMED; A-05 HTML low-fi APPROVED by user 2026-11-24**. **Figma frame NOT CREATED**, no backend implementation.


## 12. A-07 Invitation Management — HTML draft (2026-11-24)

[A-07 UX spec](./10-admin-invitation-management-wireframe.md). Interactive HTML mock exists: invitation list, distinct account/token/delivery statuses, controlled resend/revoke, reason confirmation, role/scope simulator, mock audit and negative states. **AW-17…AW-20 CONFIRMED, A-07 HTML low-fi APPROVED (2026-11-24)**. **Figma A-07 NOT CREATED**, no real mail, tokens, backend authorization or persistence.


## 13. A-06 Suspend / Restore Confirmation — HTML draft (2026-11-24)

[UX specification](./12-admin-suspend-restore-confirmation-wireframe.md). A-06 is a confirmation state launched from A-05, with target/status, mandatory reason, acknowledgement, action audit preview and test scenarios. **AW-22…AW-25 CONFIRMED, A-06 HTML low-fi APPROVED (2026-11-24)**. Offline synchronization response in the demo is illustrative and **not a confirmed final policy**. Figma frame not created; no backend action exists.


## 14. A-06 + A-07 approval update (2026-11-24)

User explicitly approved both wireframes and the associated AW suggestions. **A-07 / AW-17…20: CONFIRMED (D-063). A-06 / AW-22…25: CONFIRMED (D-064).** Both remain HTML low-fi only; Figma frames not created. **Offline unsynced learning-session handling remains OPEN** and must not be treated as approved simply because the warning UX was approved. Next: A-08 Admin User & Role Management.


## 15. A-08 Admin Users & Roles — HTML draft (2026-11-24)

[UX spec — A-08](./13-admin-user-role-management-wireframe.md). Standalone interactive HTML low-fi created: Super Admin-only create/disable and assign/revoke Admin roles, multi-role, target confirmation, reason/audit mock, viewer role simulation, last active Super Admin guard, concurrency/MFA/permission-revoked states. **AW-26…AW-29 CONFIRMED, A-08 HTML low-fi APPROVED (2026-11-25)**. **Demo does not set final Admin activation or MFA technical policies.** Figma A-08 NOT CREATED; no actual backend or audit persistence.


## 16. A-08 approval — 2026-11-25

User approved the **A-08 HTML low-fi wireframe** and **AW-26…AW-29** (D-065). This does not approve unfinished A-09 or close technical OPEN items for Admin invitations/MFA/last Super Admin recovery. [Specification](./13-admin-user-role-management-wireframe.md).
