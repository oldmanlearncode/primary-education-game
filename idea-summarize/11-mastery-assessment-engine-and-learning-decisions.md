# 11 — Mastery Assessment Engine & Learning Decision

> **Product Discovery — 2026-11-23 · ✅ CONFIRMED (nguyên tắc)**  
> Người dùng đã đồng ý cả ba đề xuất **MA-D01…MA-D03** và phương án xử lý **MA-01…MA-08** sau buổi thảo luận. Tài liệu này lưu lại quyết định ở mức ý tưởng, **không phải plans**, thuật toán chính thức hoặc đặc tả kỹ thuật.

## 1. Bối cảnh và mục tiêu

Little Explorers là nền tảng giáo dục **đa môn** dành cho lớp 1–5, có trò chơi phiêu lưu và Adaptive Learning Engine. Mastery Assessment không được suy ra đơn giản từ tỉ lệ đúng; hệ thống cần hiểu bằng chứng gốc, tính hợp lệ, mức hỗ trợ, sự đa dạng, độ tin cậy và khả năng ghi nhớ.

Luồng khái niệm:
```text
Learning Evidence (validity, assistance, context, timestamp, question family)
      ↓
Evidence Evaluator → Skill Aggregator
      ↓
Mastery Estimator + Confidence Evaluator
      ↓
Learning Decision Engine
      ↓
EXPLORE / PRACTICE / REINFORCE / ASSESS / RECALL / ADVANCE
      ↓
Parent-Guided Policy → Session Planner → Child Game
```

## 2. Quyết định được CONFIRMED

| ID | Quyết định | Trạng thái | Lý do |
|---|---|---|---|
| **MA-D01** | **Mastery Policy theo từng kỹ năng / nhóm kỹ năng**, không áp dụng một công thức thống nhất cho mọi môn. Chỉ định các chiều đánh giá phù hợp (accuracy, independence, consistency, transfer, retention hoặc tiêu chí sư phạm riêng), cùng điều kiện thành thạo. | **CONFIRMED** | Đọc hiểu khác phép nhân; hệ thống đa môn cần assessment strategy phù hợp từng skill. |
| **MA-D02** | **Evidence Aggregation phản ánh chất lượng và tính đa dạng**: nhiều question family, dạng bài, phiên độc lập, thời điểm cách nhau có giá trị thông tin khác việc lặp cùng một câu nhiều lần. | **CONFIRMED** | Giảm nguy cơ bé học thuộc màn chơi hoặc farm mastery. |
| **MA-D03** | **Tách Mastery Assessment khỏi Learning Decision**. Assessment ước lượng trạng thái năng lực/confidence; Decision lựa chọn trải nghiệm dựa thêm skill prerequisites, review due, mục tiêu và Parent-Guided Policy. | **CONFIRMED** | Tránh trộn năng lực đo được với quyết định mở khóa, phần thưởng hay điều chỉnh lộ trình. |

### Nguyên tắc diễn giải
- Mastery Level, Confidence và Review Status là các trục khác nhau (đã CONFIRMED từ tài liệu 10).
- Không đủ evidence là **uncertain**, không mặc định là low mastery.
- Independent evidence và supported evidence có mục đích khác nhau.
- Sự ổn định/đa dạng quan trọng hơn chỉ đếm số câu đúng.
- Có thể tăng nhanh mức đề xuất khi bé đã có kiến thức ngoài ứng dụng và placement assessment có đủ chứng cứ; **không được tuyên bố retention lâu dài chỉ từ bài ngắn một ngày**.
- Giảm confidence hoặc yêu cầu assessment bổ sung trước khi hạ mastery khi kết quả mâu thuẫn.
- Quyết định học tiếp vẫn tuân thủ quyền phụ huynh theo **Parent-Guided option C** đã chốt.
- `ASSESS` (thu thập bằng chứng đánh giá) và `PRACTICE` (luyện tập có trợ giúp) là hành động khác nhau; không biến đánh giá thành trải nghiệm căng thẳng.

## 3. Eight edge cases — MA-01…MA-08 (CONFIRMED)

| ID | Trường hợp | Cách xử lý đã được phê duyệt | Trạng thái |
|---|---|---|---|
| **MA-01** | Bé làm 20 câu cùng một Question Family | Hạn chế giá trị thông tin trùng lặp; không coi 20 câu là 20 evidence độc lập có trọng lượng ngang nhau. | **CONFIRMED** |
| **MA-02** | Bé học nhanh hơn lịch ôn | Cho tiếp tục bài mới khi đủ cơ sở, duy trì recall plan riêng. | **CONFIRMED** |
| **MA-03** | Mastery M5 nhưng Confidence thấp do dữ liệu cũ | Ưu tiên đánh giá bổ sung; không tự khẳng định mức chắc chắn cao hay hạ mastery ngay. | **CONFIRMED** |
| **MA-04** | Sai một định dạng nhưng đúng các định dạng khác | Tách lỗi do target skill, supporting skill, biểu diễn hay ngôn ngữ; chọn kiểm tra bổ sung phù hợp. | **CONFIRMED** |
| **MA-05** | Bé đã học kiến thức nâng cao ngoài ứng dụng | Placement assessment cho phép vượt qua phần luyện quá dễ khi đủ evidence; không buộc qua từng bậc máy móc. | **CONFIRMED** |
| **MA-06** | Câu hỏi AI sai sau khi bé được nâng mastery | Quarantine/correct question, re-evaluate evidence và các quyết định phụ thuộc; audit, parent notice theo severity. | **CONFIRMED** |
| **MA-07** | Hai phiên học cho kết quả trái ngược | Giảm confidence, mở assessment bổ sung trước khi nâng/hạ đột ngột. | **CONFIRMED** |
| **MA-08** | Phụ huynh đã duyệt lộ trình, sau đó năng lực được đánh giá khác | Xem xét lại đề xuất/đường học, giải thích thay đổi, tuân thủ Parent-Guided Policy; không sửa âm thầm decision log. | **CONFIRMED** |

## 4. Learning Decision — các hành động được chấp nhận ở cấp ý tưởng

| Action | Ý nghĩa |
|---|---|
| `EXPLORE` | Giới thiệu kiến thức mới khi cần xây dựng hiểu biết nền |
| `PRACTICE` | Luyện kỹ năng đã tiếp cận bằng bài tập có hỗ trợ thích hợp |
| `REINFORCE` | Củng cố kỹ năng có dấu hiệu chưa vững |
| `ASSESS` | Thu thập thêm evidence, đặc biệt khi confidence thấp hoặc kết quả mâu thuẫn |
| `RECALL` | Kiểm tra ghi nhớ khi đến hạn, không đồng nghĩa tự hạ mastery |
| `ADVANCE` | Đề xuất khám phá nội dung khó hơn khi phù hợp prerequisite và parental policy |

Một phiên có thể kết hợp nhiều hành động; ví dụ `RECALL` ngắn rồi `ADVANCE`. Thứ tự ưu tiên và thời lượng chưa quyết định.

## 5. Còn phải nghiên cứu/kiểm chứng — không phải từ chối quyết định đã chốt

1. Công thức/thuật toán thực tế: rule-based, Bayesian Knowledge Tracing, Item Response Theory hoặc kết hợp; thử nghiệm trên dữ liệu đủ chất lượng và có chuyên môn sư phạm.
2. Cách đo calibration của Confidence và tránh lẫn confidence với mastery.
3. Ngưỡng evidence quantity/diversity, điều kiện tăng/hạ nhiều bậc, tiêu chí validity, half-life thông tin, recall schedule.
4. Rubric cho các môn có câu hỏi mở, cách định nghĩa question family, primary/secondary skill attribution.
5. Threshold và policy khi low confidence nhưng parent muốn advance, fallback khi evidence sparse.
6. Thiết kế minh bạch trong Parent Portal mà không gắn nhãn tiêu cực hay dùng dữ liệu trẻ không cần thiết.

**Những vấn đề này là implementation/validation details cần nghiên cứu; không làm thay đổi trạng thái CONFIRMED của MA-D01…03, MA-01…08.**

## 6. Liên kết
- [10 — Learning Evidence & Mastery](./10-learning-evidence-and-mastery-assessment.md)
- [08 — Consolidated Review](./08-consolidated-review.md)
- [06 — Decision Log](./06-decisions-and-open-questions.md)
