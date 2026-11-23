# 08 — Consolidated Product Review: confirmed recommendations & edge cases

> **2026-11-23 · Product Discovery — REVIEWED & CONFIRMED by product owner**  
> Người dùng xác nhận **tất cả 53 phương án khuyến nghị** trong mục B, cách xử lý **45 edge case EC-01…EC-45** (mục C/G và tài liệu 09), và đồng ý định hướng các ý tưởng khám phá trong mục D.  
> **CONFIRMED = chốt nguyên tắc/định hướng sản phẩm; không đồng nghĩa có giải pháp kỹ thuật, ngưỡng số, ngân sách, lịch triển khai hoặc tính năng MVP được chốt.**  
> Các câu hỏi từng OPEN bên dưới được **giữ nguyên làm lịch sử review**, nhưng cột trạng thái là nguồn xác thực hiện hành.  
> **P0/P1/P2** = mức ưu tiên thiết kế, **không phải cam kết đưa vào MVP**.

## A. Đã chốt — KHÔNG hỏi lại
| ID | Nội dung |
|---|---|
| D-001 | Học sinh tiểu học Việt Nam lớp 1–5 |
| D-002 | Nền tảng **đa môn**; từng môn có nhiều module |
| D-003 | Module đầu tiên để khám phá/kiểm chứng: **Phép nhân** |
| D-004 | Phiêu lưu bản đồ (A) làm lõi + xây/trang trí làng (C) làm thưởng dài hạn |
| D-005 | Khám phá có định hướng: được chọn môn/vùng, lộ trình trong module tùy năng lực |
| D-006 | Có dashboard/cấu hình phụ huynh |
| D-007 | Dashboard tổng quan **đa môn**, chi tiết phép nhân chỉ ở cấp module |
| D-008 | Chỉ là **ideas**, chưa phải plans |
| D-009 | **Phụ huynh định hướng mục tiêu, Learning Engine đảm bảo trải nghiệm phù hợp và hỗ trợ khi cần** (Parent-Guided option C) |

## B. 53 khuyến nghị đã được xác nhận (CONFIRMED)

### B1. Product foundation & curriculum
| ID | P | Câu hỏi / các lựa chọn | Khuyến nghị đã chốt | Trạng thái |
|---|---|---|---|---|
| PF-01 | P0 | Curriculum nguồn nào cho từng môn/lớp? | Dùng mục tiêu học tập có nguồn, phiên bản và người phụ trách duyệt; kiểm chứng theo chương trình VN | ✅ **CONFIRMED** |
| PF-02 | P0 | Chuẩn phân cấp Subject→Module→Topic→Lesson→Skill→Activity áp dụng cứng hay linh hoạt? | Phân cấp nội dung + skill quan hệ N:N; tránh ghép skill cứng vào lesson | ✅ **CONFIRMED** |
| PF-03 | P0 | Ai là người chịu trách nhiệm giáo dục và phê duyệt nội dung? | Có vai trò subject-matter reviewer trước khi mở nội dung chưa tự kiểm chứng | ✅ **CONFIRMED** |
| PF-04 | P1 | Điều kiện mở khóa: level game hay prerequisite kiến thức? | Khám phá tự do, chặn chọn lọc ở hoạt động đòi điều kiện; luôn có lối đi luyện tập | ✅ **CONFIRMED** |
| PF-05 | P1 | Module khác Toán phải có loại activity riêng không? | Có: reusable templates + môn đặc thù | ✅ **CONFIRMED** |
| PF-06 | P2 | Mô hình thương mại và phạm vi nhà trường/giáo viên? | Chưa quyết; không giả định học sinh chỉ dùng tại nhà | ✅ **CONFIRMED** |

### B2. Student learning model
| ID | P | Câu hỏi / các lựa chọn | Khuyến nghị đã chốt | Trạng thái |
|---|---|---|---|---|
| AL-01 | P0 | Định nghĩa 1 skill ở mức nào? | Skill đo lường được; tách hiểu–tính–vận dụng–nhớ | ✅ **CONFIRMED** |
| AL-02 | P0 | Tiêu chí “thành thạo”? | Nhiều lần, nhiều dạng, thời gian giãn cách + mức confidence | ✅ **CONFIRMED** |
| AL-03 | P0 | Parent cold start vs discovery test? | Parent input tạo prior; ngắn gọn, kiểm chứng qua hoạt động thực | ✅ **CONFIRMED** |
| AL-04 | P0 | Mâu thuẫn Parent Report và performance? | Phân biệt source, confidence, giải thích cho phụ huynh, không đổi gấp | ✅ **CONFIRMED** |
| AL-05 | P0 | Independent vs supported performance? | Ghi riêng bằng chứng và dùng riêng khi đánh giá năng lực độc lập | ✅ **CONFIRMED** |
| AL-06 | P0 | Skill prerequisites/graph? | Có graph từng môn, cross-skill khi thực sự cần; tránh cycle | ✅ **CONFIRMED** |
| AL-07 | P1 | Khi nào điều chỉnh độ khó? | Session plan + in-session adaptation nhỏ trong phạm vi mục tiêu | ✅ **CONFIRMED** |
| AL-08 | P1 | Mastery có giảm/đến hạn ôn? | Có; trạng thái ôn tập tách khỏi kết luận mất năng lực | ✅ **CONFIRMED** |
| AL-09 | P1 | Cách đánh giá kỹ năng thuộc nhiều môn/dạng bài? | Tracking evidence nguồn và ngữ cảnh; không gộp điểm tùy tiện | ✅ **CONFIRMED** |
| AL-10 | P1 | Một câu sai do đọc hiểu hay do phép tính? | Evidence phân biệt target skill / supporting skill / ambiguity | ✅ **CONFIRMED** |
| AL-11 | P2 | Giữ tính minh bạch, giải thích level cho phụ huynh? | Explanation bằng evidence và confidence, không nhãn cố định | ✅ **CONFIRMED** |

### B3. AI / question generation & content integrity
| ID | P | Câu hỏi / các lựa chọn | Khuyến nghị đã chốt | Trạng thái |
|---|---|---|---|---|
| AI-01 | P0 | Sinh on-demand mỗi lượt hay hybrid? | Dynamic session plan + curated/validated pool + on-demand bổ sung | ✅ **CONFIRMED** |
| AI-02 | P0 | Ranh giới AI vs Learning Engine? | Engine chọn *what/why*; AI viết *how*, không tự đổi skill/luật | ✅ **CONFIRMED** |
| AI-03 | P0 | Gate phát hành câu AI? | Khác nhau theo mức tự động kiểm chứng; zero unvalidated content cho trẻ | ✅ **CONFIRMED** |
| AI-04 | P0 | Ai/điều gì có quyền xác nhận đáp án? | Deterministic validation nơi có thể; human reviewer/nguồn chuẩn nơi không thể | ✅ **CONFIRMED** |
| AI-05 | P0 | Câu lỗi đã phát hành xử lý thế nào? | Versioning, quarantine, impact scan, chấm lại learning evidence | ✅ **CONFIRMED** |
| AI-06 | P1 | Novelty vs spaced recall? | Tránh lặp văn bản/thứ tự vô ý; chủ động lặp kỹ năng | ✅ **CONFIRMED** |
| AI-07 | P1 | Một hay đa AI provider? | Một provider thử nghiệm; abstraction để sau này benchmark | ✅ **CONFIRMED** |
| AI-08 | P1 | AI down/chậm/hết quota/pool thiếu? | Fallback câu đã được kiểm duyệt, không hạ validation gate | ✅ **CONFIRMED** |
| AI-09 | P1 | Duplicate detection và Question Family? | Cùng knowledge target, variant có metadata skill + format | ✅ **CONFIRMED** |
| AI-10 | P1 | Tự luận/đọc hiểu nhiều đáp án đúng? | Rubric và content approval riêng; chưa dùng auto-grade tùy tiện | ✅ **CONFIRMED** |
| AI-11 | P1 | AI có sinh đáp án/giải thích/gợi ý? | Có thể; nhưng explanation cũng phải được kiểm tra | ✅ **CONFIRMED** |
| AI-12 | P1 | Prompt injection/hướng dẫn độc hại trong nội dung AI? | Xem output là untrusted; allowlist schema; reject instructions lạ | ✅ **CONFIRMED** |
| AI-13 | P2 | AI tạo hình/giọng nói/thoại NPC? | Ưu tiên asset đã kiểm duyệt; chỉ mở rộng khi có kiểm tra | ✅ **CONFIRMED** |
| AI-14 | P2 | Cách đo cost/latency và chất lượng theo provider? | Benchmark bằng bộ mẫu nhiều môn/độ tuổi | ✅ **CONFIRMED** |

### B4. Parent authority & engagement
| ID | P | Câu hỏi / các lựa chọn | Khuyến nghị đã chốt | Trạng thái |
|---|---|---|---|---|
| PA-01 | P0 | Phụ huynh sửa *mục tiêu* hay sửa *mastery*? | Chỉnh mục tiêu, không ghi đè bằng chứng học | ✅ **CONFIRMED** |
| PA-02 | P0 | Thay đổi nào cần approval? | 3 cấp: hỗ trợ ngay; thay đổi module có giám sát; thay đổi lớn cần đồng ý | ✅ **CONFIRMED** |
| PA-03 | P0 | Hết hạn sau 3/7 ngày thì sao? | Auto-apply chỉ nếu opt-in rõ và rủi ro thấp; im lặng không mặc định đồng ý | ✅ **CONFIRMED** |
| PA-04 | P0 | Phụ huynh yêu cầu thử khó hơn dù evidence yếu? | Cho khám phá guided/learn together; tách chứng cứ độc lập | ✅ **CONFIRMED** |
| PA-05 | P1 | Review câu hỏi con làm có quyền loại câu ngay? | Parent reports → triage/quarantine theo rủi ro → expert review | ✅ **CONFIRMED** |
| PA-06 | P1 | Ai kiểm duyệt và thông báo kết quả report? | Role/chính sách rõ; không cho người report tự thay đáp án toàn hệ thống | ✅ **CONFIRMED** |
| PA-07 | P1 | Cách ghi nhận phụ huynh hỗ trợ? | Chọn Learn Together khi bắt đầu hoặc cuối phiên; không hỏi mỗi câu | ✅ **CONFIRMED** |
| PA-08 | P1 | 2 người giám hộ bất đồng? | Chủ hồ sơ/quyền quản trị, nhật ký, policy conflict resolution | ✅ **CONFIRMED** |
| PA-09 | P1 | Tần suất, loại thông báo? | Action Center: cần xác nhận / nên xem / gợi ý, giới hạn tần suất | ✅ **CONFIRMED** |
| PA-10 | P2 | Phụ huynh tự tạo bài tập/học liệu? | Khám phá sau; xác thực/validation nếu mở | ✅ **CONFIRMED** |
| PA-11 | P1 | Cấu hình theo từng trẻ, từng môn hay toàn tài khoản? | Phân tầng account → child → subject/module; có inheritance rõ | ✅ **CONFIRMED** |
| PA-12 | P1 | Parent approval đang chờ khi bé tiếp tục chơi? | Không chặn học; hoạt động an toàn hiện tại vẫn khả dụng | ✅ **CONFIRMED** |

### B5. Gameplay, UX, reporting & MVP
| ID | P | Câu hỏi / các lựa chọn | Khuyến nghị đã chốt | Trạng thái |
|---|---|---|---|---|
| GM-01 | P1 | Game Loop vs Learning Loop bắt buộc ở mọi hoạt động? | Learning goal bắt buộc; các phase có thể khác tùy môn | ✅ **CONFIRMED** |
| GM-02 | P1 | XP/sao/vật liệu: có farm bằng chơi lại? | Diminishing rewards, vẫn thưởng cố gắng/recall, không pay-to-win | ✅ **CONFIRMED** |
| GM-03 | P1 | Làng có ảnh hưởng việc mở kiến thức? | Chủ yếu mỹ thuật; không khóa học vì thiếu vật liệu | ✅ **CONFIRMED** |
| GM-04 | P1 | MVP là 1 vùng 3 mini-game hay đủ 6? | Vertical slice có đủ intro→learn→play→recall→reward→build→parent | ✅ **CONFIRMED** |
| GM-05 | P1 | Phiên học/giới hạn màn hình? | Pause/resume & checkpoint; không cắt ngang lúc đang giải | ✅ **CONFIRMED** |
| GM-06 | P1 | Dashboard tổng quan vs môn vs module hiển thị gì? | Tổng quan đa môn; subject module; module skill/recall/heatmap | ✅ **CONFIRMED** |
| GM-07 | P1 | Thiết bị, offline, voice, tiếp cận cho trẻ lớp 1? | Validate tablet/mobile/desktop, ít chữ, hỗ trợ âm thanh và giảm motion | ✅ **CONFIRMED** |
| GM-08 | P2 | Milo và mỹ thuật phù hợp cả lớp 1–5? | Test nhóm tuổi, tùy chỉnh visual density | ✅ **CONFIRMED** |
| GM-09 | P2 | Học theo nhóm/giáo viên/nhà trường? | Chưa mở; ảnh hưởng quyền và dữ liệu lớn | ✅ **CONFIRMED** |
| GM-10 | P1 | Tiêu chí thử nghiệm thành công? | Retention evidence, usability trẻ/cha mẹ, safety, không đo chỉ bằng thời gian chơi | ✅ **CONFIRMED** |

## C. Edge cases EC-01…EC-30 — hướng xử lý đã CONFIRMED

| ID | P | Tình huống | Cách xử lý được chấp thuận | Trạng thái |
|---|---|---|---|---|
| EC-01 | P0 | Hai anh chị em dùng chung máy, chọn sai hồ sơ | Dữ liệu năng lực nhiễm chéo; xác nhận hồ sơ rõ trước phiên và cho sửa nhầm | ✅ **CONFIRMED** |
| EC-02 | P0 | Phụ huynh trợ giúp nhưng phiên gắn “tự học” | Đánh giá năng lực quá cao; hỗ trợ khai báo bổ sung và reclassify evidence | ✅ **CONFIRMED** |
| EC-03 | P0 | Câu hỏi sai được dùng cho 10.000 phiên rồi mới phát hiện | Impact tracing, rollback/scoring correction, thông báo minh bạch | ✅ **CONFIRMED** |
| EC-04 | P0 | Bài học có nhiều đáp án hợp lệ / câu AI ambiguous | Không ép một đáp án; invalidation + re-score | ✅ **CONFIRMED** |
| EC-05 | P0 | Phụ huynh yêu cầu tăng khó, bé thất bại liên tiếp | Safe scaffold/exit, không cố luyện đến khi đạt vì approval | ✅ **CONFIRMED** |
| EC-06 | P0 | Phụ huynh không phản hồi khi hết hạn, device offline | Policy snapshot + deadline server, idempotent auto action, sự kiện log rõ ràng | ✅ **CONFIRMED** |
| EC-07 | P0 | Phụ huynh A đồng ý, phụ huynh B từ chối | Quyền quản trị/ưu tiên, conflict & notification, audit | ✅ **CONFIRMED** |
| EC-08 | P0 | Thay phiên bản câu hỏi trong lúc bé đang làm | Pinned question version cho session, sửa kết quả hậu kiểm nếu cần | ✅ **CONFIRMED** |
| EC-09 | P0 | AI tạo lời giải sai dù đáp án đúng | Validate explanation riêng, không phát hành gợi ý chưa kiểm tra | ✅ **CONFIRMED** |
| EC-10 | P0 | AI sinh nội dung bất hợp tuổi hay chứa thông tin định danh | Content safety, no child PII in prompts, quarantine + incident process | ✅ **CONFIRMED** |
| EC-11 | P1 | Bé làm đúng do đoán may mắn/câu trắc nghiệm ít lựa chọn | Confidence theo dạng bài, không phong mastery vì vài câu đúng | ✅ **CONFIRMED** |
| EC-12 | P1 | Bé trả lời chậm vì đọc chậm hay motor skill, không phải chưa hiểu Toán | Latency là chỉ số phụ, không hạ level dựa vào tốc độ đơn lẻ | ✅ **CONFIRMED** |
| EC-13 | P1 | Skill prerequisite tạo vòng lặp hoặc thay đổi curriculum giữa năm | Validate skill graph, content version, migration/learning continuity | ✅ **CONFIRMED** |
| EC-14 | P1 | Bé tạm nghỉ dài ngày / chuyển lớp giữa năm | Gentle return, stale confidence, không reset hay ép kiểm tra lại toàn bộ | ✅ **CONFIRMED** |
| EC-15 | P1 | Bé bỏ dở/mất mạng/thiết bị hết pin hoặc nộp trùng đáp án | Resume, dedup attempts, event idempotency; giữ tiến trình | ✅ **CONFIRMED** |
| EC-16 | P1 | Học offline rồi hai thiết bị đồng bộ khác nhau | Chính sách conflict cho tiến độ, rewards và parent policy | ✅ **CONFIRMED** |
| EC-17 | P1 | AI không có câu đủ tốt cho skill hiếm | Fallback/giảm số câu/hoãn session có hướng dẫn; không thả câu lỗi | ✅ **CONFIRMED** |
| EC-18 | P1 | Phụ huynh report nhầm/hàng loạt; cố tình làm sai report | Audit, triage, chống lợi dụng quarantine, cơ chế phản hồi minh bạch | ✅ **CONFIRMED** |
| EC-19 | P1 | Bé lặp màn để farm gỗ, bỏ qua mục tiêu học | Reward cap/diminishing return, nội dung học không bị khóa vì vật liệu | ✅ **CONFIRMED** |
| EC-20 | P1 | Một kết quả bị tính đôi do một câu gắn nhiều skill | Primary/secondary skill evidence weighting; không double count | ✅ **CONFIRMED** |
| EC-21 | P1 | Bài toán văn chứa từ khó làm bé sai toán dù nhớ bảng nhân | Ghi nhận evidence đọc hiểu vs tính; dễ đọc/âm thanh hỗ trợ | ✅ **CONFIRMED** |
| EC-22 | P1 | Nội dung Tự nhiên và Xã hội thay đổi hoặc có tranh luận | Provenance, version, source / reviewer, phân biệt sự thật–ngữ cảnh | ✅ **CONFIRMED** |
| EC-23 | P1 | Giới hạn thời gian tới hạn khi bé đang ở giữa câu hỏi | Pause at safe checkpoint + sync with parent policy, không phạt | ✅ **CONFIRMED** |
| EC-24 | P1 | Trẻ có nhu cầu tiếp cận khác: đọc chậm, nhạy cảm âm thanh, rối loạn vận động | Reduced motion/audio toggle, phương thức trả lời thay thế, không suy đoán chẩn đoán | ✅ **CONFIRMED** |
| EC-25 | P1 | Parent onboarding bỏ trống, khai quá cao/thấp, dữ liệu đổi theo thời gian | Cho skip, edit, calibrate confidence từ hành vi thực | ✅ **CONFIRMED** |
| EC-26 | P1 | Phụ huynh xem question history có thông tin nhạy cảm trong nội dung AI | Rà soát, lọc dữ liệu, retention/access rights | ✅ **CONFIRMED** |
| EC-27 | P2 | Trẻ muốn mở module ngoài khối lớp trước khi được phê duyệt | Có vùng preview/guided không ghi mastery và không phá prerequisite | ✅ **CONFIRMED** |
| EC-28 | P2 | Học sinh lớp 5 thấy game “quá trẻ con”; lớp 1 chưa biết đọc | Chế độ hiển thị/giọng nói, test usability theo tuổi | ✅ **CONFIRMED** |
| EC-29 | P2 | Phụ huynh bị quá tải thông báo; bỏ qua mọi đề xuất | Priority queue, digest, giới hạn alerts và kiểm tra hiểu biết | ✅ **CONFIRMED** |
| EC-30 | P2 | Dữ liệu cần xóa nhưng event audit cần truy vết | Chính sách retention, tách audit không định danh, đối chiếu quy định hiện hành | ✅ **CONFIRMED** |

## D. Các hướng khám phá được đồng ý về nguyên tắc (CONFIRMED AS DIRECTION — NOT MVP SCOPE)
1. **Learning Evidence Timeline:** hiển thị vì sao hệ thống đề xuất level mới; lưu nguồn phụ huynh/tự học/có hỗ trợ.
2. **Confidence-aware UI:** thay “bé yếu Toán” bằng “chưa đủ bằng chứng” hoặc “cần ôn”.
3. **Parent-child micro-quests:** 5 phút hoạt động ngoại tuyến, không cần màn hình; phụ huynh đánh dấu đã cùng làm.
4. **Question incident console:** truy tìm mọi phiên bị tác động bởi câu hỏi sai, hành động chấm lại.
5. **Curriculum versioning:** có hiệu lực theo lớp/năm học, không làm mất tiến trình cũ.
6. **Explainable recommendations:** đề xuất có lý do, mức chắc chắn và nút “xem bằng chứng”.
7. **Mastery without grind:** khi bé biết sẵn, dùng mini-assessment để bỏ qua phần lặp, vẫn giữ nhiệm vụ cốt truyện.
8. **Adaptive accessibility:** thay đổi cách trình bày/đầu vào mà không âm thầm thay chuẩn kiến thức.
9. **Learning Mode preference:** Tự học, Cùng phụ huynh, Khám phá nâng cao, nhưng phân biệt bằng chứng.
10. **Content observability:** theo dõi tỉ lệ báo lỗi, tần suất thất bại bất thường theo blueprint, skill, nhóm tuổi.

## E. 12 chủ đề ưu tiên đặc tả/kiểm thử sau khi chốt định hướng
- **R-01:** Định nghĩa 1 skill (AL-01) và cách công nhận mastery (AL-02)?
- **R-02:** Bằng chứng tự học vs có hỗ trợ (AL-05) xử lý như thế nào?
- **R-03:** Parent Cold Start (AL-03/04): hỏi gì, skip, hiệu chỉnh?
- **R-04:** AI mỗi phiên vs hybrid (AI-01), fallback và validation gate (AI-03/08)?
- **R-05:** Chính sách báo câu hỏi sai và re-score (AI-05, PA-05/06)?
- **R-06:** Quyền phụ huynh: chỉnh mục tiêu hay mastery (PA-01)?
- **R-07:** Approval levels và ranh giới tự điều chỉnh (PA-02/04)?
- **R-08:** Hết hạn 3–7 ngày: policy default và các loại auto-apply (PA-03)?
- **R-09:** Đối tượng kiểm duyệt/curriculum ownership (PF-01/03)?
- **R-10:** Đoạn MVP đủ 1 game loop và 1 learning loop (GM-04)?
- **R-11:** Quyền nhiều người giám hộ/nhiều bé (PA-08, EC-01/07)?
- **R-12:** Quyền riêng tư, lưu/xóa dữ liệu và bảo vệ trẻ khi dùng AI (EC-10/26/30)?

## F. Mẫu ghi quyết định
```markdown
### [ID] Tên quyết định
- Status: CONFIRMED / PROPOSED / OPEN / DEFERRED / SUPERSEDED
- Date: YYYY-MM-DD
- Decision: ...
- Reason: ...
- Rejected alternatives: ...
- Impacts: Learning / AI / Child UI / Parent UI / Safety / Content
- Follow-ups: ...
```

**Chú ý:** không nên chốt các chỉ số như số ngày recall, % mastery hoặc điểm tự tin bằng trực giác; cần thử nghiệm và phản biện chuyên môn giáo dục. Chính sách pháp lý/bảo vệ dữ liệu trẻ em phải được xác minh trước vận hành, không suy ra từ ý tưởng.


## G. EC-31…EC-45 — hướng xử lý đã CONFIRMED (2026-11-23)

**Chủ trương người dùng đã xác nhận**:
- EC-02: Phụ huynh được đổi phân loại phiên học đã ghi nhầm, lưu toàn bộ dữ liệu và lịch sử chỉnh sửa.
- EC-03: Có thông báo/email đính chính và điều chỉnh kết quả; xử lý cả tình huống **nhiều câu hỏi sai cùng bộ**.
- EC-12: Ghi nhận các mốc thời gian ngầm, tham khảo kỹ năng Tiếng Việt để diễn giải bài Toán có lời văn.

**Cập nhật 2026-11-23:** người dùng đã **CONFIRMED** các hướng xử lý EC-02/03/12 và các khuyến nghị còn lại, bao gồm nguyên tắc raw event bất biến + editable context, phân tầng incident, session invalidation khi thiếu bằng chứng và không suy diễn thời gian đọc từ một mốc. Ngưỡng định lượng, UI chi tiết và thuật toán vẫn cần kiểm thử/đặc tả.

### Edge case bổ sung (EC-31…EC-45)
- EC-31 — ✅ CONFIRMED: Sửa mode phiên muộn sau khi đã nâng level.
- EC-32 — ✅ CONFIRMED: Hai người giám hộ sửa phân loại mâu thuẫn.
- EC-33 — ✅ CONFIRMED: Sửa mode nhưng đã có recall độc lập sau đó.
- EC-34 — ✅ CONFIRMED: Lạm dụng chỉnh session để nâng mastery.
- EC-35 — ✅ CONFIRMED: Câu sai được phát hiện sau nhiều tháng, tác động dây chuyền.
- EC-36 — ✅ CONFIRMED: Câu sai hàng loạt không cùng nguyên nhân.
- EC-37 — ✅ CONFIRMED: Hủy nhiều câu làm phiên không còn ý nghĩa đánh giá.
- EC-38 — ✅ CONFIRMED: Email không gửi được/không được đọc.
- EC-39 — ✅ CONFIRMED: Câu thay đổi giữa phiên đang làm.
- EC-40 — ✅ CONFIRMED: Re-score ảnh hưởng đề xuất đã được phụ huynh phê duyệt.
- EC-41 — ✅ CONFIRMED: Không tách được chính xác đọc vs suy nghĩ chỉ từ thời gian.
- EC-42 — ✅ CONFIRMED: Phụ huynh giải thích trong giai đoạn đọc.
- EC-43 — ✅ CONFIRMED: Ứng dụng chậm, tạm dừng, đổi tab.
- EC-44 — ✅ CONFIRMED: Đọc chậm hoặc thao tác chậm nhưng hiểu tốt.
- EC-45 — ✅ CONFIRMED: Năng lực Tiếng Việt bị lạm dụng để chặn tiến trình Toán.

**Tài liệu chi tiết:** [09 — Session Correction, Question Incidents & Response Time](./09-session-correction-question-incidents-and-response-time.md). Tổng số edge case đã ghi: **45**; 53 câu hỏi quyết định trong nhóm B ban đầu không bao gồm các câu hỏi mới ở file 09.


## H. Biên bản chốt tổng thể — 2026-11-23

**Owner confirmation:** “Tôi hoàn toàn đồng ý với các đề xuất/khuyến nghị ... 08-consolidated-review.md ... Các EC còn lại cũng theo ông đề xuất. Đánh dấu CONFIRM luôn.”

- ✅ **53/53 khuyến nghị** thuộc `PF-01…06, AL-01…11, AI-01…14, PA-01…12, GM-01…10` được xác nhận **CONFIRMED** ở cấp nguyên tắc/thiết kế.
- ✅ **45/45 edge cases** `EC-01…45` được xác nhận **CONFIRMED** cho **hướng xử lý được khuyến nghị**, bao gồm các EC-31…45 nêu trong tài liệu 09.
- ✅ **10 ý tưởng ở mục D:** đồng ý **tiếp tục khám phá như định hướng**, không tự động biến thành scope MVP.
- ✅ [09 — session corrections & incidents](./09-session-correction-question-incidents-and-response-time.md): các nguyên tắc được chấp thuận.
- **Chưa xác định trong lần duyệt này:** thuật toán cụ thể, ngưỡng mastery/incident/quarantine, thời gian hết hạn chính xác, nội dung giáo án được thẩm định, thông số vận hành và mốc phát triển. Những thứ này là **implementation details / validation tasks**, không nên lẫn với các quyết định sản phẩm đã chốt.
- Những file ý tưởng được viết *trước khi chốt* vẫn có thể nhắc tới `PROPOSED` theo lịch sử; **mục H và Decision Log mới nhất có hiệu lực ưu tiên**.
