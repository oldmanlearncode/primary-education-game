# 01 — Sitemap & Information Architecture

> **UX Navigation decisions UX-01…UX-05: ✅ CONFIRMED · 2026-11-24.** Sitemap chi tiết và wireframe vẫn đang được hoàn thiện.

## 1. Sơ đồ tổng thể

```text
APP ENTRY
├─ Chọn/đổi hồ sơ bé (trẻ)
├─ Parent gate → Parent Portal (người giám hộ)
└─ Child World
   ├─ Home / Làng Khởi Đầu (hub)
   │  ├─ Nhiệm vụ gợi ý / ôn tập đến hạn
   │  ├─ Khám phá
   │  ├─ Làng của bé
   │  ├─ Sổ tay
   │  ├─ Túi đồ
   │  └─ Nhân vật
   ├─ Khám phá / World Map
   │  └─ Chọn môn học
   │     ├─ Toán
   │     │  ├─ Cộng / Trừ / Phép nhân / Phép chia / Hình học ... (module)
   │     │  └─ Module → Topic Map → Lesson/Quest → Activity
   │     ├─ Tiếng Việt
   │     │  └─ Module → Topic Map → Lesson/Quest → Activity
   │     └─ Tự nhiên & Xã hội
   │        └─ Module → Topic Map → Lesson/Quest → Activity
   ├─ Learning Activity
   │  ├─ Giới thiệu mục tiêu & hướng dẫn
   │  ├─ Mini-game (câu hỏi; gợi ý; giải thích; tạm dừng)
   │  ├─ Trợ giúp / Learn Together status
   │  ├─ Hoàn thành & phần thưởng
   │  └─ Đề xuất hoạt động tiếp theo / ôn tập
   ├─ Village Builder
   ├─ Sổ tay (kiến thức, hành trình, huy hiệu)
   ├─ Túi đồ
   ├─ Nhân vật (avatar, Milo)
   └─ Child UI status: offline, retry, age-appropriate guidance
PARENT PORTAL
├─ Tổng quan đa môn
│  ├─ Môn học → Module → Kỹ năng / Mastery + Confidence + Recall
│  ├─ Nhật ký học tập / Session History
│  └─ Hành động cần chú ý / Parent Action Center
├─ Hồ sơ của bé
│  ├─ Tạo / chọn / sửa hồ sơ
│  └─ Parent Assessment (cold start / cập nhật)
├─ Mục tiêu học tập & giới hạn thời gian
│  ├─ Theo bé / môn / module
│  ├─ Chế độ phê duyệt điều chỉnh lộ trình
│  └─ Thông báo
├─ Parent Action Center
│  ├─ Learning Path Proposal detail / approve / reject / customize
│  ├─ Question Report / status / outcome
│  └─ Parent–Child learning suggestions
├─ Session History & Question Review
│  ├─ Chi tiết phiên / câu hỏi và lời giải
│  ├─ Chỉnh phân loại tự học / có hỗ trợ / không chắc
│  └─ Đính chính sau câu hỏi lỗi / before-after effect
├─ Learn Together mode setup
├─ Privacy & data rights
└─ Guardian roles / account / notification preferences
```

## 2. Các phân hệ điều hướng

| Khu | Navigation chính | Đối tượng |
|---|---|---|
| Entry | Switch child / parental gate | Trẻ + phụ huynh |
| Child Hub | Khám phá, Làng, Sổ tay, Túi đồ, Nhân vật | Trẻ |
| Subject/Module | World → Subject → Module → Topic → Quest | Trẻ |
| Learning | Activity → feedback/hints → completion | Trẻ |
| Parent | Overview, Action Center, History, Profiles, Settings & Privacy | Phụ huynh |

## 3. Quy tắc thông tin / usability

- **Không** đưa heatmap bảng nhân lên dashboard tổng quan toàn ứng dụng; chỉ hiện ở chi tiết module khi phù hợp.
- Learning Content (subject/module/topic/lesson/skill) không bị hardcode vào khu vực bản đồ.
- Parent Portal có adult gate, không phải tab trẻ có thể tự ý truy cập.
- User actions là nhiệm vụ; câu hỏi AI được chọn ở backend theo kế hoạch phiên — trẻ chỉ thấy hoạt động, không thấy provider/thuật toán.
- Không biến Parent Approval đang pending thành trạng thái chặn toàn bộ Child World.
- Lịch sử chỉnh sửa session và bản đính chính question incident thuộc Parent Portal.
- Giao diện đa tuổi có audio, ít chữ và chế độ giảm chuyển động (đề xuất thiết kế chi tiết ở giai đoạn 3).

## 4. Những quyết định về kiến trúc điều hướng — CONFIRMED

| ID | Phương án đã chốt | Trạng thái |
|---|---|---|
| UX-01 | **B — Hub-Based Navigation:** Làng Khởi Đầu làm trung tâm; sử dụng quick navigation theo ngữ cảnh để không bắt trẻ quay về hub qua mọi thao tác. | **CONFIRMED** |
| UX-02 | **World Map → Subject Map → Module Map → Topic/Quest → Learning Activity.** Có thể linh hoạt cách hiển thị từng tầng theo nội dung, không hardcode môn/chương trình vào map. | **CONFIRMED** |
| UX-03 | **Parent Portal dùng Navigation-Based Dashboard**, có 5 khu vực chính: Dashboard, Learning Progress, Action Center, Learning History, Settings & Profiles. | **CONFIRMED** |
| UX-04 | **C — Hybrid:** Child World trong game app; Parent Portal có thể dùng trình duyệt và truy cập qua adult gate trong app. Không bắt buộc tách hai ứng dụng ở MVP. | **CONFIRMED** |
| UX-05 | Trẻ được tự chọn **những hồ sơ đã được người giám hộ cho phép trên thiết bị**, có xác nhận hồ sơ đang chọn; sửa hồ sơ và quản lý quyền phải qua Adult Gate. | **CONFIRMED** |

### Quy tắc UX đi kèm
- Khi đang trong mini-game, hạn chế điều hướng gây phân tâm; thoát/chuyển hồ sơ phải có checkpoint an toàn và không làm mất tiến trình.
- Parent Portal và Child World có quyền truy cập khác nhau; quản lý tài khoản/điều chỉnh mục tiêu quan trọng không để trẻ tự thực hiện.
- Chọn môn/vùng tự do nhưng nhiệm vụ có prerequisite cần được hướng dẫn phù hợp và không khóa toàn bộ trò chơi.
- Đề xuất nhiệm vụ của Milo không đồng nghĩa bắt buộc theo lộ trình duy nhất.

## 5. Còn cần thiết kế/kiểm thử (không phải 5 quyết định chưa chốt)

- Cơ chế quick navigation: nút quay lại, đường tắt, trạng thái checkpoint và tránh mất tiến trình.
- Các tầng bản đồ có cần full-screen hay bottom-sheet/overlay tùy nhóm tuổi, loại thiết bị?
- UX truy cập Parent Portal hybrid khi chỉ có một thiết bị hoặc mất kết nối.
- Chuyển hồ sơ trên máy dùng chung: biểu hiện hồ sơ đang hoạt động, thông báo xác nhận và cách xử lý chọn nhầm.
- Kỹ năng/ôn tập có cần màn “Lộ trình học tập” riêng cho trẻ, hay tích hợp vào Milo và các nhiệm vụ?
- Toàn bộ wireframe, trạng thái offline/loading/error và kiểm thử UX vẫn **IN PROGRESS**.
