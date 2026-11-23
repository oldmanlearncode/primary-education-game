# 01 — Tầm nhìn sản phẩm & Product Foundation

> Discovery notes · 2026-11-23 · **Không phải kế hoạch thực thi**

## 1. Tầm nhìn [CONFIRMED: định hướng chính]
**Little Explorers — Những Nhà Thám Hiểm Nhỏ** (tên tạm) là nền tảng trò chơi giáo dục dành cho học sinh tiểu học Việt Nam **lớp 1–5**. Bé khám phá kiến thức theo cách học–chơi–ghi nhớ, có phiêu lưu trên bản đồ và phần thưởng phát triển thế giới riêng. Nền tảng phải hỗ trợ **nhiều môn, nhiều module trong mỗi môn**.

Các môn ví dụ: **Toán, Tiếng Việt, Tự nhiên và Xã hội**, về sau có thể có môn/nhóm kiến thức khác. Không khóa cấu trúc theo bảng cửu chương. **Module đầu tiên là Phép nhân**, dùng để thử nghiệm nền tảng.

## 2. Giá trị cốt lõi [PROPOSED]
- **Learning first:** mỗi hoạt động phải có mục tiêu giáo dục và dấu hiệu chứng minh việc học.
- **Playful learning:** kiến thức là một phần cách chơi, không đơn thuần câu hỏi gắn XP.
- **Personalized progress:** lộ trình theo năng lực, không chỉ khối lớp.
- **Child wellbeing & safety:** không phạt vì sai, không ép duy trì streak, không quảng cáo nhắm vào trẻ, tối thiểu hóa dữ liệu.
- **Modular by design:** engine và phần thưởng dùng chung, nội dung học đặc thù theo môn.

## 3. Người dùng [PROPOSED]
| Vai trò | Nhu cầu |
|---|---|
| Học sinh lớp 1–5 | Giao diện phù hợp khả năng đọc và thao tác, khám phá an toàn, nhận phản hồi tích cực |
| Phụ huynh/người giám hộ | Tổng quan **toàn bộ các môn**, tiến độ từng môn/module, thời gian, hồ sơ, dữ liệu |
| Quản trị/nội dung/giáo dục | Tạo, duyệt, phiên bản hóa môn học, module, kỹ năng, câu hỏi; chưa chốt phạm vi giao diện quản trị |

Khác biệt độ tuổi: trẻ lớp 1 cần ít chữ, hướng dẫn giọng nói, thao tác lớn; lớp 4–5 cần thử thách tư duy hơn và có thể giảm yếu tố quá trẻ con. Phân nhóm trải nghiệm Junior/Explorer/Advanced **mới là đề xuất**, không gắn cứng với lớp.

## 4. Phân cấp nội dung [ĐỊNH HƯỚNG ĐÃ THỐNG NHẤT]
```text
Little Explorers (Platform)
 ├── Toán (Subject)
 │    ├── Phép nhân (Module) → Bảng nhân 2 (Topic) → Bài học → Kỹ năng → Hoạt động
 │    ├── Phép chia
 │    ├── Cộng / Trừ
 │    └── Hình học ...
 ├── Tiếng Việt
 │    ├── Chính tả
 │    └── Đọc hiểu ...
 └── Tự nhiên và Xã hội
      ├── Thực vật
      └── Động vật ...
```
Các module/đề mục trên là ví dụ, **không phải curriculum đã chốt**; phải rà soát theo chương trình giáo dục phổ thông Việt Nam, mức lớp và tài liệu chuyên môn.

**Thiết kế dữ liệu gợi ý [PROPOSED]:** nội dung giáo dục (mục tiêu/kiến thức/kỹ năng/câu hỏi) tách khỏi luật mini-game, vật phẩm, nhiệm vụ. Một activity có thể liên hệ nhiều skill; phải biết skill chính dùng để đánh giá.

## 5. Khám phá có định hướng — Phương án C [CONFIRMED]
Bé **tự do chọn môn/vùng**, nhưng trong một module, hệ thống **đề xuất lộ trình** và có thể ràng buộc các hoạt động đòi hỏi kiến thức nền. Mức khó theo năng lực hiện tại; không tạo cảm giác trẻ học thấp hơn lớp. Cần phân biệt nội dung khám phá tự do với bài học/đánh giá có yêu cầu tiên quyết.

## 6. Mô hình hai môi trường [CONFIRMED: có khu vực phụ huynh]
- **Child World:** avatar, bản đồ, mini-game, sổ tay, túi đồ, làng.
- **Parent Portal:** dashboard đa môn, báo cáo theo môn/module, mục tiêu/thời gian, hồ sơ, thông báo và dữ liệu; có adult gate.
- **Learning Engine dùng chung:** lập phiên học, đánh giá tiến bộ, ôn tập và cá nhân hóa. Cơ chế chính xác cần thiết kế/kiểm thử.

## 7. Những giới hạn hiện tại
- Chưa chọn công nghệ, loại thiết bị ưu tiên cuối cùng, mô hình kinh doanh hay kế hoạch ra mắt.
- Tablet ngang 16:9, 2D cozy fantasy và phiên học ~5–10 phút là **đề xuất UX**, chưa được nghiệm thu.
- Không mặc định “lớp nào cũng học phép nhân”; học sinh lớp 1 có thể chỉ làm quen nhóm bằng nhau.
- Không xem XP/cấp nhân vật là thước đo năng lực học.

## 8. Liên quan
- [Game & Learning Loop](./02-game-and-learning-loops.md)
- [AI adaptive](./03-adaptive-ai-questions.md)
- [Quyết định & câu hỏi mở](./06-decisions-and-open-questions.md)
