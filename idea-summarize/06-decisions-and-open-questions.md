# 06 — Decision Log, giả thuyết và câu hỏi mở

> **Nguồn tra cứu đầu tiên trước mỗi buổi thảo luận mới.** **CẬP NHẬT 2026-11-23: mục J và tài liệu 08 là trạng thái quyết định hiện hành; các bảng PROPOSED/OPEN ở mục C–I là snapshot lịch sử trước lúc duyệt.**  
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


## I. Bổ sung EC-02 / EC-03 / EC-12 — 2026-11-23

**Người dùng đồng ý về định hướng** các đề xuất đã thảo luận (Adaptive Learning, Parent-Guided option C) và nêu ba điều chỉnh cụ thể; các tiêu chí/ngưỡng vận hành còn OPEN. Chi tiết trong [09 — Session Correction, Question Incident & Response Time](./09-session-correction-question-incidents-and-response-time.md).

| ID | Quyết định ở cấp ý tưởng | Trạng thái |
|---|---|---|
| D-010 | **EC-02:** Phụ huynh có quyền sửa phân loại `Tự học / Có hỗ trợ` của phiên, dữ liệu phiên được lưu và có lịch sử chỉnh sửa; phụ huynh chịu trách nhiệm xác nhận ngữ cảnh tham gia. | **CONFIRMED — chủ trương người dùng**; quy tắc re-evaluate/giới hạn quyền chi tiết vẫn OPEN |
| D-011 | **EC-03:** Khi câu hỏi đã dùng bị xác minh sai: cần đính chính/thông báo (bao gồm email nếu phù hợp), tính lại kết quả bị ảnh hưởng; phải có phương án cho **bộ nhiều câu sai**. | **CONFIRMED — chủ trương người dùng**; severity/quarantine/triage vẫn OPEN |
| D-012 | **EC-12:** Thu thập ngầm các mốc tương tác để tham khảo thời gian tiếp nhận và trả lời; có thể đối chiếu với kỹ năng Tiếng Việt, không cần hiện đồng hồ cho trẻ. | **CONFIRMED — chủ trương người dùng**; cách đo/diễn giải cần thử nghiệm |
| P-022 | Giữ immutable raw attempts; parent được sửa context và reweight learning evidence thay vì sửa đáp án gốc. | **PROPOSED** |
| P-023 | Question incident theo 3 cấp + `SESSION_ASSESSMENT_INVALIDATED` khi không còn đủ bằng chứng. | **PROPOSED** |
| P-024 | Không coi time-to-first-action là thời gian đọc thực; dùng hai bước đọc dữ kiện và giải bài khi cần. | **PROPOSED** |

**OPEN:** thời hạn sửa session, xung đột người giám hộ, mức ảnh hưởng đến mastery, threshold mass-incident, giao tiếp đính chính, cách sử dụng cross-subject evidence.


## J. CONFIRMED — duyệt toàn bộ recommendations & edge cases (2026-11-23)

**Người ra quyết định:** Product owner (người dùng), xác nhận rõ: “Tôi hoàn toàn đồng ý với các đề xuất/khuyến nghị ... 08-consolidated-review.md ... Các EC còn lại cũng theo ông đề xuất. Đánh dấu CONFIRM luôn.”

| ID | Phạm vi quyết định | Trạng thái |
|---|---|---|
| D-013 | **Tất cả 53 khuyến nghị** có mã `PF-01…06`, `AL-01…11`, `AI-01…14`, `PA-01…12`, `GM-01…10` thuộc [08](./08-consolidated-review.md) | **CONFIRMED** (cấp nguyên tắc/định hướng) |
| D-014 | **Tất cả EC-01…EC-45** theo hướng xử lý đề xuất trong [08](./08-consolidated-review.md) và mô tả mở rộng [09](./09-session-correction-question-incidents-and-response-time.md) | **CONFIRMED** (cấp hướng xử lý) |
| D-015 | **10 hướng khám phá** mục D file 08 | **CONFIRMED as exploration direction**, không phải cam kết triển khai/MVP |
| D-016 | Cách diễn giải các quyết định: không coi con số ngưỡng, thuật toán, chính sách pháp lý cần kiểm chứng hoặc kế hoạch giao hàng là đã chốt | **CONFIRMED as documentation boundary** |

**SUPERSEDED (về trạng thái, không xóa nội dung lịch sử):** Các nhãn `PROPOSED`/câu hỏi `OPEN` trong phần C, D, G, I của chính file này **khi trùng khuyến nghị đã ghi trong 08/09** được thay bằng `CONFIRMED` ở cấp định hướng. Chúng chỉ còn có giá trị giải thích nguồn gốc thảo luận. Các chi tiết `how much/which algorithm/which regulation/how tested` vẫn chưa được xác định.

**Quyết định cần theo dõi về implementation/validation (không làm mất trạng thái CONFIRMED của nguyên tắc):**
- Ngưỡng thành thạo, độ tin cậy và lịch ôn học theo chuyên môn/kiểm thử.
- Mốc hết hạn phê duyệt 3 hay 7 ngày và cấu hình exact policy; nguyên tắc chỉ auto-apply khi đã có opt-in rõ ràng cho tác động thấp **đã chốt**.
- Quy tắc phát hiện incident theo severity, batch quarantine và tiêu chí invalidation.
- Chi tiết thiết kế UI/UX, curriculum do ai phê duyệt, kiểm chứng quyền riêng tư/pháp luật, benchmark AI.
- Phạm vi/schedule/budget/tech stack của MVP: **vẫn chưa có plans**.


## K. CONFIRMED — Learning Evidence Model & Mastery Assessment (2026-11-23)

**Người dùng:** “Tôi đồng ý hoàn toàn. Hãy ghi lại idea và các phương án xử lý EC lại và ghi chú đã CONFIRM.”

**Tài liệu chi tiết:** [10 — Learning Evidence & Mastery Assessment](./10-learning-evidence-and-mastery-assessment.md).

| ID | Quyết định mới | Trạng thái |
|---|---|---|
| D-017 | **Mastery Model — phương án C:** đánh giá mức thành thạo và confidence độc lập, diễn giải trạng thái dễ hiểu cho trẻ/phụ huynh. | **CONFIRMED** |
| D-018 | **Mastery Reassessment — phương án C:** có thể điều chỉnh mức thành thạo dựa trên đủ bằng chứng; Review Status độc lập với Mastery Level; không hạ vì một phiên lỗi. | **CONFIRMED** |
| D-019 | **Evidence Value — phương án C:** trọng lượng và ý nghĩa của bằng chứng phụ thuộc mục tiêu đánh giá, phân biệt independent/supported/transfer/retention. | **CONFIRMED** |
| D-020 | **EV-01…EV-08:** xác nhận toàn bộ khuyến nghị xử lý các edge case được mô tả tại tài liệu 10. | **CONFIRMED** |
| D-021 | **Learning Evidence Framework:** dữ liệu tương tác gốc có lịch sử, Learning Profile suy ra từ Evidence và có thể đánh giá lại; đa môn dùng cùng framework nhưng rubric riêng. | **CONFIRMED** (nguyên tắc sản phẩm) |

**Lưu ý để tránh hiểu nhầm:** M0…M5 và 5 chiều Accuracy/Independence/Consistency/Transfer/Retention là mô hình tham chiếu được đồng ý nghiên cứu; chưa chốt **số mức cuối cùng**, ngưỡng phần trăm, công thức trọng số, thuật toán confidence hay lịch ôn. Đây là giai đoạn idea/product discovery, không phải plans.

**Ưu tiên tài liệu mới:** Nếu nhãn `PROPOSED` cũ trùng các quyết định mới ở trên thì dùng trạng thái **CONFIRMED của mục K**; không xóa dữ liệu thảo luận lịch sử.


## L. CONFIRMED — Mastery Assessment Engine & Learning Decision (2026-11-23)

**Người dùng:** “Tôi đồng ý các phương án trên”, xác nhận cả ba quyết định và các khuyến nghị xử lý edge case trong buổi thảo luận tiếp theo.

**Tài liệu chính:** [11 — Mastery Assessment Engine & Learning Decision](./11-mastery-assessment-engine-and-learning-decisions.md).

| ID | Quyết định | Trạng thái |
|---|---|---|
| D-022 / MA-D01 | **Mastery Policy theo từng kỹ năng/nhóm kỹ năng**; mỗi lĩnh vực có tiêu chí thành thạo phù hợp, không một công thức áp dụng cứng cho mọi môn. | **CONFIRMED** |
| D-023 / MA-D02 | **Evidence Aggregation có tính đa dạng**: điều chỉnh giá trị bằng chứng theo chất lượng, mức hỗ trợ, question family, phiên học và thời điểm; không tính lặp như evidence độc lập. | **CONFIRMED** |
| D-024 / MA-D03 | **Tách Mastery Assessment khỏi Learning Decision**; engine quyết định lộ trình theo mastery, confidence, prerequisites, recall và Parent-Guided Policy. | **CONFIRMED** |
| D-025 / MA-01…MA-08 | **Toàn bộ tám edge case** và cách xử lý tại tài liệu 11 đã được người dùng chấp nhận. | **CONFIRMED** |

**Ranh giới:** Đã xác nhận nguyên tắc; chưa lựa chọn thuật toán rule-based/BKT/IRT, ngưỡng evidence và confidence, số bậc mastery cuối cùng, cách hiệu chỉnh mô hình hoặc timeline/MVP. Tài liệu vẫn nằm trong `idea-summarize/`.


## M. Roadmap 7 giai đoạn & chuyển sang UX Design (2026-11-24)

**Người dùng xác nhận** Product Design giai đoạn 1 đã đủ để chuyển sang giai đoạn 2 và yêu cầu đưa roadmap vào repo, tạo README giới thiệu, tiếp tục cập nhật trong suốt vòng đời dự án.

| ID | Nội dung quyết định | Trạng thái |
|---|---|---|
| D-026 | **7 giai đoạn:** (1) Product Design — yêu cầu/mục tiêu học/game loop; (2) UX Design — user flow/sitemap/wireframe toàn bộ màn; (3) Visual Design — design system/nhân vật/bản đồ/UI kit; (4) Prototype — Rừng Bảng Nhân 2; (5) Learning Design — question bank/hints/recall algorithm; (6) Playtesting — nhiều nhóm tuổi; (7) MVP — Phép Nhân/rewards/village/parents. | **CONFIRMED** |
| D-027 | **Phase 1 COMPLETED ở mức Product Discovery baseline**; chuyển sang **Phase 2 UX Design IN PROGRESS**. | **CONFIRMED** |
| D-028 | Root `README.md` là điểm giới thiệu/trạng thái hiện hành của dự án, sẽ cập nhật sau các cột mốc đáng kể; `ROADMAP.md` lưu 7 giai đoạn. | **CONFIRMED** |

**Không đánh đồng Phase 1 completed với mọi PRD/thuật toán đã viết xong**. Các phần cần kiểm chứng vẫn thuộc những giai đoạn tương ứng. Tài liệu:
- [ROADMAP.md](../ROADMAP.md)
- [README.md](../README.md)
- [ux-design/README.md](../ux-design/README.md)

**Tài liệu Phase 2 được khởi tạo**: sitemap, 12 core flows, screen inventory; hiện là UX draft cần review, **chưa chốt toàn bộ wireframe/Figma**.


## N. CONFIRMED — Phase 2.1 UX Information Architecture (2026-11-24)

**Người dùng đã trả lời:** “Okay tôi hoàn toàn đồng ý.” đối với năm phương án UX-01…UX-05 trong buổi thảo luận kiến trúc điều hướng.

| ID | Quyết định UX | Trạng thái |
|---|---|---|
| D-029 / UX-01 | **B — Hub-Based Child Navigation:** Làng Khởi Đầu là hub, có quick navigation theo ngữ cảnh. | **CONFIRMED** |
| D-030 / UX-02 | Bản đồ phân tầng **World → Subject → Module → Topic/Quest → Activity**, hiển thị linh hoạt theo nội dung. | **CONFIRMED** |
| D-031 / UX-03 | **Parent Navigation-Based Dashboard** với năm khu: Dashboard, Learning Progress, Action Center, Learning History, Settings & Profiles. | **CONFIRMED** |
| D-032 / UX-04 | **C — Hybrid access:** Parent Portal qua web và cổng adult gate trong app, nhưng **không bắt buộc làm hai ứng dụng ngay trong MVP**. | **CONFIRMED** |
| D-033 / UX-05 | Cho phép trẻ đổi giữa hồ sơ đã được cấp quyền trên thiết bị, có xác nhận; cấu hình và quản lý hồ sơ cần Adult Gate. | **CONFIRMED** |

**Nguồn chi tiết:** [ux-design/01-sitemap-information-architecture.md](../ux-design/01-sitemap-information-architecture.md). **Chưa coi Phase 2 hoàn tất:** các user flow chi tiết và các wireframe/interaction còn cần review.


## O. CONFIRMED — Admin-managed onboarding & Admin Portal (2026-11-24)

**Người dùng:** “Tôi nghĩ cần thêm một bộ flow và màn hình cho admin, hiện tại về phần quản lý ngươi dùng sẽ do admin phụ trách chưa mở rộng tự đăng ký. Phần tự đăng ký sẽ được phát triển khi sản phẩm đã hoàn thiện hơn và hạ tầng cho phép nhiều truy cập. Còn các phần còn lại tôi đề đồng ý.”

| ID | Quyết định | Trạng thái |
|---|---|---|
| D-034 / UX-06 | Onboarding ngắn theo các bước, có thể bỏ qua thông tin không thiết yếu. | **CONFIRMED** |
| D-035 / UX-07 | Parent Assessment theo **Progressive Profiling** (đánh giá chung trước, bổ sung từng môn/module khi cần). | **CONFIRMED** |
| D-036 / UX-08 | Ý tưởng **Guest Preview + public self-registration** của đề xuất trước đây **không sử dụng giai đoạn đầu**; chỉ xem xét khi sản phẩm và hạ tầng sẵn sàng. | **DEFERRED / SUPERSEDED for initial rollout** |
| D-037 / UX-09 | Child Profiles do phụ huynh quản lý trong family/parent account, yêu cầu dữ liệu tối thiểu. | **CONFIRMED** |
| D-038 / UX-10 | **Admin cấp phát và quản lý tài khoản phụ huynh ban đầu**; không có public self-registration. | **CONFIRMED** |
| D-039 / UX-11 | **Thêm Admin Portal** cùng với Parent Portal và Child World; có sitemap, admin flows và screen inventory. | **CONFIRMED** |
| D-040 / ON-01…ON-12 | Đồng ý hướng xử lý 12 onboarding edge cases đã đề xuất; áp dụng trong bối cảnh tài khoản do admin cấp, không theo public sign-up. | **CONFIRMED** (cấp nguyên tắc) |

**Ranh giới:** Admin chịu trách nhiệm cấp/quản lý account; phụ huynh vẫn có thể tự tạo/cập nhật **child profile** trong account đã cấp. Các phương thức invitation, recovery, admin roles, content reviewer và bảo mật vận hành trong [Admin Portal draft](../ux-design/04-admin-portal.md) còn **OPEN/PROPOSED**, chưa chốt cụ thể.


## P. CONFIRMED — Admin roles, audit & secure activation (2026-11-24)

**Người dùng đã xác nhận trực tiếp:** “Tôi đồng ý với Super Admin + phân quyền Admin” và bốn nguyên tắc phân quyền dữ liệu học sinh, audit, kích hoạt an toàn bằng lời mời, tách quyền quản lý tài khoản và kiểm duyệt nội dung.

| ID | Quyết định | Trạng thái |
|---|---|---|
| D-041 / ADM-01 | Mô hình **Super Admin + Admin có phân quyền**; không giả định mọi quản trị viên có quyền giống nhau. | **CONFIRMED** |
| D-042 / ADM-02 | Admin quản lý tài khoản **không mặc nhiên** truy cập toàn bộ hồ sơ học tập nhạy cảm của trẻ; least privilege. | **CONFIRMED** |
| D-043 / ADM-03 | **Audit log** cho thao tác tạo, khóa, khôi phục tài khoản và thay đổi quyền. | **CONFIRMED** |
| D-044 / ADM-04 | Chọn hướng **gửi lời mời/kích hoạt an toàn thay cho gửi mật khẩu**; phương tiện gửi, token/expiry và khôi phục tài khoản chưa quyết định. | **CONFIRMED ở mức nguyên tắc** |
| D-045 / ADM-05 | **Tách quyền quản lý account và quyền review/duyệt nội dung giáo dục**. | **CONFIRMED** |

**Chưa chốt:** chi tiết phân quyền từng thao tác, cơ chế bootstrap và số lượng Super Admin, xác thực quản trị, kênh mời, xử lý tài khoản bị khóa trong phiên đang học, quyền hỗ trợ dữ liệu nhạy cảm. [Admin Portal](../ux-design/04-admin-portal.md) là bản draft UX, chưa phải thiết kế hoàn chỉnh.


## Q. CONFIRMED — Admin Permission Architecture (2026-11-24)

**Người dùng xác nhận:** “Tôi hoàn toàn đồng ý về các role ban đầu, Mô hình phân quyền, vấn đề nhiều role và quản lý quyền nhạy cảm.”

| ID | Quyết định | Trạng thái |
|---|---|---|
| D-046 / ADM-D01 | **Bốn role ban đầu:** `SUPER_ADMIN`, `ACCOUNT_ADMIN`, `CONTENT_REVIEWER`, `SUPPORT_OPERATOR`. | **CONFIRMED** |
| D-047 / ADM-D02 | **RBAC + Resource Scope + Context Policy**, không dùng role đơn thuần để cấp quyền truy cập dữ liệu trẻ. | **CONFIRMED** |
| D-048 / ADM-D03 | **Cho phép Admin nhiều role**; tổng hợp quyền phải tiếp tục thỏa mãn phạm vi và ngữ cảnh. | **CONFIRMED** |
| D-049 / ADM-D04 | **Chỉ Super Admin quản lý role/tài khoản Admin**; dữ liệu trẻ và các quyền nhạy cảm được bảo vệ bằng chính sách riêng. | **CONFIRMED** |

**Chưa xác nhận:** các ô cụ thể trong permission matrix (ai được xem audit ở mức nào, ai duyệt nội dung...), cơ chế bootstrap, MFA, invitation expiry, phục hồi tài khoản. Bảng và các EC được ghi **PROPOSED** tại [Admin Portal UX](../ux-design/04-admin-portal.md).


## R. CONFIRMED — Admin edge cases AD-01…AD-12 (2026-11-24)

**Người dùng xác nhận rõ:** “AD-01…AD-12 tôi đồng ý với đề xuất”.

| ID | Quyết định | Trạng thái |
|---|---|---|
| D-050 | **Toàn bộ 12 edge case AD-01…AD-12** và hướng xử lý trong [Admin Portal UX](../ux-design/04-admin-portal.md) được chấp thuận ở mức nguyên tắc. | **CONFIRMED** |

**Phạm vi xác nhận:** AD-01 bảo vệ Super Admin cuối cùng; AD-02 không tự nâng quyền; AD-03 nhiều role có kiểm tra scope/context; AD-04 chống sửa đồng thời; AD-05 phiên trẻ an toàn khi khóa; AD-06 token dùng lại; AD-07 token hết hạn; AD-08 truy cập dữ liệu ngoài ticket; AD-09 reviewer ngoài quyền; AD-10 thu hồi quyền khi đang đăng nhập; AD-11 khôi phục khóa nhầm có audit; AD-12 yêu cầu xóa dữ liệu được xử lý theo privacy workflow.

**Cập nhật trạng thái:** các ô permission matrix trước đây chưa được chốt, nay đã được người dùng duyệt ở **mục S**. Vẫn OPEN các chi tiết như thời hạn token, cách xác thực/phục hồi Super Admin, chính sách khi offline và điều kiện từng ô 🔒.


## S. CONFIRMED — Admin Permission Matrix (2026-11-24)

**Người dùng xác nhận rõ:** “Okay tôi đồng ý với ma trận phân quyền đã đề xuất”.

| ID | Quyết định | Trạng thái |
|---|---|---|
| D-051 / ADM-PM-01 | **Toàn bộ ma trận phân quyền của 4 vai trò** tại [04 — Admin Portal](../ux-design/04-admin-portal.md), gồm các hành động tạo/khóa/khôi phục parent account, lời mời, quản lý Admin, duyệt nội dung, truy cập dữ liệu học sinh, audit; giữ nguyên các giá trị ✅ / ❌ / 🔒 như đề xuất. | **CONFIRMED** |

**Ý nghĩa quyền:** ✅ được phép trong phạm vi bảo mật chung; ❌ bị cấm; 🔒 là **quyền có điều kiện, không tự động được cấp** và phải kiểm tra authorization, Resource Scope, Context Policy. Không ai được trực tiếp sửa raw attempts hay mastery. **Chưa chốt:** chính sách chi tiết đối với các ô 🔒, token expiry, MFA, bootstrap/recovery và triển khai cụ thể. Không thay đổi trạng thái `AD-01…AD-12 CONFIRMED`.


## T. CONFIRMED — Admin Account Provisioning UX (2026-11-24)

**Người dùng:** “Okay. Tôi đã đọc tất cả các đề xuất. Hoàn toàn hợp lý. Tôi xác nhận đồng ý.” — xác nhận toàn bộ năm quyết định và mười edge case trong Phase 2.4.

| ID | Quyết định | Trạng thái |
|---|---|---|
| D-052 / AP-D01 | **Account Lifecycle tách Invitation Lifecycle**; phân biệt token state và delivery state, không tạo trùng account vì invitation lỗi/hết hạn. | **CONFIRMED** |
| D-053 / AP-D02 | **Admin Dashboard theo permission**: widgets/dữ liệu theo role/scope, không mặc định toàn quyền. | **CONFIRMED** |
| D-054 / AP-D03 | **Create Parent Account yêu cầu email tối thiểu**; display name/note tùy chọn, Admin không nhập dữ liệu trẻ hoặc mật khẩu. | **CONFIRMED** |
| D-055 / AP-D04 | **Invitation mặc định 72 giờ, cấu hình được và single-use**; resend tuân thủ policy token đang hiệu lực. | **CONFIRMED** |
| D-056 / AP-D05 | **Super Admin bắt buộc MFA**; Admin khác MFA tối thiểu với các thao tác nhạy cảm. | **CONFIRMED** |
| D-057 / AP-01…AP-10 | **Toàn bộ 10 edge case Account Provisioning và phương án xử lý** đã được chấp thuận. | **CONFIRMED** |

**Tài liệu chi tiết:** [05 — Admin Account Provisioning & Parent Activation](../ux-design/05-admin-account-provisioning.md). **Không mặc định chốt** MFA provider, invitation email infrastructure, exact resend/rate-limit, chính sách tài khoản offline hay wireframe; Phase 2 vẫn IN PROGRESS.


## U. CONFIRMED — First two Admin wireframes (2026-11-24)

**Người dùng xác nhận:** “Okay đồng ý với 2 wireframe đã vẽ.”

| ID | Quyết định | Trạng thái |
|---|---|---|
| D-058 / AW-APP-01 | **Phê duyệt hai low-fi wireframe A-01 Admin Login và A-02 Admin Dashboard** theo bố cục đã dựng ở [Figma](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ?node-id=13-4). | **CONFIRMED — WIREFRAME APPROVED** |

**Phạm vi:** Duyệt hai màn hình hiện có, **không** suy rộng sang các màn MFA, error/loading/session, role-specific variants, responsive hoặc prototype chưa vẽ. [UX detail](../ux-design/06-admin-login-dashboard-wireframes.md).


## V. CONFIRMED — A-03 Parent Account List HTML wireframe (2026-11-24)

**Người dùng:** “Okay tôi nghĩ như vậy ổn rồi. Tiếp tục thôi.” — chấp thuận wireframe A-03 và các hướng AW-05…AW-08 được đề nghị ngay trước đó.

| ID | Quyết định | Trạng thái |
|---|---|---|
| **D-059 / AW-APP-02** | Phê duyệt **A-03 HTML low-fi**: sidebar + search/filter toolbar + table; không khóa/khôi phục one-click; metadata tối thiểu; tìm kiếm/lọc/sort/phân trang theo scope, đồng ý AW-05…AW-08. | **CONFIRMED — HTML WIREFRAME APPROVED** |

**Giới hạn:** Không khẳng định có A-03 Figma frame (MCP tool limit); không duyệt sẵn A-04. [Spec A-03](../ux-design/07-admin-parent-account-list-wireframe.md).


## W. CONFIRMED — A-04 Create Parent Account HTML wireframe (2026-11-24)

**Người dùng xác nhận trực tiếp:** “Bố cục tôi thấy ổn rồi. các AW cần review đều đồng ý.”

| ID | Quyết định | Trạng thái |
|---|---|---|
| **D-060 / AW-APP-03** | Phê duyệt **A-04 HTML low-fi wireframe** và **AW-09…AW-12**: form chính có panel giải thích onboarding; invitation checkbox bật mặc định và có thể tắt; email bắt buộc/tên hiển thị tùy chọn; trạng thái tạo account/gửi lời mời tách biệt; invitation lỗi hiển thị partial success, giữ account và dẫn đến A-07 để gửi lại. | **CONFIRMED — HTML WIREFRAME APPROVED** |

**Ranh giới:** chưa có frame A-04 trong Figma; demo frontend không phải hệ thống thật. Các trạng thái backend/xác thực, dịch vụ gửi email, chi tiết token và việc thiết kế A-05/A-07 vẫn OPEN. [A-04 UX Spec](../ux-design/08-admin-create-parent-account-wireframe.md).


## X. CONFIRMED — A-05 Parent Account Detail HTML wireframe (2026-11-24)

**Người dùng xác nhận:** “Hợp lý, tôi đồng ý với các đề xuất trên.”

| ID | Quyết định | Trạng thái |
|---|---|---|
| **D-061 / AW-APP-04** | Phê duyệt **A-05 HTML low-fi wireframe** cùng **AW-13…AW-16**: bố cục Account Overview/Invitation Summary/Audit Activity/Administrative Actions; xác nhận và lý do bắt buộc cho suspend/restore/disable; chỉ hiện số lượng child profiles và tách invitation token/delivery status; tài khoản DISABLED/CLOSED không khôi phục tức thì tại A-05. | **CONFIRMED — HTML WIREFRAME APPROVED** |

**Ranh giới:** không tạo/duyệt Figma frame A-05; không có backend, persistence/audit thực tế hay server-side authorization từ bản demo. [Chi tiết A-05](../ux-design/09-admin-parent-account-detail-wireframe.md). **A-07 Invitation Management chưa thiết kế.**


## Y. CONFIRMED — Global Layout Stability & AW-21 (2026-11-24)

**Người dùng xác nhận:** “Okay thống nhất. Tôi muốn toàn bộ dự án áp dụng rule tránh Layout Shift, giải pháp có thể tuỳ tình huống. nhưng luôn luôn cố gắng tránh Layout Shift.”

| ID | Quyết định | Trạng thái |
|---|---|---|
| **D-062 / UX-GLOBAL-01** | **Toàn bộ Little Explorers** (Child World, Parent Portal, Admin Portal) phải **luôn chủ động hạn chế Layout Shift ngoài dự kiến**; giải pháp tùy tình huống, không ép một kỹ thuật; cân bằng khả năng truy cập và responsive. Áp dụng qua thiết kế, code review và QA. | **CONFIRMED** |
| **AW-21** | Data Tables tránh giật cột: nút icon xem chi tiết kích thước ổn định, dùng highlight cho dòng đang xem, giữ chiều rộng cột; có nhãn và tương tác bàn phím. | **CONFIRMED** |

**Chi tiết và acceptance checklist:** [11 — Global Layout Stability Guidelines](../ux-design/11-global-layout-stability-guidelines.md). **AW-17…AW-20 vẫn PROPOSED**, vì người dùng chỉ xác nhận AW-21 và rule toàn dự án. Không suy diễn rằng mọi màn đã đạt kiểm thử CLS.


## Z. CONFIRMED — A-06 and A-07 HTML low-fi wireframes (2026-11-24)

**Người dùng:** “Okay. Tôi đồng ý toàn bộ A06, các đề xuất AW-22 đến AW-25, tôi cũng đồng ý tất cả, các phần của A-07.”

| ID | Quyết định | Trạng thái |
|---|---|---|
| **D-063 / AW-APP-05** | Duyệt **toàn bộ A-07 Invitation Management HTML low-fi**, gồm **AW-17…AW-20**: KPI + invitation table + detail/audit; tách account/token/delivery status; thao tác resend/revoke có quyền hợp lệ, xác nhận và lý do; resend tránh hai token còn hiệu lực, send failure giữ account. Những quyết định nền tảng AP-D01/AP-02/AP-09 vẫn áp dụng. | **CONFIRMED** |
| **D-064 / AW-APP-06** | Duyệt **toàn bộ A-06 Suspend/Restore Confirmation HTML low-fi**, gồm **AW-22…AW-25**: modal xác nhận trong A-05, định danh trạng thái rõ, reason + acknowledgement bắt buộc; thông báo riêng lỗi quyền/concurrency/network; cảnh báo phiên học active hoặc offline chưa đồng bộ. | **CONFIRMED** |

**Ranh giới:** A-06/A-07 chưa có Figma frame, không có API hay backend thật. **Quy tắc xử lý khi thiết bị offline chưa đồng bộ là OPEN**; AW-25 duyệt cảnh báo và xử lý UX thận trọng, không chốt chính sách chặn/hoãn/cho phép thao tác. Các quyết định kỹ thuật rate-limit, token retry/reissue và transaction boundary vẫn OPEN.

**Specs:** [A-06](../ux-design/12-admin-suspend-restore-confirmation-wireframe.md) · [A-07](../ux-design/10-admin-invitation-management-wireframe.md).


## AA. CONFIRMED — A-08 Admin User & Role Management (2026-11-25)

**Người dùng xác nhận:** “Tốt rồi, tôi đồng ý với màn hình và các đề xuất của ông.”

| ID | Quyết định | Trạng thái |
|---|---|---|
| **D-065 / AW-APP-07** | Phê duyệt **A-08 HTML low-fi** và **AW-26…AW-29**: Admin list + detail panel có filter và audit preview; tạo Admin bằng email + chọn nhiều role + tên tùy chọn, không nhập mật khẩu thay; thay đổi quyền/trạng thái cần xác nhận, lý do, acknowledgement và MFA; bảo vệ Super Admin cuối cùng, không cho tự sửa role tại A-08 và giải thích các nút bị khóa. | **CONFIRMED — HTML WIREFRAME APPROVED** |

**Ranh giới:** A-08 Figma frame chưa tạo; backend, activation, MFA và audit chưa triển khai. Các lựa chọn chi tiết về invitation Admin, khả năng delegated Admin xem danh sách read-only, cơ chế khôi phục Super Admin cuối cùng và A-09 vẫn **OPEN**. [Spec A-08](../ux-design/13-admin-user-role-management-wireframe.md).


## AB. CONFIRMED — A-09 Permission Change Confirmation HTML wireframe (2026-11-25)

**Người dùng xác nhận:** “Tốt, tôi đồng ý và xác nhận tất cả các đề xuất mới của ông”.

| ID | Quyết định | Trạng thái |
|---|---|---|
| **D-066 / AW-APP-08** | Phê duyệt **A-09 HTML low-fi** và **AW-30…AW-33**: modal xác nhận từ A-08 so sánh role thêm/thu hồi; lý do, xác nhận tác động và MFA; lỗi quyền/concurrency/MFA expiry/network được xử lý riêng; cảnh báo ảnh hưởng phiên đăng nhập, bảo vệ Super Admin cuối cùng và chặn tự sửa role. | **CONFIRMED — HTML WIREFRAME APPROVED** |

**Ranh giới:** Figma A-09 chưa tạo; chưa có MFA thật, backend, audit persistence hoặc final policy về invalidation session. Các mục này vẫn **OPEN**. [Chi tiết A-09](../ux-design/14-admin-permission-change-confirmation-wireframe.md). Tiếp theo **A-10 Admin Audit History**.


## AC. CONFIRMED — A-10 Admin Audit History HTML wireframe (2026-11-27)

**Người dùng xác nhận:** “Okay tôi đồng ý và xác nhận màn hình này và các đề xuất”.

| ID | Quyết định | Trạng thái |
|---|---|---|
| **D-067 / AW-APP-09** | Phê duyệt **A-10 HTML low-fi** và **AW-34…AW-37**: bảng Audit read-only cùng thống kê, tìm kiếm/bộ lọc và chi tiết sự kiện; metadata trước/sau được lọc dữ liệu nhạy cảm; quyền xem áp dụng trên totals/list/detail theo role + scope + context; hạn chế Layout Shift bằng icon và độ rộng cột ổn định. | **CONFIRMED — HTML WIREFRAME APPROVED** |

**Ranh giới:** Chưa có frame Figma A-10 hoặc backend audit; chưa chốt policy chi tiết cho các ô 🔒, retention, export, redaction/immutable storage. [Spec A-10](../ux-design/15-admin-audit-history-wireframe.md). **Tiếp theo: A-11 Access Recovery & Support.**


## AD. CONFIRMED — A-11 Access Recovery & Support HTML wireframe (2026-11-27)

**Người dùng xác nhận:** “Okay, Tôi hoàn toàn đồng ý với các đề xuất và màn hình A-11”.

| ID | Quyết định | Trạng thái |
|---|---|---|
| **D-068 / AW-APP-10** | Phê duyệt **A-11 HTML low-fi** và **AW-38…AW-41**: ticket list/filter/detail + audit theo scope; phân loại Password Reset / Expired Invite / Delivery Failure / Locked Account / Admin-MFA Recovery; thao tác có xác minh quyền, lý do và acknowledgement, không lộ mật khẩu/token hoặc bypass khóa; feedback tách biệt cho các lỗi gửi, hết hạn, quyền, conflict, network. | **CONFIRMED — HTML WIREFRAME APPROVED** |

**Ranh giới:** A-11 chưa có Figma frame, backend/email thật. Self-service password reset, quyền hỗ trợ 🔒 cụ thể, quy trình Super Admin/MFA recovery, token policy và rate limit vẫn **OPEN**. [A-11 UX Spec](../ux-design/16-admin-access-recovery-support-wireframe.md). **A-12 Content Quality Operations** là màn FUTURE/scope review, chưa mặc nhiên thuộc MVP.


## AE. CONFIRMED — A-12 Content Quality Operations V5 (2026-11-27)

**Người dùng xác nhận:** “OK rồi, đồng ý với màn hình này và xác nhận các đề xuất của ông”.

| ID | Quyết định | Trạng thái |
|---|---|---|
| **D-069 / AW-APP-11** | Chốt **A-12 V5 HTML low-fi** cùng **AW-42…AW-48**: queue và panel review; Triage khác Quarantine; sửa đáp án/giải thích qua version mới, đánh giá lại ảnh hưởng phiên học theo quy trình độc lập không sửa raw attempts; kiểm soát role/scope/incident; **Xem lịch sử xử lý báo cáo** ở popup có từng nút **Chi tiết**; sáu Audit gần nhất chỉ là preview, full Audit hỗ trợ filter/search/pagination. | **CONFIRMED — HTML LOW-FI APPROVED** |

**Trạng thái:** **12/12 màn Admin Portal A-01…A-12 đã được duyệt ở mức UX low-fi**. A-12 vẫn **FUTURE / scope review**, không tự động nằm trong MVP. Figma A-03…A-12, nội dung hệ thống backend, quy tắc tính lại điểm/mastery, quyền 🔒, thông báo và audit retention còn OPEN. [A-12 spec](../ux-design/17-admin-content-quality-operations-wireframe.md). Bước kế tiếp: Admin Portal UX Final Review.
