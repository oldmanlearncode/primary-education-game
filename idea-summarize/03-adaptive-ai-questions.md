# 03 — Adaptive Learning & AI Question Generation

> **Trạng thái: Ý TƯỞNG + ĐỀ XUẤT, CHƯA CHỐT KIẾN TRÚC.**  
> Người dùng đề xuất **AI (ChatGPT/OpenAI, Gemini, Claude)** cung cấp bộ câu hỏi mới mỗi lần vào bài/màn, kể cả chơi lại, và thích ứng theo năng lực. Đã thảo luận sâu nhưng chưa có xác nhận cuối cho phương án kỹ thuật cụ thể.

## 1. Mục tiêu của ý tưởng
- Mỗi **Learning Session** có câu hỏi phù hợp tình trạng học tại thời điểm bắt đầu.
- Chơi lại một mini-game không chỉ gặp cùng thứ tự/văn bản câu hỏi.
- Kỹ năng cần ôn vẫn được lặp có chủ đích: **lặp kiến thức ≠ lặp nguyên văn câu hỏi**.
- Độ khó không chỉ là số lớn/nhỏ; có yếu tố dạng bài, trực quan, suy luận, ngôn ngữ, trợ giúp.

## 2. Mô hình trách nhiệm [PROPOSED]
```text
Mục tiêu giáo dục / Skill Catalog + Learning Profile
                      ↓
            Adaptive Learning Engine
       (chọn skill, độ khó, ôn tập cần thiết)
                      ↓
                Question Planner
       (phân phối câu theo mục tiêu phiên)
                      ↓
          AI Content Generator / Pool
       (OpenAI / Gemini / Claude tùy nhà cung cấp)
                      ↓
          Validation & Moderation Gates
                      ↓
                Approved Questions
                      ↓
             Mini-game / Activity
                      ↓
          Assessment → Learning Profile
```
**Learning Engine** phải quyết định *học gì*; AI tạo biến thể *hỏi như thế nào*, **không tự ý đổi chương trình, kỹ năng, luật chơi hay phần thưởng**.

## 3. Đề xuất: Hybrid Question Generation [PROPOSED]
- **Curated source:** câu hỏi/tri thức do con người thiết kế, kiểm duyệt.
- **AI-generated validated pool:** AI sinh trước, đã qua kiểm tra và lưu lại.
- **On-demand generation:** chỉ khi pool thiếu câu phù hợp, sinh bổ sung có kiểm tra, không nhất thiết chờ provider khi bắt đầu mỗi màn.

Lợi ích kỳ vọng: hạn chế độ trễ, giảm chi phí, cho phép cache/offline một phần, chất lượng dễ giám sát hơn. Đây là khuyến nghị, **chưa được người dùng chốt**; có thể đối chiếu với đề xuất gọi AI mỗi lần.

## 4. Validation bắt buộc nếu dùng AI [PROPOSED / SAFETY]
1. **Schema:** câu hỏi, dạng đáp án, gợi ý, skill, độ tuổi và format mini-game.
2. **Correctness:** kiểm tra xác định được bằng code với phép tính; kiến thức phức tạp phải dùng nguồn đối chiếu/duyệt chuyên môn.
3. **Unambiguity:** một đáp án đúng khi loại bài đòi hỏi; distractors không gây hiểu sai.
4. **Pedagogy:** khớp curriculum, mục tiêu, độ khó, từ vựng.
5. **Safety:** ngữ cảnh hợp tuổi, không thu thập/đưa thông tin trẻ vào prompt ngoài nhu cầu.
6. **Novelty & recall:** tránh lặp nguyên văn không có chủ đích nhưng **giữ ôn tập**.
7. **Provenance:** nguồn tạo, phiên bản prompt/model, kết quả validation, thay đổi/review.

LLM-as-judge không đủ thay thế toán kiểm tra bằng code hoặc kiểm duyệt chuyên môn cho các môn có tính diễn giải.

## 5. Learning profile [PROPOSED]
Có thể lưu theo từng kỹ năng: chưa học → làm quen → đang luyện → cần ôn → thành thạo; số lần thử, độ chính xác, trợ giúp, thời điểm, khoảng cách giữa các lần nhớ lại, hình thức câu hỏi. Các tiêu chí xác định mức thành thạo phải thử nghiệm, **không mặc định một lần đúng**.

Chỉ gửi cho AI thông số không định danh tối thiểu như `subject/module/skills/difficulty/question_count/visual_support`; không gửi tên, ngày sinh, địa chỉ hoặc toàn bộ lịch sử học. Cần nghiên cứu điều khoản bảo vệ dữ liệu trẻ em, chính sách provider và yêu cầu phụ huynh trước triển khai thực tế.

## 6. AI provider [PROPOSED]
Mô hình có thể hỗ trợ OpenAI, Gemini và Claude qua lớp thay thế. **Không có quyết định dùng cả ba**, không có benchmark hay đơn giá/chọn model nào được chốt. Có thể khởi đầu một provider để học về chất lượng, nhưng thiết kế tránh phụ thuộc một bên.

## 7. AI có thể tạo gì? [PROPOSED]
- Biến thể câu hỏi trắc nghiệm, điền chỗ trống, tình huống vận dụng, đọc hiểu, phân loại.
- Giải thích/gợi ý có kiểm soát, thoại NPC, biến thể bối cảnh (không thay luật game).
- Câu hỏi theo mẫu bám sát skill, không mở ra nội dung ngoài chương trình.

Ví dụ cùng skill `3 × 4`: 3 giỏ × 4 quả, 3 rào × 4 gỗ, hay nhóm trực quan. Các biến thể có thể có cùng phép tính để đo khả năng chuyển giao, không xem là độc lập về độ khó.

## 8. Câu hỏi cần chốt [OPEN]
- Sinh **on-demand mỗi lần** hay **hybrid/pregen**? SLA khởi động màn và offline?
- Ai duyệt câu AI ở từng môn? Có bắt buộc human review trước khi public?
- Cách biểu diễn skill graph và knowledge prerequisites xuyên môn?
- Cách chấm/kiểm duyệt bài mở, đọc hiểu, câu trả lời nhiều cách?
- Adaptive theo phiên hay giữa phiên? Chống nhảy độ khó quá nhanh?
- Chọn provider dựa trên thử nghiệm, chi phí/latency/điều khoản?
- Lưu lịch sử câu hỏi, chống lặp và đảm bảo quyền xóa dữ liệu thế nào?
- Có tạo giọng nói, hình ảnh AI không; kiểm duyệt ra sao?
