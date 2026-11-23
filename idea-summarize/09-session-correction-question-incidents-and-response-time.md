# 09 — EC-02 / EC-03 / EC-12: Chỉnh phân loại phiên học, sự cố câu hỏi và thời gian tương tác

> Product Discovery — 2026-11-23. Ghi nhận phản hồi trực tiếp từ người dùng. Chi tiết xử lý là **đề xuất**, chưa coi là chính sách kỹ thuật đã chốt.

## 1. EC-02: Parent-reclassifiable learning session

**Người dùng đồng ý:** Khi phiên bị gắn nhầm `Tự học` hay `Có phụ huynh hỗ trợ`, phụ huynh được đổi lại phân loại; dữ liệu phiên phải được lưu và có thể cập nhật ngữ cảnh bởi phụ huynh; phụ huynh chịu trách nhiệm cuối cùng về **xác nhận ngữ cảnh tham gia**.

**Khuyến nghị về tính toàn vẹn:** tách `immutable answer/interaction events` với `editable session metadata`. Quyền phụ huynh xác nhận bối cảnh **không đồng nghĩa** tự ghi đè đáp án gốc hoặc kỹ năng đã thành thạo.

### Trường dữ liệu ý tưởng
- `session_id`, `child_profile_id`, `activity_id`, `question_version_ids`
- `attempt_events`: câu hỏi, lựa chọn, điểm được chấm, gợi ý, mốc thời gian (append-only)
- `participation_classification`: `INDEPENDENT` / `PARTIALLY_ASSISTED` / `LEARN_TOGETHER` / `UNKNOWN`
- `classification_history`: previous/new, timestamp, actor, reason, evidence confidence.
- `assessment_snapshot_before/after`: tác động lên các kỹ năng và đề xuất lộ trình.

### Workflow đề xuất
1. Parent Portal → Lịch sử học → Chọn phiên → Chỉnh chế độ.
2. Lưu sự kiện chỉnh sửa và lý do, không sửa sự kiện trả lời gốc.
3. Đánh dấu learning evidence cho chế độ mới; tính lại skill confidence, pending recommendations và lịch ôn bị ảnh hưởng khi cần.
4. Giữ XP/vật phẩm đã nhận trong game trừ khi có lỗi cấp phát độc lập.
5. Cho sửa phiên cũ với cảnh báo độ tin cậy nếu đã quá lâu.

### Edge cases bổ sung
- **EC-31:** phiên cũ đã kích hoạt thăng mức trước khi phụ huynh đổi loại → re-evaluate downstream decisions, thông báo minh bạch.
- **EC-32:** hai phụ huynh liên tiếp sửa ngược nhau → role/ownership, optimistic conflict handling, append-only log.
- **EC-33:** đổi “Có hỗ trợ” sau khi đã hoàn tất recall → phân biệt kết quả kỹ năng tự lập vs khả năng làm có hướng dẫn; không tự xóa những bằng chứng độc lập khác.
- **EC-34:** phụ huynh cố tình nâng năng lực bằng sửa loại phiên → hệ thống chỉ cập nhật nguồn bằng chứng, không cho ghi đè correctness hay mastery trực tiếp.

## 2. EC-03: Question quality incident & mass correction

**Người dùng đề xuất:** Khi câu hỏi sai, thông báo trong ứng dụng/email và đính chính công khai cho phụ huynh bị ảnh hưởng; điều chỉnh kết quả theo nội dung đúng. Cần kế hoạch khi **một bộ có nhiều câu sai**.

### Chiến lược khuyến nghị (PROPOSED)
| Incident | Khi nào | Hành động |
|---|---|---|
| Level 1: single question | Một câu đã xác minh sai | Quarantine phiên bản → sửa/cancel câu → impact scan → recompute |
| Level 2: question batch | Nhiều câu trong cùng blueprint/batch/provider có dấu hiệu lỗi liên quan | Quarantine toàn bộ batch nghi vấn → revalidate → phân phối nguồn đã duyệt |
| Level 3: systemic | Sai lệch trên diện rộng hoặc lỗi nghiêm trọng ảnh hưởng học sinh | Dừng pipeline/sources gây lỗi, lập incident, kiểm tra phạm vi, chấm lại/loại evidence, thông báo chủ động |

**Severity phụ thuộc loại lỗi + phạm vi + ảnh hưởng, không chỉ % câu lỗi.** Một nội dung không an toàn nghiêm trọng có thể đòi cấp cao dù chỉ một câu.

### Re-score vs invalidate
- Đáp án sai nhưng câu hợp lệ và có một đáp án xác định: cập nhật answer key, tính lại câu bị ảnh hưởng.
- Câu thiếu dữ kiện/mơ hồ/không có đáp án xác định: **invalidate evidence**, không đoán đáp án.
- Lời giải sai dù đáp án đúng: duyệt lại explanation và xem có gây ảnh hưởng đến những bài học tiếp theo.
- Nếu một phiên có quá ít câu hợp lệ để kết luận: `SESSION_ASSESSMENT_INVALIDATED` hoặc `INSUFFICIENT_EVIDENCE`. Giữ lịch sử hoạt động và phần thưởng game; mời đánh giá bổ sung nhẹ nhàng, không bắt làm lại ngay.

### Communication
- Email + thông báo trong app cho người giám hộ bị ảnh hưởng, theo mức severity và tuỳ chọn liên lạc.
- Nêu: câu/phiên bị ảnh hưởng, sai ở đâu, nội dung đúng, điểm/kỹ năng trước và sau, cần hành động gì (nếu có).
- Track delivery/read states; không đợi phụ huynh đọc mail mới chấm lại.
- Chấm lại phải tính đến tất cả học sinh bị tác động, version pin ở thời điểm trả lời, và audit provenance.

### Edge cases bổ sung
- **EC-35:** lỗi mới phát hiện sau nhiều tháng; learning path/notifications đã thay đổi theo điểm sai → impact graph + targeted re-evaluation.
- **EC-36:** batch có tỷ lệ lỗi cao nhưng lỗi khác nguyên nhân → kiểm tra theo severity, batch provenance, tránh rollback sai nguồn.
- **EC-37:** hủy nhiều câu làm phiên không đủ bằng chứng → invalidation và check lại quyết định lên mức; không tước thưởng.
- **EC-38:** email không gửi được hoặc phụ huynh chưa đọc → sửa dữ liệu độc lập, lưu lịch sử thông báo.
- **EC-39:** câu hỏi thay đổi trong phiên đang mở → pin phiên bản tại session và xử lý sau.
- **EC-40:** re-score gây tăng/giảm mastery khác với đề xuất đã được phụ huynh approve → re-evaluate proposal, không diễn giải lại thao tác approval cũ.

### OPEN
- Ngưỡng kỹ thuật của quarantine hàng loạt theo risk tier và confidence.
- Human review SLA, mức thông báo khẩn/công khai/từng người.
- Quy tắc bù đắp về mặt trải nghiệm và xử lý câu đã sai trong bài đang mở.
- Cách quản lý incident history và quyền truy cập dữ liệu đối với trẻ.

## 3. EC-12: Tách mốc đọc và trả lời, tham khảo kỹ năng Tiếng Việt

**Người dùng đề xuất:** âm thầm ghi nhận thời gian tiếp nhận/đọc hiểu và thời gian trả lời, dùng năng lực Tiếng Việt làm ngữ cảnh khi đánh giá Toán có lời văn; không hiện đồng hồ gây áp lực.

**Giới hạn bắt buộc:** không thể suy ra chính xác “thời gian đọc” và “thời gian suy nghĩ” chỉ bằng việc lấy hai mốc thời gian. Mốc quan sát được chỉ là proxy.

### Instrumentation đề xuất
`QUESTION_DISPLAYED` → `AUDIO_STARTED/COMPLETED` → `FIRST_INTERACTION` → `ANSWER_SELECTED` → `SUBMITTED`, cùng `PAUSED`, `HINT_REQUESTED`, `APP_BACKGROUND`.
- Không hiện stopwatch cho trẻ ở bài học thông thường.
- Đánh dấu timeout do rời app để tránh diễn giải sai.
- Time-to-first-action chỉ là thời gian chờ hành động đầu tiên, không đồng nghĩa thời gian đọc.
- Khi cần đánh giá riêng đọc hiểu đề: hoạt động 2 bước xác định dữ kiện → giải toán; không bắt buộc mọi bài.

### Cross-subject evidence
- Kỹ năng **Tiếng Việt / đọc hiểu** có thể gợi ý cần có audio, diễn giải đơn giản hoặc chia đề.
- Bé giải đúng câu trực quan nhưng sai câu văn: tín hiệu có thể liên quan đọc/diễn giải đề, **chưa đủ kết luận**.
- Một lỗi trong bài Toán có lời văn không tự hạ điểm phép nhân nếu chưa phân biệt sai ở đọc đề hay tính toán.
- Không dùng latency đơn độc để hạ level; motor/visual/attention/context có thể khiến trẻ chậm mà vẫn hiểu.

### Edge cases bổ sung
- **EC-41:** bé vừa đọc vừa tính hoặc đọc lại sau audio → không có phân tách thời gian nhận thức chính xác.
- **EC-42:** phụ huynh giải thích trong lúc bé đọc → mốc thời gian không đại diện năng lực độc lập.
- **EC-43:** app bị treo, đổi tab, máy chậm → bỏ thời gian không hoạt động trước khi diễn giải.
- **EC-44:** bé đọc chậm nhưng hiểu tốt hoặc khó khăn về thao tác → không điều chỉnh Toán sai hướng.
- **EC-45:** lấy kỹ năng Tiếng Việt làm yếu tố tiên quyết quá mạnh khiến trẻ bị chặn các nhiệm vụ Toán → chỉ dùng để lựa chọn hỗ trợ/đánh giá tách biệt, không gộp điểm 2 môn.

## 4. Tác động kiến trúc sản phẩm (vẫn ở mức idea)
- Learning Evidence: nguồn, chế độ, độ tin cậy, phiên bản câu và lịch sử chỉnh sửa.
- Parent Portal: Session History + Edit Classification + Question Incident/Corrections.
- Learning Analytics: before/after correction, reason & revision.
- Question Validation: batch provenance, quarantine & re-score.
- Cross-skill: bản đồ chứng cứ đọc đề vs tính toán.
- Safety: bảo mật thông tin trẻ, quyền của người giám hộ, audit nhưng vẫn có cơ chế xóa/giảm dữ liệu theo chính sách.

## 5. Quyết định cần chốt (trừ mục tiêu do người dùng đã nêu)
1. Phụ huynh có thể sửa classification đến khi nào; có cần lý do?
2. Sửa classification có tự tính lại mastery ngay, hay đề xuất đánh giá lại?
3. Khi batch lỗi nhiều, có ngưỡng invalidate toàn phiên nào?
4. Severity level 1/2/3 và cách truyền thông tương ứng?
5. Có cho phụ huynh xem before/after learning state trong lịch sử?
6. Cross-skill evidence giữa Toán và Tiếng Việt ảnh hưởng degree nào?
7. Dạng bài nào nên có bước đọc/hiểu đề riêng? Mặc định tắt/đôi lúc dùng?
