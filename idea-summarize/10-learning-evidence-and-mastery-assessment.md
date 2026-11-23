# 10 — Learning Evidence Model & Mastery Assessment

> **Product Discovery · 2026-11-23 · ✅ CONFIRMED (nguyên tắc và cách xử lý EV-01…EV-08)**  
> Người dùng xác nhận rõ cả **ba phương án C** và các đề xuất/khuyến nghị xử lý edge case được nêu trong buổi thảo luận Learning Evidence. **Không phải plans, không phải cam kết thuật toán/ngưỡng/kiến trúc kỹ thuật cuối cùng.**
>
> **Scope:** Nền tảng Little Explorers dành cho học sinh tiểu học lớp 1–5, đa môn (Toán, Tiếng Việt, Tự nhiên và Xã hội...), nhiều module. Phép nhân chỉ là module đầu tiên.

## 1. Nguyên tắc cốt lõi — CONFIRMED

1. **Learning Evidence không đồng nghĩa Activity Result:** Trả lời đúng/sai chỉ là một phần bằng chứng. Cần biết mục tiêu kỹ năng, mức hỗ trợ, bối cảnh, thời gian, nguồn và độ hợp lệ.
2. **Learning Profile là trạng thái suy ra từ Evidence, không phải nguồn dữ liệu gốc duy nhất.** Khi thêm/chỉnh ngữ cảnh, sửa câu hỏi sai, đổi rubric hoặc cập nhật chương trình, kết quả có thể được đánh giá lại.
3. **Raw attempts/interaction events lưu nguyên trạng**, còn ngữ cảnh (ví dụ phân loại phiên học do phụ huynh xác nhận) được chỉnh bằng bản ghi lịch sử; không âm thầm ghi đè đáp án gốc.
4. **Không đủ bằng chứng ≠ năng lực yếu.** Không dùng một lần sai/đúng hoặc phần trăm đúng đơn lẻ để kết luận.
5. **Independent Performance ≠ Supported Performance.** Cả hai hữu ích theo mục tiêu, nhưng có trọng lượng khác nhau trong đánh giá khả năng thực hiện độc lập.
6. **Learning/Adventure/Village progress độc lập.** Chấm lại Evidence không tự động thu hồi XP/vật phẩm.
7. **Đa môn:** cùng khung Evidence, mỗi skill/loại nội dung có Assessment Strategy/rubric phù hợp; không áp dụng một công thức điểm đúng/sai chung cho mọi môn.

## 2. Ba phương án C được người dùng CONFIRMED

| ID | Quyết định C | Nội dung được chốt |
|---|---|---|
| LE-DEC-01 | **Mastery Model — phương án C** | Engine quản lý **mức thành thạo + mức độ tin cậy độc lập**; giao diện trẻ/phụ huynh trình bày dễ hiểu, không nhất thiết công khai con số phức tạp. |
| LE-DEC-02 | **Reassessment — phương án C** | Mastery **có thể được đánh giá lại** nhưng cần đủ bằng chứng; **Review Status** (đến hạn ôn tập) tách khỏi Mastery Level. Một ngày làm sai không lập tức hạ bậc. |
| LE-DEC-03 | **Evidence Value — phương án C** | Giá trị bằng chứng **phụ thuộc mục tiêu đánh giá**: độc lập, có hỗ trợ, vận dụng, ghi nhớ. Không coi mọi câu trả lời đúng có giá trị như nhau và cũng không loại bỏ bằng chứng có hỗ trợ. |

## 3. Evidence Model — các nhóm thông tin được chấp thuận ở cấp ý tưởng

| Nhóm | Dữ liệu / ý nghĩa |
|---|---|
| Knowledge | Skill(s) đang kiểm tra; primary/secondary skill |
| Outcome | Đúng, sai, đúng một phần, chưa đủ căn cứ |
| Assistance | Tự học, có gợi ý, có phụ huynh hỗ trợ, không xác định |
| Context | Dạng câu, độ khó, nguồn, question version, môi trường tương tác |
| Temporal | Thời gian thực hiện, thời gian giữa các lần ôn, pause/hint events |
| Validity & Provenance | Câu có hợp lệ không, rubric, người/nguồn sửa, lịch sử đánh giá |

### Phân tầng dữ liệu khái niệm
```text
Activity → Raw Attempt Events (append-only)
                ↓
        Evidence Evaluation
                ↓
        Learning Evidence (versioned)
                ↓
   Validity / Context / Confidence
                ↓
      Skill Mastery Snapshot
                ↓
 Adaptive Planner → Next Activity / Review / Parent Recommendation
```

Thay đổi phân loại phiên học hoặc xử lý sự cố câu hỏi có thể dẫn tới **re-evaluation**. Luôn truy vết được kết quả trước/sau, lý do, actor và ảnh hưởng phụ thuộc. Chính sách dữ liệu phải tuân thủ quyền riêng tư, xóa/giữ dữ liệu hợp lệ; “append-only” là nguyên tắc toàn vẹn nghiệp vụ, không có nghĩa lưu thông tin cá nhân mãi mãi.

## 4. Skill Model & Mastery — định hướng đã chốt, thang số chỉ là đề xuất ban đầu

- Skill được định nghĩa ở mức **có thể quan sát/đánh giá**, không chỉ bằng việc hoàn thành Lesson.
- Nhiều Activity có thể đóng góp cho một Skill; một Activity có thể liên quan nhiều Skill nhưng phải tránh double-count và attribution sai.
- Các chiều Mastery: **Accuracy, Independence, Consistency, Transfer, Retention**. Chúng là các góc nhìn đánh giá chứ **chưa có công thức trộn**.
- Mastery Level và Assessment Confidence được quản lý riêng.
- Review Status (chưa đến hạn/đến hạn ôn/cần củng cố) tách biệt; `Mastered + Due for Review` không mâu thuẫn.
- **Thang minh họa** M0 Not Assessed → M1 Exploring → M2 Developing → M3 Practicing → M4 Proficient → M5 Mastered. Việc giữ đúng 6 mức, tên gọi, ngưỡng chuyển mức và confidence thresholds cần nghiên cứu/kiểm thử, **chưa chốt số lượng hay ngưỡng**.
- Ví dụ phép nhân: hiểu nhóm bằng nhau, biểu diễn phép nhân, tính, ghi nhớ, vận dụng 1 bước, nhiều bước phải phân biệt.
- Ví dụ Tiếng Việt: câu đúng/sai có thể cần rubric cho thông tin trực tiếp, suy luận, tóm tắt; Tự nhiên và Xã hội có phân loại/quan sát và bằng chứng mở.

## 5. Vòng đời và xử lý thay đổi

- `Raw Attempt → Initial Evaluation → Learning Evidence → Validity Check → Skill Snapshot`.
- Khi Evidence bị **DISPUTED**, tạm giảm/không sử dụng trong mastery nếu mức rủi ro đòi hỏi; sau review trở về **VALID** hoặc **INVALID**, ghi phiên bản.
- Khi Question Validation kết luận sai: fix key/re-score nếu xác định; invalidate nếu mơ hồ; re-evaluate downstream suggestions và skill confidence; giữ tiến trình adventure không bị phạt.
- Khi phụ huynh đổi `INDEPENDENT` ↔ `ASSISTED`, re-evaluate evidence theo nguồn phù hợp; không thay đổi bản ghi tương tác gốc.
- Khi có bằng chứng mới mâu thuẫn (ví dụ trước kia mastered, nay sai nhiều): chuyển trạng thái cần củng cố/giảm confidence và đánh giá thêm; **không hạ mức từ một phiên yếu duy nhất**.

## 6. Assessment Strategies theo môn/loại câu hỏi

| Strategy | Loại hoạt động | Nguyên tắc |
|---|---|---|
| Exact Answer | Toán phép tính | So khớp đáp án đã kiểm chứng; tính độc lập |
| Classification | Phân loại thực vật, động vật... | Quy tắc nhóm, cho phép trường hợp ngoại lệ |
| Sequence | Sắp xếp các bước/câu | Rubric trật tự |
| Multiple Valid Answers | Nhiều đáp án hợp lý | Bộ đáp án hợp lệ/rubric, không gạt oan |
| Rubric-based | Đọc hiểu/tự luận | Tiêu chí kiểm duyệt, có thể đúng một phần |
| Observational | Kéo thả, thao tác | Ghi nhận hành vi có thể đo và ý nghĩa skill |

**Không dùng AI tự phát quyết định đúng/sai cho câu diễn giải khi thiếu rubric và validation.**

## 7. Edge cases EV-01…EV-08 — ✅ CONFIRMED

| ID | Tình huống | Cách xử lý đã chốt ở cấp nguyên tắc | Trạng thái |
|---|---|---|---|
| EV-01 | Bé đoán trúng câu trắc nghiệm | Không kết luận mastery chỉ từ ít đáp án đúng; yêu cầu bằng chứng đa dạng. | **CONFIRMED** |
| EV-02 | Bé giải theo cách khác đáp án mẫu | Đánh giá đáp án, phép biến đổi/phương pháp hợp lệ và mục tiêu skill; không chỉ so cách làm mẫu. | **CONFIRMED** |
| EV-03 | Bé đúng nhờ vừa xem gợi ý | Ghi assistance và ngữ cảnh; phân biệt luyện tập với recall độc lập. | **CONFIRMED** |
| EV-04 | Một câu gắn nhiều kỹ năng | Primary/secondary skill attribution, không nhân đôi điểm/bằng chứng; kiểm tra mối liên hệ kỹ năng. | **CONFIRMED** |
| EV-05 | Phụ huynh sửa phiên cũ | Giữ lịch sử, đánh giá lại learning evidence và những quyết định downstream có ảnh hưởng; không sửa raw attempts. | **CONFIRMED** |
| EV-06 | Các phiên cho kết quả mâu thuẫn | Giảm confidence/đánh dấu cần làm rõ; thêm assessment đa dạng, không nâng/hạ vội. | **CONFIRMED** |
| EV-07 | Định nghĩa skill/curriculum thay đổi | Version hóa skill/rubric, giữ lineage, migrate/re-evaluate khi phù hợp, không làm mất lịch sử. | **CONFIRMED** |
| EV-08 | Bé làm đúng nhưng không thích mini-game | Tách preference và learning competency; đổi trải nghiệm mà không tự hạ mastery. | **CONFIRMED** |

## 8. Tình huống minh họa

- Tuần 1: Bé làm tốt bảng nhân 3 trong bài luyện → evidence thực hiện tốt.
- Tuần 2: Bé vận dụng thành công ở nhiều dạng bài → evidence transfer, có thể tăng mastery khi confidence đủ.
- Tuần 4: Bé sai 3/5 câu trong một phiên recall → **Review Status: Needs Reinforcement**, chưa tự động hạ mastery.
- Nếu phiên tuần 4 bị report câu sai, phần ảnh hưởng được re-evaluate; không đánh giá trẻ yếu do câu hỏi không hợp lệ.
- Nếu phụ huynh sửa phiên tuần 1 thành `LEARN_TOGETHER`, các bằng chứng độc lập thuộc phiên này được giảm vai trò; những phiên độc lập khác vẫn có giá trị.

## 9. Chi tiết cần kiểm thử/đặc tả, không thay đổi CONFIRMED
- Mức skill granularity, graph prerequisites, đánh giá kỹ năng phụ và chống double-count.
- Thang hiển thị chính xác (có giữ M0…M5 không), ngưỡng mastery/confidence và calibration.
- Phương pháp đánh giá mastery từng môn/loại câu, rubrics và nguồn giáo dục.
- Thời điểm ôn tập, cách evidence cũ giảm giá trị và thuật toán chọn câu đánh giá.
- Quy trình đối chiếu và thông báo khi kết quả thay đổi sau incident/parent correction.
- Thiết kế UI báo cáo năng lực dễ hiểu, không gắn nhãn trẻ.
- Chính sách bảo vệ dữ liệu trẻ, vòng đời bản ghi và quyền xóa.

## 10. Tài liệu liên quan
- [06 — Decision Log](./06-decisions-and-open-questions.md)
- [08 — Consolidated Review](./08-consolidated-review.md)
- [09 — Session Correction & Question Incidents](./09-session-correction-question-incidents-and-response-time.md)

**Chú ý:** Các quyết định ở đây là **product principles**, không phải kế hoạch phát triển, API/schema database hay thuật toán đã được chốt.
