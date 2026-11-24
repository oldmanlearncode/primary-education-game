# 02 — Core User Flows & Edge Cases

> **INITIAL DRAFT · 2026-11-24**. Product principles đã CONFIRMED, nhưng cách tổ chức luồng và từng interaction chưa được review.

## Flow F-01 — First-time setup + parent-assisted cold start

```text
Open app → Adult entry/gate → Tạo hồ sơ bé
→ Thông tin lớp/khả năng/mục tiêu [có thể bỏ qua]
→ Tạo Parent Assessment (prior only)
→ Chọn bé → Child Hub
→ Chọn môn/module lần đầu → Discovery Assessment ngắn
→ Learning Profile sơ bộ → Đề xuất hoạt động phù hợp
```
**Edge:** phụ huynh khai cao/thấp → calibrate qua activity; không bắt trẻ làm lại kiến thức quá dễ; nếu khai báo trống vẫn có default discovery path. Nhiều bé dùng chung thiết bị: rõ hồ sơ đang chọn.

## Flow F-02 — Explore subject and module

```text
Child Hub → Khám phá → World Map → Chọn môn
→ Chọn module → Topic Map → Quest detail
→ [prerequisite check] → Start Learning Session
```
**Edge:** kỹ năng chưa sẵn sàng → hiển thị hoạt động chuẩn bị/có hỗ trợ; vẫn cho khám phá vùng khác, không khóa toàn bộ môn.

## Flow F-03 — Start / finish a mini-game

```text
Quest intro → Session Plan → Approved Question Pool
→ Activity (đề / thao tác / câu trả lời)
→ đúng: phản hồi phù hợp
→ chưa đúng: gợi ý theo tầng + thử lại/giải thích
→ kết thúc: Learning Evidence + rewards + next suggestion
→ Village Builder / Explore / Stop
```
**Edge:** offline/AI down → dùng câu đã được duyệt; không bỏ qua validation. App thoát → resume checkpoint; không trừ XP khi sai.

## Flow F-04 — Recall, reassessment & advance

```text
Review due → đề xuất ôn → recall activity
→ evidence cập nhật → Mastery + Confidence + Review Status
→ Learning Decision → PRACTICE / REINFORCE / ASSESS / RECALL / ADVANCE
```
**Edge:** bé sai một phiên không tự hạ mastery; evidence mâu thuẫn → thêm assessment; phụ huynh cần phê duyệt nếu vượt phạm vi policy.

## Flow F-05 — Parent review of a session + reclassify assistance

```text
Parent gate → History → Session detail → Change learning mode
→ Independent / Partially assisted / Learn Together / Unknown
→ Confirm → Append audit event → Re-evaluate evidence if affected
→ Display before/after learning impact
```
**Edge:** parent edits old session; two guardians disagree; giữ raw answer events không sửa.

## Flow F-06 — Parent reports invalid question

```text
Parent gate → Session detail → Question detail
→ Report issue → Select reason / note → Submit
→ Review queue / quarantine (risk based)
→ Valid / Corrected / Invalid
→ Re-score/re-evaluate affected evidence → Parent notification
```
**Edge:** nhiều câu sai cùng batch → question batch incident; thiếu câu hợp lệ → session assessment invalidation; không thu hồi thành tích game; email fail không chặn sửa dữ liệu.

## Flow F-07 — Approve learning path proposal

```text
Action Center → Proposal detail (reason + evidence)
→ Approve / Reject / Customize → Audit decision
→ Learning path update (theo scope parent policy)
```
**Edge:** timeout chỉ được auto-apply low-impact nếu phụ huynh đã opt-in từ trước; thay đổi lớn không tự ý áp dụng; vẫn có hỗ trợ/tạm thay activity trong phiên học.

## Flow F-08 — Learn Together

```text
Parent Portal / mode chooser → Learn Together
→ Chọn môn/module/challenge → Parent guidance available
→ Child + parent play → Assisted evidence
→ Có thể chọn bài độc lập tương tự để kiểm tra việc vận dụng
```
**Edge:** phụ huynh quên bật mode → sửa phân loại phiên sau; không dùng kết quả assisted như mastery independent.

## Flow F-09 — Time limit and pause

```text
Parent sets screen-time policy → Child starts quest
→ Approaching limit → child-friendly notice
→ Safe checkpoint → pause/save → resume when allowed
```
**Edge:** đang giữa câu → không cắt ngang gây mất kết quả; offline → áp dụng policy đã đồng bộ an toàn.

## Flow F-10 — Child switches profile / multiple guardians

```text
Entry/parent-approved switch → Choose child profile
→ Confirm active profile → Load profile-specific progress
```
**Edge:** sai profile → parent flags/reclassifies affected session; nếu guardians bất đồng → owner/permission + audit, tránh quyết định bất nhất.

## Flow F-11 — Parent learning analytics

```text
Parent Overview (multi-subject)
→ Subject → Module → Skills
→ Mastery + Confidence + Review Status
→ Evidence timeline / recommended action
```
**Edge:** thiếu bằng chứng ≠ bé yếu; hiện language tích cực, không kết luận dựa trên một câu.

## Flow F-12 — Incident correction after the fact

```text
Question version invalidated
→ identify affected attempts → re-score/invalidate
→ re-evaluate learning state and downstream decisions
→ notify guardians (in-app / email based on severity)
→ Session history shows correction & reason
```
**Edge:** parent không nhận mail, đề xuất cũ đã được approve, nhiều phiên liên quan; lưu audit và hành động nhất quán.

## Yêu cầu nối với wireframes

Mỗi flow cần screen-ID trong [Screen Inventory](./03-screen-inventory.md), trạng thái success/error/empty/loading và link frame Figma khi đã vẽ. Tài liệu flow chưa phải prototype tương tác.
