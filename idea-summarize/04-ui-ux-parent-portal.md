# 04 — UI/UX Ideas & Parent Portal

> Bản vẽ Figma **mang tính khám phá**, chưa phải thiết kế được nghiệm thu.

## 1. Visual direction [PROPOSED]
2D cartoon / cozy fantasy, màu tươi, thân thiện, nút chạm lớn, ít chữ cho lớp nhỏ, giọng nói hướng dẫn, không phạt câu sai. Tablet landscape 16:9 làm điểm khởi đầu thiết kế; cần kiểm chứng thiết bị và accessibility cho lớp 1–5.

## 2. Child-world screens đã phác thảo trên Figma
Có **5 wireframe + 5 high-fidelity concept**:
1. Home / Làng Khởi Đầu
2. World Map / Bản đồ thế giới
3. Multiplication Map / Đảo Phép Nhân
4. Learning Game / Xây cầu
5. Village Builder / Ngôi làng

Các concept hi-fi vẫn là lớp khối/vector/text chỉnh sửa được, **chưa có character art/animation cuối**. Milo và game assets cần làm tiếp.

## 3. Parent Portal — 4 wireframes đã tạo
1. **Dashboard Tổng quan:** số buổi, thời gian, **môn học đang tham gia**, nhiệm vụ cần ôn, biểu đồ hoạt động và xu hướng theo **môn**.
2. **Settings / Mục tiêu & thời gian:** chọn **môn trước, module sau**, buổi/tuần, thời lượng và điểm nghỉ an toàn, giảm hoạt ảnh/âm thanh.
3. **Student Profiles:** nhiều hồ sơ, lớp, mức phù hợp, chuyển hồ sơ, lộ trình cá nhân hóa.
4. **Privacy & Notifications:** thông báo đến hạn ôn, báo cáo, xem/xuất/xóa dữ liệu với xác thực người giám hộ.

**Quy tắc quan trọng [CONFIRMED — user correction]:**
> Dashboard tổng quan **không được có KPI “Phép nhân thành thạo”** hay liệt kê `6 × 7` như chỉ số mặc định của cả ứng dụng. Phép nhân chỉ là module trong môn Toán.

## 4. Báo cáo có ba cấp [ĐỊNH HƯỚNG ĐÃ THỐNG NHẤT]
- **Platform overview:** tổng hợp học tập đa môn, không gộp tất cả môn thành một điểm “thành thạo” vô nghĩa.
- **Subject detail:** ví dụ Toán → Phép cộng/Phép trừ/Phép nhân/Hình học...
- **Module detail:** ví dụ Phép nhân → từng bảng, phép tính, heatmap, recall và dạng bài.

Cấp module chỉ là **đề xuất chức năng chi tiết**; heatmap chưa được dựng thành wireframe.

## 5. UX safety & edge cases [PROPOSED]
Có hướng dẫn bằng giọng nói cho trẻ ít chữ; khi sai dùng gợi ý nhiều tầng; cho tạm dừng/tự ngắt ở checkpoint; hỗ trợ giảm animation; tránh bảng xếp hạng trẻ em công khai. Adult gate bảo vệ cấu hình phụ huynh. Chưa chốt chính sách tự động hết giờ.

## 6. Liên kết thiết kế
- [Figma — toàn bộ file](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ)
- [Parent Portal — 4 wireframes](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ?node-id=4-2)
- [Parent Dashboard sau sửa thành đa môn](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ?node-id=4-5)

## 7. Chưa chốt
- Interaction flows/clickable prototype; empty/loading/error/offline states.
- Visual design cho nhóm 10–11 tuổi, multi-device responsive.
- Cấp report theo môn và module, heatmap, tiêu chí diễn giải kết quả cho phụ huynh.
- Kiểm thử khả năng hiểu với trẻ và phụ huynh thực tế.
