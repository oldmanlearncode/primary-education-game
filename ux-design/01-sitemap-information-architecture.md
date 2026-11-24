# 01 — Sitemap & Information Architecture

> **INITIAL DRAFT · 2026-11-24** · Giai đoạn 2, chưa chốt.

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

## 4. Cần review

- Child World có nên dùng bottom navigation cố định hay hub-centric?
- Các module có hiển thị như đảo/vùng trên world map hay drill-down trực tiếp?
- Phụ huynh truy cập qua cùng app (adult gate) hay web portal riêng?
- Trẻ có được tự chuyển profile hay cần xác nhận người lớn?
- Kỹ năng/ôn tập có cần màn “Lộ trình học tập” riêng cho trẻ?
