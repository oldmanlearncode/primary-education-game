# 07 — Parent-Guided Adaptive Learning (PGAL)

> **Ý tưởng bổ sung — 2026-11-23.** Phần này ghi nhận thảo luận, **chưa phải kế hoạch/requirement đã chốt**.
>
> **Người dùng đề xuất:** Tăng vai trò chủ động của phụ huynh trong cold start, báo lỗi câu hỏi, phê duyệt điều chỉnh lộ trình và tương tác cùng con.

## 1. Parent-assisted cold start [USER IDEA / PROPOSED]
- Khi tạo hồ sơ, phụ huynh trả lời một số câu về mức lớp, môn/module đã biết, điểm mạnh/yếu, khả năng tự học, mục tiêu; tránh buộc bé đã giỏi khởi đầu quá thấp.
- Dữ liệu phụ huynh là **prior assessment**, chưa phải bằng chứng năng lực chắc chắn.
- Trẻ thực hiện **Discovery Assessment** ngắn, vừa học vừa đánh giá, theo môn/module khi bắt đầu; không tổ chức một kỳ thi dài ở lần đầu.
- Hệ thống so sánh khai báo với năng lực quan sát, điều chỉnh dần, lưu nguồn bằng chứng; tránh gắn nhãn phụ huynh khai báo “sai”.
- Dự kiến hỏi ~5–8 câu chung khi onboarding chỉ là giả thuyết UX, chưa chốt số lượng.
- Cần xác định: cách phân cấp độ tự tin của thông tin phụ huynh; trường hợp bỏ qua; người giám hộ có nhiều con; điều chỉnh sau onboarding.

## 2. Parent Question Review [USER IDEA / PROPOSED]
- Phụ huynh xem lịch sử phiên học và nội dung câu hỏi con đã gặp, chọn **Báo cáo vấn đề**: đáp án sai, mơ hồ, thiếu dữ kiện, độ khó/tuổi không hợp, ảnh không khớp, kiến thức sai, lý do khác.
- **Báo cáo của phụ huynh ≠ xác nhận câu hỏi không hợp lệ.** Đưa qua kiểm tra sơ bộ → có thể tạm ngưng phát hành câu nghiêm trọng → kiểm duyệt tự động/chuyên môn → sửa/loại/giữ.
- Lưu phiên bản câu hỏi, bằng chứng khiếu nại, kết luận và thông báo lại cho phụ huynh.
- Nếu câu đã chấm sai: xem xét **recalculate affected attempts/learning evidence**, kể cả các trẻ khác đã gặp câu lỗi; không chỉ sửa đáp án hiển thị.
- Parent review là **tầng phát hiện lỗi bổ sung**, không thay thế correctness validation hay người kiểm duyệt chuyên môn.
- Mở câu hỏi: khi nào quarantine tự động; chống report nhầm/lạm dụng; SLA duyệt; ai có quyền quyết định; giữ an toàn dữ liệu khi hiển thị lịch sử.

## 3. Parent approval / learning-path proposals [USER IDEA + SAFETY DESIGN PROPOSED]
**Đề xuất của người dùng:** Khi năng lực bé nên tăng/hạ mức, thông báo phụ huynh, có thể yêu cầu xác nhận, và sau 3 ngày–1 tuần không phản hồi có thể xử lý theo cơ chế tự động; ghi log.

**Thiết kế khuyến nghị (chưa chốt):** phân ba cấp:
1. **Điều chỉnh hỗ trợ trong bài** (gợi ý, hình ảnh, bài dễ tiếp cận): tự động để không chặn học.
2. **Điều chỉnh mức module** (thêm ôn, mở thử thách khó hơn trong module): thông báo, có thể áp dụng theo **chính sách đã được phụ huynh lựa chọn trước**.
3. **Thay đổi lớn** (mục tiêu phụ huynh đặt, vượt khối lớp, lộ trình dài hạn): cần **xác nhận chủ động**, không mặc nhiên “im lặng = đồng ý”.

**Chế độ quyền phụ huynh (đề xuất):**
- Tự động có giám sát.
- Phê duyệt thay đổi quan trọng (**mặc định được đề xuất**).
- Kiểm soát chặt.

**Hết hạn:** quy tắc áp dụng chỉ cho các thay đổi rủi ro thấp và khi có opt-in trước; nếu không, giữ nguyên quyết định đang chờ. Không khiến trẻ phải làm tiếp nội dung quá khó: luôn có trợ giúp và hoạt động thay thế. Audit log phân biệt `PARENT_APPROVED`, `PARENT_REJECTED`, `POLICY_AUTO_APPLIED`, `EXPIRED_NO_ACTION`, `PARENT_CUSTOMIZED`; ghi ai, lúc nào, bằng chứng, phiên bản trước/sau, lý do.

## 4. Learn Together – học cùng phụ huynh [PROPOSED]
- Phụ huynh có thể chọn phiên **học cùng con**; có thể thử thách hơi trên năng lực hiện tại với hỗ trợ.
- Phân biệt **Independent Performance** và **Supported Performance**; không cộng gộp điểm thành thạo như nhau.
- Bé có thể thử lại bài tương tự trong phiên độc lập sau này để đánh giá khả năng tự vận dụng.
- Tránh bắt phụ huynh xác nhận hỗ trợ sau mỗi câu; tùy chọn lúc đầu hoặc cuối phiên.
- Cần kiểm chứng cơ chế ghi nhận hỗ trợ không gây áp lực hay đánh giá sai.

## 5. Parent Action Center [PROPOSED]
- Parent dashboard tổng quan **đa môn**, bổ sung tab **Cần xác nhận** / **Nên xem** / **Gợi ý đồng hành**, không phải chỉ báo cáo tĩnh.
- Thông báo về đề xuất lộ trình, điểm kỹ năng cần lưu ý, báo cáo câu hỏi, gợi ý hoạt động ngắn tại nhà.
- Cấu hình nhịp thông báo/bản tóm tắt và khả năng tắt; không làm phụ huynh bị quá tải.
- Có mục tiêu học tập (củng cố / theo chương trình / nâng cao / cân bằng các môn) nhưng không bỏ qua prerequisite giáo dục chỉ vì phụ huynh chọn.

## 6. Product safety invariants [PROPOSED]
- Hành trình học của bé không bị chặn vô thời hạn bởi pending approval.
- Khi trẻ gặp khó khăn, có thể **giảm mức hỗ trợ/tăng scaffold** hoặc thay hoạt động tạm thời bất kể trạng thái phê duyệt lộ trình.
- Phụ huynh thấy lý do & bằng chứng trước khi quyết định; ngôn ngữ mô tả tích cực, không gắn nhãn trẻ “kém”.
- Im lặng không tương đương với sự đồng ý trừ khi có **chính sách opt-in trước, rõ phạm vi**, và chỉ áp dụng thay đổi rủi ro thấp.
- Cảnh báo/feedback phải hợp lý, tránh spam; chính sách bảo vệ dữ liệu trẻ được ưu tiên.

## 7. Câu hỏi cần chốt [OPEN]
1. Bộ câu hỏi onboarding cụ thể cho từng khối lớp/môn? Cho phép skip không?
2. Phụ huynh có chỉnh trực tiếp lộ trình hay chỉ duyệt đề xuất?
3. Mức nào bắt buộc approval? Tăng/hạ mức khác nhau không?
4. Hết hạn là 3 ngày, 7 ngày hay tùy chọn? Chính sách mặc định?
5. Xử lý giữa phiên nếu phụ huynh chưa chấp thuận nhưng bé đang gặp khó?
6. Report câu hỏi có gây quarantine ngay không, ngưỡng và quyền review?
7. Câu hỏi bị xác nhận sai sẽ re-score thế nào và thông báo cho ai?
8. Cách phân biệt hoạt động có người lớn hỗ trợ trong hồ sơ năng lực?
9. Action Center cần bao nhiêu thông báo/tuần để đủ hữu ích mà không quá tải?
10. Có cần dashboard điều chỉnh từng môn/module khác nhau không?

## 8. Liên quan
- [Adaptive Learning & AI Generation](./03-adaptive-ai-questions.md)
- [UI/UX Parent Portal](./04-ui-ux-parent-portal.md)
- [Decision log](./06-decisions-and-open-questions.md)
