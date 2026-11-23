# 06 — Decision Log, giả thuyết và câu hỏi mở

> **Nguồn tra cứu đầu tiên trước mỗi buổi thảo luận mới.**  
> Mốc ghi nhận: **2026-11-23**. Chỉ gọi là **CONFIRMED** khi người dùng đã đồng ý rõ ràng; những suy luận hoặc tư vấn của trợ lý là **PROPOSED**.

## A. Đã thống nhất (CONFIRMED)

| ID | Quyết định | Căn cứ cuộc thảo luận / hệ quả |
|---|---|---|
| D-001 | Đối tượng: học sinh tiểu học **lớp 1–5** | UX phải phù hợp nhiều nhóm tuổi |
| D-002 | Sản phẩm **đa môn học, nhiều module mỗi môn** | Toán, Tiếng Việt, Tự nhiên và Xã hội…; không mặc định là app phép nhân |
| D-003 | **Module đầu tiên: Phép nhân** | Dùng để thử nghiệm mô hình, không phải toàn bộ platform |
| D-004 | Chọn gameplay **A (phiêu lưu trên bản đồ) + một phần C (xây làng làm phần thưởng dài hạn)** | Bản đồ là lõi; làng là động lực phụ |
| D-005 | **Khám phá có định hướng (phương án C)** | Trẻ chọn môn/vùng tự do; trong module hệ thống định hướng theo nền tảng và năng lực |
| D-006 | Có **dashboard và cấu hình phụ huynh** | Đã phác thảo 4 wireframe Figma |
| D-007 | Dashboard **tổng quan phải đa môn**, không có KPI riêng phép nhân | Chi tiết phép nhân chỉ ở cấp Toán → Module Phép nhân |
| D-008 | Đang trong giai đoạn **ý tưởng**, chưa phải plans | Lưu trong `idea-summarize/`, không đưa thành kế hoạch/commit giao hàng |

## B. Ý tưởng do người dùng nêu, đang cần chốt cách thực hiện

| ID | Ý tưởng | Trạng thái |
|---|---|---|
| U-001 | Khi bé mở/chơi lại bài, dùng **AI (ChatGPT, Gemini hoặc Claude)** để tạo bộ câu hỏi phong phú và **phù hợp năng lực hiện tại** | **USER IDEA — cơ chế cụ thể chưa chốt** |
| U-002 | Duy trì hồ sơ ý tưởng trong GitHub repo suốt dự án để tránh quên/nhầm | **CONFIRMED** |

## C. Đề xuất cần quyết định (PROPOSED)

| ID | Đề xuất | Vấn đề cần chốt |
|---|---|---|
| P-001 | Learning Loop: Discover → Understand → Practice → Apply → Recall | Các giai đoạn bắt buộc hay tùy môn? |
| P-002 | Tách tiến trình Adventure / Learning / Village | Chỉ số và ranh giới dữ liệu? |
| P-003 | Mini-game templates dùng chung đa môn | Nội dung nào đòi mini-game riêng? |
| P-004 | Adaptive Learning Engine chọn skill và độ khó, AI chỉ tạo biến thể câu hỏi | Ranh giới AI vs engine? |
| P-005 | Hybrid: curated + AI validated pool + on-demand khi thiếu | Có thay ý tưởng AI gọi mỗi lần không? |
| P-006 | Question validator nhiều lớp + review chuyên môn | Ai duyệt, kiểm tra được đến đâu? |
| P-007 | Multi-provider OpenAI/Gemini/Claude | Có cần ở phiên bản đầu, cách chọn provider? |
| P-008 | Ôn tập ngắt quãng, trạng thái thành thạo theo nhiều lần thử | Chọn thuật toán, lịch, tiêu chí đánh giá? |
| P-009 | MVP/vertical slice ở Rừng Bảng Nhân 2 | Mấy mini-game, có xây làng cơ bản không? |
| P-010 | Tablet landscape, hoạt hình 2D cozy fantasy | Kiểm thử thiết bị/thẩm mỹ theo tuổi |
| P-011 | Nhân vật đồng hành Milo | Kiểu nhân vật và nội dung thoại |
| P-012 | XP/sao/huy hiệu/vật liệu, không phạt sai, tránh gây áp lực | Cân bằng phần thưởng |
| P-013 | Vai trò quản trị nội dung/curriculum review | Cần CMS ở mức nào? |
| P-014 | Dashboard ba cấp: tổng quan → môn → module | Chỉ số và cấu trúc báo cáo |
| P-015 | Học theo năng lực thay vì bám cứng lớp | Placement test, prerequisite, điều chỉnh |
| P-016 | Data minimization khi gọi AI, parental gate | Yêu cầu pháp lý/quyền riêng tư cần xác minh |

## D. Các câu hỏi chưa có đáp án (OPEN)

### Sản phẩm / giáo dục
1. Curriculum theo chương trình Việt Nam phiên bản nào, ai phê duyệt nội dung từng môn?
2. Mức tự do chuyển môn và điều kiện khóa/mở nhiệm vụ theo skill?
3. Công thức xác định mức hiểu/vận dụng/ghi nhớ? Các môn sử dụng thang khác nhau ra sao?
4. Khả năng hỗ trợ học sinh đặc thù, giọng nói, tablet/mobile/desktop và offline?
5. Đo học thật so với học thuộc câu trả lời thế nào?

### AI / ngân hàng câu hỏi
6. **Mỗi lượt chơi có gọi AI trực tiếp** hay **hybrid pre-generated pool**?
7. Phê duyệt câu hỏi do AI sinh, cách xử lý sai/mơ hồ/không hợp lứa tuổi?
8. Cách giới hạn cost/latency khi lượng học sinh tăng?
9. Lưu prompt/model provenance, cơ chế feedback/loại bỏ câu hỏi lỗi?
10. Không gửi PII trẻ; điều khoản/độ tuổi/đồng ý của phụ huynh với từng provider?
11. Gợi ý đáp án và chấm tự luận/đọc hiểu/hoạt động mở thế nào?

### Gameplay / trải nghiệm
12. Thưởng cho tiến bộ vs. tránh thưởng quá nhiều cho lặp màn?
13. Bao nhiêu chức năng xây làng trong thử nghiệm đầu tiên?
14. Cách dừng phiên chơi an toàn khi phụ huynh giới hạn thời lượng?
15. Có hoạt động đa môn/cross-skill không, và ai quản lý prerequisite?

### Thiết kế / sản phẩm vận hành
16. Dashboard cấp môn/module và heatmap sẽ ra sao?
17. Cách quản lý nhiều hồ sơ trẻ và quyền truy cập của phụ huynh?
18. Công cụ biên tập nội dung cần ở giai đoạn nào?
19. Định nghĩa MVP, tiêu chí kết thúc thử nghiệm, số lượng trẻ/phụ huynh tham gia?
20. Mô hình thu phí/phi thương mại, kiến trúc kỹ thuật và lịch phát triển: **chưa bàn/chưa chốt**.

## E. Những giả thuyết cần kiểm chứng (EXPERIMENT)
- E-001: bản đồ phiêu lưu làm trẻ hào hứng tham gia học.
- E-002: xây làng tăng động lực dài hạn mà không kéo dài thời gian sử dụng không lành mạnh.
- E-003: học qua tương tác tăng hiểu/khả năng vận dụng.
- E-004: recall ngắt quãng giúp giữ kiến thức lâu hơn.
- E-005: câu AI đa dạng giúp giảm học thuộc văn bản/thứ tự câu hỏi mà vẫn đo đúng skill.
- E-006: phụ huynh hiểu dashboard đa môn và đưa ra hỗ trợ phù hợp.

## F. Cách cập nhật decision log
Mỗi lần có quyết định mới: thêm ID, ngày, người quyết định, trạng thái và lý do; nếu thay đổi quyết định cũ hãy đánh dấu **SUPERSEDED → ID mới**. Không chuyển đề xuất thành CONFIRMED vì trợ lý đã từng gợi ý hoặc vì có UI minh họa.

**Đề xuất trọng tâm thảo luận tiếp:** adaptive learning, quy trình tạo/kiểm duyệt câu AI, cách định nghĩa năng lực cho từng môn, game loop và ranh giới MVP.


## G. Bổ sung 2026-11-23 — Parent-Guided Adaptive Learning

> Đây là **USER IDEA + PROPOSED**, không tự động coi các chi tiết thiết kế là CONFIRMED. Xem [tài liệu chuyên đề 07](./07-parent-guided-adaptive-learning.md).

| ID | Ý tưởng / vấn đề | Trạng thái |
|---|---|---|
| U-003 | Phụ huynh trả lời câu hỏi khi tạo hồ sơ để xác lập năng lực ban đầu, tránh bắt đầu quá thấp; kết quả được điều chỉnh theo năng lực thực tế | **USER IDEA — cần chốt cách đánh giá** |
| U-004 | Phụ huynh review câu hỏi con đã gặp, báo mơ hồ/đáp án sai/nội dung chưa đúng; là một lớp phản hồi bổ sung | **USER IDEA — cần quy trình xác minh** |
| U-005 | Phụ huynh tham gia xác nhận đề xuất nâng/hạ độ khó; cân nhắc hết hạn 3–7 ngày, auto xử lý và audit log | **USER IDEA — chính sách auto-accept CHƯA CHỐT** |
| U-006 | Phụ huynh tham gia học cùng trẻ, hỗ trợ tiếp cận thử thách nhỉnh hơn mức đang tự làm được | **USER IDEA** |
| P-017 | Parent Assessment + Discovery Assessment: khai báo ban đầu là thông tin tham khảo, có bằng chứng trực tiếp kiểm chứng | **PROPOSED** |
| P-018 | Parent Question Report → review/quarantine/versioning → hiệu chỉnh learning evidence nếu câu bị xác nhận lỗi | **PROPOSED** |
| P-019 | Parent approval theo 3 mức ảnh hưởng và chế độ parental control; im lặng không mặc nhiên là đồng ý nếu chưa opt-in | **PROPOSED** |
| P-020 | Learn Together: phân biệt năng lực độc lập và có hỗ trợ | **PROPOSED** |
| P-021 | Parent Action Center với hành động cần xác nhận/gợi ý/nhắc nhẹ, không spam | **PROPOSED** |

**Cần chốt ưu tiên:** cấu hình mức phê duyệt, deadline và hành vi khi hết hạn; xác định nội dung cần kiểm duyệt thủ công; cách cập nhật lại các kết quả bị ảnh hưởng bởi câu hỏi lỗi; nội dung onboarding cho phụ huynh.


## H. Quyết định xác nhận 2026-11-23

| ID | Quyết định | Trạng thái | Hệ quả |
|---|---|---|---|
| D-009 | **Parent-Guided Learning Path — phương án C:** Phụ huynh định hướng mục tiêu; Learning Engine duy trì trải nghiệm phù hợp và hỗ trợ khi cần. | **CONFIRMED (người dùng đồng ý rõ)** | Trẻ có thể khám phá nâng cao có hỗ trợ, nhưng bằng chứng `SUPPORTED` không tự đổi thành thành thạo `INDEPENDENT`. Cơ chế approval, timeout, quyền phụ huynh vẫn **OPEN**. |

Xem [08 — Consolidated Review](./08-consolidated-review.md) để duyệt tập trung các vấn đề chưa quyết định và edge case.
