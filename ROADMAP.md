# Little Explorers — Development Roadmap

> **Cập nhật:** 2026-11-24 · Roadmap cấp sản phẩm, **không phải sprint plan/timeline hoặc cam kết release**.
>
> **Trạng thái:** Giai đoạn 1 đã được người dùng xác nhận hoàn tất ở mức **Product Design / Product Discovery (concept decisions)**. **Giai đoạn 2 — UX Design: IN PROGRESS**. Chưa có sản phẩm chạy, chưa xây đủ prototype hay MVP.

## 7 giai đoạn phát triển (theo thứ tự đã thống nhất)

| Giai đoạn | Tên | Phạm vi | Trạng thái | Sản phẩm đầu ra / Điều kiện hoàn tất |
|---|---|---|---|---|
| **1** | **Product Design** | Tài liệu yêu cầu, mục tiêu học tập, game loop | ✅ **COMPLETED — Discovery baseline** | Có tầm nhìn đa môn, lựa chọn game loop, Adaptive Learning, Parent-Guided Learning, quyết định và edge cases ghi tại `idea-summarize/`. Chi tiết định lượng/thuật toán chưa phải quyết định cuối. |
| **2** | **UX Design** | User flow, sitemap, wireframe **toàn bộ màn hình** | 🟡 **IN PROGRESS** | Có sitemap đầy đủ cho Child World/Parent Portal; user flow chính & ngoại lệ; inventory mọi màn hình + UI states; wireframe/interaction được rà soát. |
| **3** | **Visual Design** | Design system, nhân vật, bản đồ, UI kit | ⬜ **NOT STARTED** | Tokens, typography, assets, Milo, bản đồ, component states/responsive, accessibility; Figma hi-fi hiện có là exploration, không đồng nghĩa hoàn tất giai đoạn. |
| **4** | **Prototype** | Bản tương tác của **Rừng Bảng Nhân 2** | ⬜ **NOT STARTED** | Prototype có thể trải nghiệm luồng học/ôn/tặng thưởng/xây làng, gồm trường hợp đúng/sai/gợi ý. |
| **5** | **Learning Design** | Ngân hàng câu hỏi, gợi ý, thuật toán ôn tập | ⬜ **NOT STARTED** | Skill blueprint, nội dung đã duyệt, assessment/recall policy được kiểm chứng; lựa chọn rule-based/BKT/IRT hay kết hợp khi đủ dữ liệu. |
| **6** | **Playtesting** | Kiểm thử với học sinh ở các nhóm tuổi khác nhau | ⬜ **NOT STARTED** | Kế hoạch và kết quả thử nghiệm về hiểu bài, thao tác, sự phù hợp lứa tuổi, phụ huynh, safety; sửa thiết kế dựa trên dữ liệu. |
| **7** | **MVP** | Module **Phép Nhân**, phần thưởng, ngôi làng và phụ huynh | ⬜ **NOT STARTED** | Phiên bản tích hợp thử nghiệm đáp ứng trải nghiệm học–chơi–phụ huynh; tiêu chí phát hành được xác định sau. |

## Nguyên tắc phạm vi

- **Platform vision**: học sinh Việt Nam lớp **1–5**, nhiều môn và module. **Phép Nhân là module đầu tiên**, không phải toàn bộ sản phẩm.
- Các giai đoạn là **trình tự ưu tiên sản phẩm**; có thể quay lại sửa UX/Product Design khi kiểm thử cho thấy vấn đề, nhưng phải cập nhật decision log.
- **Figma hiện có** chứa 5 child screens (wireframe + concept hi-fi), 4 parent portal wireframes. Chúng là **tài sản đầu vào giai đoạn 2**, chưa phải bộ wireframe đầy đủ.
- Các ý tưởng AI/adaptive/parent approval được **CONFIRMED ở mức nguyên tắc**; định lượng, chi tiết privacy/legal, thuật toán và phần nào có trong MVP vẫn phải được đặc tả và đánh giá.
- Mỗi giai đoạn không mặc nhiên có thời hạn; không suy ra đã viết code từ việc có tài liệu.

## Giai đoạn đang thực hiện: 2 — UX Design

Bắt đầu tại [ux-design/README.md](./ux-design/README.md).

### Đầu ra cần phát triển
1. **Information Architecture / Sitemap**: toàn bộ trải nghiệm của bé và phụ huynh.
2. **User flows**: admin provisioning / activation, onboarding, discovery/cold start, chọn môn và nhiệm vụ, làm bài, chơi lại, recall, reward, parent review, approval, session correction, incident/correction, multiple profiles, time limit.
3. **Screen inventory & states**: danh sách màn hình, modal, overlay, empty/loading/offline/error/permission, theo nhóm tuổi và khả năng tiếp cận.
4. **Wireframes**: hoàn thiện những màn còn thiếu trong Figma, duy trì mapping screen ↔ flow ↔ chức năng.
5. **UX review**: xem lại với chủ dự án trước khi khóa baseline chuẩn bị Visual Design.

## Tài liệu tham khảo
- [Idea knowledge base](./idea-summarize/README.md)
- [Confirmed product decisions](./idea-summarize/06-decisions-and-open-questions.md)
- [Consolidated review](./idea-summarize/08-consolidated-review.md)
- [Learning Evidence & Mastery](./idea-summarize/10-learning-evidence-and-mastery-assessment.md)
- [Mastery Assessment Engine](./idea-summarize/11-mastery-assessment-engine-and-learning-decisions.md)
- [Figma](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ)

### Cách cập nhật Roadmap
Chỉ đổi `IN PROGRESS` thành `COMPLETED` khi chủ dự án xác nhận điều kiện hoàn tất. Các thay đổi phạm vi phải được phản ánh vào tài liệu UX và decision log.


### UX scope update — 2026-11-24

**Đã CONFIRMED:** Giai đoạn đầu do **Admin cấp và quản lý tài khoản**, không mở public self-registration/guest preview. UX Design mở rộng thêm **Admin Portal** (account management, roles, audit, support) và các flow kích hoạt tài khoản được cấp. Xem [Admin Portal](./ux-design/04-admin-portal.md). Bản chi tiết admin vẫn cần review và wireframe; **Phase 2 IN PROGRESS**, Phase 1 status không thay đổi.
