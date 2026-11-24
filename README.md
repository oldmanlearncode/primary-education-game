# Little Explorers — Những Nhà Thám Hiểm Nhỏ 🌱🐉

> **Một thế giới phiêu lưu để trẻ khám phá, học tập và trưởng thành qua từng nhiệm vụ.**

**Little Explorers** là dự án trò chơi giáo dục dành cho học sinh tiểu học Việt Nam **từ lớp 1 đến lớp 5**. Thay vì trình bày kiến thức như những bài kiểm tra rời rạc, dự án hướng đến trải nghiệm **học qua khám phá**: trẻ chọn những vùng đất, thực hiện nhiệm vụ, học kiến thức mới, nhận phần thưởng và xây dựng ngôi làng của mình.

Dự án được thiết kế như **nền tảng đa môn học** — không chỉ là ứng dụng bảng cửu chương. Trong tương lai, mỗi môn học có thể có nhiều module, chủ đề, bài học và hoạt động tương ứng.

> **Trạng thái hiện tại (2026-11-24):** ✅ Giai đoạn 1 — Product Design/Discovery đã được xác nhận hoàn tất ở mức ý tưởng và nguyên tắc. 🟡 **Giai đoạn 2 — UX Design đang thực hiện.** Chưa có MVP hoặc trò chơi hoàn chỉnh.

## 🎯 Tầm nhìn

Little Explorers hướng tới ba mục tiêu:

1. **Học tập có ý nghĩa:** giúp trẻ hiểu, luyện tập, vận dụng và ghi nhớ kiến thức, không chỉ tích lũy điểm số.
2. **Khám phá thú vị:** trải nghiệm phiêu lưu bản đồ kết hợp mini-game, nhân vật đồng hành và ngôi làng có thể xây dựng/trang trí.
3. **Phụ huynh đồng hành:** phụ huynh theo dõi tiến độ đa môn, cung cấp đánh giá ban đầu, cùng con học, báo câu hỏi có vấn đề và tham gia những quyết định lộ trình quan trọng.

### Các môn học dự kiến

| Môn học | Module minh họa |
|---|---|
| **Toán** | Cộng, trừ, nhân, chia, hình học |
| **Tiếng Việt** | Đọc hiểu, chính tả |
| **Tự nhiên và Xã hội** | Thực vật, động vật và kiến thức đời sống |

Các module trên là định hướng nội dung; chương trình giáo dục chi tiết cần được rà soát trước khi phát hành.

## 🎮 Trải nghiệm học–chơi

Một vòng trải nghiệm dự kiến:

```text
Khám phá bản đồ
       ↓
Nhận nhiệm vụ
       ↓
Học & chơi mini-game
       ↓
Phản hồi và gợi ý phù hợp
       ↓
Nhận XP/vật liệu/phần thưởng
       ↓
Xây dựng ngôi làng
       ↓
Ôn tập và khám phá tiếp
```

Bé được **tự do chọn môn/vùng khám phá**; trong từng module, hệ thống hướng dẫn theo kiến thức nền và năng lực. Thành tích phiêu lưu, năng lực học tập và tiến trình xây làng được theo dõi **riêng biệt**.

Hình tượng đồng hành tạm gọi là **Milo**, một chú rồng nhỏ trong thế giới hoạt hình fantasy 2D thân thiện.

## 🧠 Adaptive Learning & AI

Little Explorers định hướng sử dụng **Adaptive Learning Engine** để lập kế hoạch học tập dựa trên bằng chứng: kết quả câu hỏi, mức hỗ trợ, sự đa dạng của hoạt động, khả năng ghi nhớ qua thời gian và độ tin cậy của đánh giá.

**AI Question Generation** có thể tạo các biến thể câu hỏi phù hợp kỹ năng và năng lực, nhưng nội dung phải qua các bước kiểm tra chất lượng trước khi đưa tới trẻ. Kiến trúc được định hướng theo **validated question pool + sinh bổ sung bằng AI khi cần**; không phụ thuộc vào việc gọi AI trực tiếp cho mọi lượt chơi.

Hệ thống phân biệt **Mastery**, **Confidence** và **Review Status**, cũng như năng lực **tự học** và **khi có người lớn hỗ trợ**. Câu hỏi hoặc phân loại phiên học có thể được đính chính với lịch sử thay đổi rõ ràng.

> Các chính sách/thuật toán chi tiết, công nghệ và ngưỡng đánh giá **chưa được chọn**; đây là định hướng thiết kế, không phải tuyên bố về các chức năng đã chạy.

## 🔐 Phân hệ người dùng & chính sách cấp tài khoản

Giai đoạn vận hành ban đầu gồm **Child World**, **Parent Portal** và **Admin Portal**. **Admin cấp phát/quản lý tài khoản phụ huynh**; phụ huynh sử dụng tài khoản được cấp để tạo hồ sơ cho con và thiết lập mục tiêu. **Chưa mở tự đăng ký công khai hoặc Guest Preview**. Các tính năng này có thể nghiên cứu ở giai đoạn mở rộng khi sản phẩm và hạ tầng sẵn sàng.

[Khám phá Admin Portal UX](./ux-design/04-admin-portal.md)

## 👨‍👩‍👧 Parent-Guided Learning

Phụ huynh không chỉ xem dashboard. Định hướng được thống nhất:

- Cung cấp thông tin ban đầu khi tạo hồ sơ trẻ; dữ liệu được hiệu chỉnh bằng hoạt động học thực tế.
- Xem lịch sử câu hỏi, báo nội dung sai/mơ hồ và nhận thông báo đính chính.
- Chỉnh lại ngữ cảnh phiên học (tự học / có người lớn hỗ trợ), giữ lịch sử dữ liệu gốc.
- Xem đề xuất điều chỉnh lộ trình, xác nhận những thay đổi quan trọng; Learning Engine vẫn bảo đảm trẻ được hỗ trợ khi gặp khó khăn.
- Tham gia chế độ **Learn Together**.

Dashboard tổng quan dành cho phụ huynh sẽ hiển thị **nhiều môn học**, sau đó mới đi sâu theo môn và module.

## 🌳 Module đầu tiên: Rừng Bảng Nhân 2

Module thử nghiệm đầu tiên thuộc môn **Toán → Phép Nhân**. Một số mini-game đang được khám phá:

- **Thu hoạch táo:** hiểu nhóm đồ vật bằng nhau.
- **Ghép thẻ:** nối phép tính với kết quả hoặc hình minh họa.
- **Xây cầu:** dùng kiến thức để hoàn thành nhiệm vụ trên bản đồ.
- **Thử thách tổng hợp và ôn tập:** vận dụng, nhớ lại và nhận thưởng để phát triển ngôi làng.

Đây là **một lát cắt trải nghiệm (vertical slice)** để kiểm chứng nền tảng, không phải giới hạn nội dung của Little Explorers.

## 🗺️ Lộ trình phát triển

| # | Giai đoạn | Nội dung | Trạng thái |
|---|---|---|---|
| 1 | **Product Design** | Tài liệu yêu cầu, mục tiêu học tập, game loop | ✅ Hoàn tất ở mức Product Discovery |
| 2 | **UX Design** | User flow, sitemap, wireframe toàn bộ màn hình | 🟡 Đang thực hiện |
| 3 | **Visual Design** | Design system, nhân vật, bản đồ, UI kit | ⬜ Chưa bắt đầu |
| 4 | **Prototype** | Bản tương tác Rừng Bảng Nhân 2 | ⬜ Chưa bắt đầu |
| 5 | **Learning Design** | Ngân hàng câu hỏi, gợi ý, thuật toán ôn tập | ⬜ Chưa bắt đầu |
| 6 | **Playtesting** | Kiểm thử với học sinh nhiều nhóm tuổi | ⬜ Chưa bắt đầu |
| 7 | **MVP** | Phép Nhân, phần thưởng, ngôi làng, phụ huynh | ⬜ Chưa bắt đầu |

➡️ **Chi tiết và điều kiện hoàn tất:** [ROADMAP.md](./ROADMAP.md)

## 📁 Tài liệu dự án

```text
primary-education-game/
├── README.md                  # Giới thiệu & trạng thái dự án
├── ROADMAP.md                 # 7 giai đoạn phát triển
├── idea-summarize/            # Ý tưởng, quyết định đã chốt, edge cases
└── ux-design/                 # Giai đoạn 2: Child/Parent/Admin IA, flows, screens
```

- [Kho ý tưởng và tài liệu Product Discovery](./idea-summarize/README.md)
- [Decision Log — các quyết định đã xác nhận](./idea-summarize/06-decisions-and-open-questions.md)
- [Consolidated Review — 53 recommendations và EC](./idea-summarize/08-consolidated-review.md)
- [UX Design — bắt đầu giai đoạn 2](./ux-design/README.md)

## 🎨 Thiết kế Figma

[Figma — Little Explorers: Wireframes & UI Concepts](https://www.figma.com/design/sC9vpDkKAruU3dgV7shCAJ)

File hiện có chứa concept cho một số màn hình Child World và Parent Portal; **chưa phải toàn bộ UX được nghiệm thu**.

## 🔄 Quy tắc cập nhật dự án

README là **trang giới thiệu và cập nhật tiến trình cấp cao**. Khi có thay đổi đáng kể:
- Cập nhật trạng thái roadmap và liên kết tài liệu đầu ra.
- Tóm tắt các cột mốc sản phẩm hoặc quyết định ảnh hưởng đến định hướng.
- Giữ nội dung chi tiết trong `idea-summarize/`, `ux-design/` và thư mục giai đoạn tương ứng để README dễ đọc.
- **Không suy diễn đã hoàn thiện tính năng từ việc hoàn thành bản vẽ/tài liệu.**

---

**Little Explorers** đang ở giai đoạn thiết kế — cùng xây dựng một trải nghiệm học tập vừa thú vị, vừa có trách nhiệm với trẻ và phụ huynh. 🐉
