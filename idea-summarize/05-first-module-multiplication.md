# 05 — Module khám phá đầu tiên: Phép nhân

> **Đây là ví dụ để thử nghiệm platform, KHÔNG phải toàn bộ sản phẩm.** Nội dung cần đối chiếu chương trình/khối lớp với người có chuyên môn.

## 1. Mục tiêu giáo dục [PROPOSED]
1. Hiểu phép nhân qua các nhóm đồ vật bằng nhau, cộng lặp.
2. Nhận diện và tính bảng nhân theo khả năng.
3. Nhớ lại kết quả qua thời gian, không chỉ sau một bài.
4. Vận dụng phép nhân trong tình huống thật và nhiệm vụ game.

Đối tượng lớp 1–5 của **nền tảng** không có nghĩa bắt mọi bé học bảng nhân. Với lớp 1, hoạt động tiền đề như nhóm bằng nhau có thể dùng nếu phù hợp.

## 2. Đảo Phép Nhân [PROPOSED]
Các vùng minh họa: Đồng Cỏ Nhóm Số; Rừng Bảng 2; Vườn Bảng 5; Hồ Bảng 3; Núi Bảng 4; Hang Bảng 6–7; Lâu Đài Bảng 8–9; Đấu Trường Tổng Hợp; Tháp Ghi Nhớ. Lộ trình có định hướng nhưng thích ứng theo skill.

## 3. Rừng Bảng Nhân 2 — vertical slice đề xuất
| Màn | Nhiệm vụ | Năng lực trọng tâm | Hoạt động |
|---|---|---|---|
| 1 | Thu hoạch táo | Hiểu nhóm bằng nhau | kéo quả vào giỏ, hiển thị `3 × 2 = 6` |
| 2 | Ghép thẻ thần kỳ | Ghép biểu thức–kết quả | nối `2 × 4` với `8` |
| 3 | Xây cầu qua sông | Luyện tính | mỗi câu giải giúp thêm đoạn cầu, sai có gợi ý |
| 4 | Mê cung bí mật | Vận dụng | chọn đường bằng phép tính/bài toán |
| 5 | Giải cứu Milo | Đánh giá tổng hợp | nhận biết/điền khuyết/giải tình huống |
| 6 | Kho báu ghi nhớ | Ôn tập dài hạn | xuất hiện lặp lại vào các phiên sau |

Cả 6 là **thiết kế ý tưởng**; phạm vi MVP thực tế (3 mini-game hay cả 6) chưa chốt.

## 4. Ví dụ dạng câu hỏi
- Trực quan: 3 giỏ, mỗi giỏ 2 táo; tổng bao nhiêu?
- Ghép: `4 × 5` ↔ `20`.
- Điền chỗ trống: `2 × ? = 12`.
- Tình huống: 6 hàng rào, mỗi hàng rào 4 khúc gỗ.
- Recall: hỏi lại skill cần ôn, câu chữ/tình huống khác.

**AI tạo câu hỏi** là ý tưởng riêng có [phương án hybrid và validator](./03-adaptive-ai-questions.md), chưa được chốt.

## 5. Phản hồi & ôn tập [PROPOSED]
- Đúng: xác nhận, giải thích khi phù hợp; sai: gợi ý nhẹ → hình ảnh → giải thích từng bước.
- Không trừ XP, không timer cưỡng ép ở đánh giá chính.
- Trạng thái skill: chưa học / đang học / đang luyện / cần ôn / thành thạo.
- Thời điểm ôn thử nghiệm: khoảng 1, 3, 7, 14, 30 ngày; **không phải lịch cố định**; dựa vào kết quả nhớ lại.

## 6. Kết nối sang ngôi làng [PROPOSED]
Hoàn thành nhiệm vụ nhận gỗ/đá/hạt; dùng để dựng công trình nhỏ đầu tiên. Vật liệu được cấp theo nỗ lực, không ngăn bé học chậm. Giả thuyết: xây làng tăng động lực dài hạn nhưng phải đo xem có lấn át mục tiêu học hay không.

## 7. Một phiên học ví dụ (không ràng buộc)
- 2–3 phút khám phá
- 3–4 phút mini-game
- 1–2 phút recall
- nhận thưởng & dừng ở checkpoint
Thời lượng này là gợi ý, cần thử nghiệm theo tuổi và kỹ năng.

## 8. Chưa chốt [OPEN]
- Học theo thứ tự bảng 2, 5, 3... hay theo năng lực?
- Định nghĩa “thành thạo” bằng minh chứng nào, theo từng dạng bài?
- Khối lớp áp dụng và tiêu chí prerequisite?
- Cân bằng câu hỏi mới/cũ và cách ôn?
- Dùng AI câu hỏi on-demand hay pool đã kiểm duyệt?
- Phạm vi vertical slice, tiêu chí đánh giá trẻ hiểu bài.
