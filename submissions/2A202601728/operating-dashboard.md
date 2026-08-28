# Operating Dashboard — OmniChat AI

> Đây là **worksheet nguồn** để validator và rubric truy vết evidence. Sau khi
> hoàn tất, rút gọn phần vận hành sang
> `templates/one-page-dashboard-template.md`; không ép bảng 12 cột này lên một trang.

- Học viên: Nguyễn Đức Đạt
- Mã học viên: 2A202601728
- Mô hình: B2B
- Cập nhật: 2026-08-28
- North Star: Median time-to-first-value dưới 3 ngày

## Chẩn đoán mô hình

OmniChat AI là mô hình B2B vì các chủ shop và doanh nghiệp bán lẻ trực tuyến (SME Merchants) trên Pancake POS trả tiền theo số resolution thành công, nhân viên vận hành và chủ shop trực tiếp cấu hình kịch bản và theo dõi bot, đồng thời chúng tôi không có quan hệ thương hiệu độc lập trực tiếp với người mua hàng cuối cùng.

| Dữ liệu đầu vào | Trạng thái | Nằm ở đâu hoặc cần gì để đo | Ngày có số |
|---|---|---|---|
| Unit economics Day 24 | Đo được | File mô hình tài chính Day 24 đã loại dữ liệu cá nhân (ARPU 299k, COGS 80k, GM 73.2%, CAC 450k) | 2026-08-28 |
| Value Metric và Cost/Job Day 25 | Đo được | Báo cáo Cost/Job ($0.2486) và định giá Outcome-based ($0.99 / resolution) trong evidence pack Day 25 | 2026-08-28 |

## Kiểm kê đèn ứng viên

| Đèn ứng viên từ handbook | Tầng | Trạng thái | Bằng chứng hiện có hoặc kế hoạch đo |
|---|---|---|---|
| Time-to-first-value (TTFV) | L | ✅ | Event kickoff và milestone 20 resolution thật đã log tự động trên plugin Pancake POS |
| Pipeline coverage | L | 🔧 | Chuẩn hóa deal stage và số lượng shop đăng ký trial trên CRM đối tác trước 2026-09-15 |
| % deal chết ở khâu security/procurement | L | 🔧 | Thêm tracking lý do từ chối kết nối webhook fanpage trên form hỗ trợ trước 2026-09-15 |
| POC → paid | O | ✅ | Cohort sheet theo dõi 10 shop thiết kế ban đầu chuyển đổi sang gói trả phí |
| Sales cycle (ngày) | O | 🔧 | Trích xuất thời gian từ lúc cài plugin đến lúc nâng cấp gói trả phí trước 2026-09-20 |
| Usage depth trong tài khoản | O | ✅ | Tỷ lệ hội thoại ca đêm (22h30–01h00) được AI xử lý trọn vẹn trong event log |
| Chi phí triển khai ÷ ACV | O | 🔧 | Gắn timesheet hỗ trợ cấu hình catalog sản phẩm với shop ID trước 2026-09-20 |
| Tập trung doanh thu | O | ✅ | Báo cáo doanh thu theo shop export từ cổng thanh toán đã ẩn danh |
| NRR | G | 🔧 | Thu thập đủ dữ liệu 2 quý thanh toán của các cohort vào 2027-02-28 |
| Gross Margin | G | ✅ | Bảng sao kê đối soát doanh thu trừ chi phí token LLM và hạ tầng Cloud |
| CAC payback | G | 🔧 | Báo cáo chi phí kênh Partner-Led chia sẻ doanh thu theo quý trước 2026-10-15 |

## Đèn báo sớm

| ID | Đèn | Định nghĩa và công thức | Nhịp · Owner | Hiện tại | 🟢 | 🟡 | 🔴 | Nguồn | Ngày kiểm tra | Báo trước cho | Luật |
|---|---|---|---|---:|---|---|---|---|---|---|---|
| L-01 | Time-to-first-value | Số ngày từ khi shop cài plugin Pancake đến khi AI hoàn tất 20 resolution thật đạt QA; median theo cohort | Tuần · Product Operations | 2.5 ngày | ≤3 ngày | 4–7 ngày | >7 ngày | [TB] Dùng 2 cohort đầu tiên làm chuẩn tạm thời và chốt baseline sau 4 cohort vào 2026-10-31 | 2026-08-28 | Pilot activation và tỷ lệ gia hạn tháng | R-01 |
| L-02 | Tỷ lệ Containment của AI Agent | Số hội thoại chốt đơn hoặc giải quyết thành công không cần nhân sự can thiệp chia tổng hội thoại AI tiếp nhận | Tuần · AI Engineering | 82% | ≥80% | 73–79% | <73% | [MH] MH-02 suy từ điểm hòa vốn an toàn để Gross Margin không dưới 60% | 2026-08-28 | Chi phí AI mỗi resolution và Gross Margin | R-02 |

## Đèn vận hành

| ID | Đèn | Định nghĩa và công thức | Nhịp · Owner | Hiện tại | 🟢 | 🟡 | 🔴 | Nguồn | Ngày kiểm tra | Báo trước cho | Luật |
|---|---|---|---|---:|---|---|---|---|---|---|---|
| O-01 | Pilot activation rate | Số shop có ít nhất 100 resolution thật trong 30 ngày chia tổng số shop cài plugin Pancake | Tuần · Customer Success | 75% | ≥70% | 50–69% | <50% | [TB] Đo lường trên 3 cohort đầu tiên và chốt baseline chuẩn hóa vào 2026-10-31 | 2026-08-28 | POC-to-paid conversion | R-03 |
| O-02 | Chi phí AI trên mỗi job | Tổng chi phí token LLM, vector database và retry chia cho tổng số resolution hoàn thành | Tuần · FinOps | 5.400 đ | ≤6.000 đ | 6.001–8.000 đ | >8.000 đ | [MH] MH-01 suy từ giá bán 24.000 đ và Gross Margin mục tiêu 70% | 2026-08-28 | Gross Margin sau AI cost | R-04 |
| O-03 | POC-to-paid conversion | Số shop nâng cấp lên gói trả phí chính thức chia tổng số shop kết thúc thời gian trial | Tháng · Growth Lead | 52% | ≥50% | 35–49% | <35% | [BM] Báo cáo ICONIQ State of Go-to-Market 2026 https://www.iconiq.com/growth/reports/state-of-go-to-market-2026 mốc tham khảo chuyển đổi POC B2B ~50% | 2026-08-28 | Doanh thu MRR mới | R-03 |

## Đèn kết quả

| ID | Đèn | Định nghĩa và công thức | Nhịp · Owner | Hiện tại | 🟢 | 🟡 | 🔴 | Nguồn | Ngày kiểm tra | Báo trước cho | Luật |
|---|---|---|---|---:|---|---|---|---|---|---|---|
| G-01 | Gross Margin sau AI cost | Doanh thu resolution trừ toàn bộ chi phí biến đổi COGS chia cho doanh thu resolution | Tháng · Finance | 74.89% | ≥70% | 60–69% | <60% | [MH] MH-01 bảo đảm biên lợi nhuận gộp dày trên 70% bù đắp chi phí R&D và vận hành | 2026-08-28 | Runway và LTV/CAC | R-04 |
| G-02 | Net Revenue Retention | Doanh thu từ cohort khách hàng cuối kỳ chia doanh thu đầu kỳ sau khi tính expansion và churn | Quý · Finance | 108% | ≥110% | 100–109% | <100% | [BM] Benchmarkit SaaS Performance Report FY2024 https://www.benchmarkit.ai/reports/saas-benchmarks-2024 trung vị NRR toàn ngành đạt 101% | 2026-08-28 | LTV và khả năng mở rộng doanh thu tự nhiên | R-05 |

## Luật quyết định

| ID | NẾU | TRONG | VÀ | THÌ | KHÔNG THÌ | Luật dừng? |
|---|---|---|---|---|---|---|
| R-01 | Median TTFV > 7 ngày | 2 cohort liên tiếp | Mỗi cohort có ít nhất 10 shop | Dừng kích hoạt plugin cho shop mới trong 14 ngày và tinh gọn kịch bản mẫu còn đúng một luồng chốt đơn trực tiếp | Không giảm giá cước để bù cho việc khách chậm thấy giá trị | CÓ |
| R-02 | Tỷ lệ Containment < 73% | 2 tuần liên tiếp | Có ít nhất 1.000 hội thoại phát sinh | Đóng băng mở rộng tính năng mới và điều chuyển 2 kỹ sư AI sang gán nhãn 200 ca hội thoại thất bại để cập nhật Few-shot Prompting | Không đổ thêm tiền marketing để bù đắp số lượng hội thoại hỏng | CÓ |
| R-03 | Pilot activation rate < 50% | 2 cohort liên tiếp | Có ít nhất 15 shop tham gia trial | Thiết lập quy trình 1-on-1 onboarding trực tiếp với chủ shop và cắt bỏ các bước cấu hình API phức tạp | Không tăng số lượng shop dùng thử để che giấu tỷ lệ kích hoạt thấp | KHÔNG |
| R-04 | Chi phí AI trên mỗi job > 8.000 đ | 2 tuần liên tiếp | Có ít nhất 2.000 resolution thành công | Bật chế độ Semantic Prompt Caching, hạ tier model sang Claude 3.5 Haiku / Gemini Flash cho các tác vụ hỏi đáp thông thường và giới hạn context window dưới 2.000 token | Không tắt bước kiểm duyệt QA để làm giảm chi phí nhân tạo | KHÔNG |
| R-05 | NRR < 100% | 2 quý liên tiếp | Cohort có ít nhất 20 shop hoạt động | Chuyển 80% nguồn lực phát triển sang giải quyết 3 nguyên nhân rời bỏ hàng đầu được xác thực qua phỏng vấn khách hàng | Không cộng doanh thu từ shop mới vào công thức tính NRR của cohort cũ | KHÔNG |

## Cổng gác 90 ngày

| Ngày | Metric gác cổng | Ngưỡng | Bằng chứng vật lý | Nếu đạt | Nếu trượt |
|---:|---|---|---|---|---|
| 30 | Phỏng vấn chuyên sâu 10 Design Partners xác nhận Pain Moment ca đêm | 8/10 chủ shop xác nhận AI chốt đơn ban đêm hiệu quả và hài lòng với chất lượng | Biên bản phỏng vấn và video ghi lại phiên trải nghiệm đã ẩn danh | GO | FIX |
| 60 | Pilot activation rate và Tỷ lệ Containment thực tế | Activation rate ≥ 70% và Containment ≥ 75% trên ít nhất 30 shop thử nghiệm | Báo cáo trích xuất log webhook đơn hàng và database phiên hội thoại | GO | PIVOT |
| 90 | Gross Margin sau AI cost và Doanh thu trả phí | Gross Margin ≥ 70% trên tối thiểu 5.000 resolution thành công | Sao kê đối soát doanh thu cổng thanh toán và hóa đơn token LLM | GO | KILL |

## Kill criteria

KILL và dừng hoàn toàn dự án vào ngày 90 nếu Gross Margin sau AI cost vẫn dưới 60% sau 2 chu kỳ tối ưu prompt caching và tỷ lệ chuyển đổi POC-to-paid đạt dưới 25% trên 30 shop thử nghiệm.

## Chưa đo được

| Đèn hoặc giả định | Cần gì để đo | Ai chịu trách nhiệm | Ngày có số |
|---|---|---|---|
| Tỷ lệ chủ shop sẵn sàng chia sẻ 20% doanh thu đơn hàng cho tính năng chốt sale tự động | Form khảo sát tích hợp vào giao diện Pancake POS sau khi hoàn tất 50 đơn hàng đầu tiên | Product Operations | 2026-09-15 |

## Phụ lục ngưỡng suy từ mô hình

| ID | Metric | Input Day 24–25 | Phép tính | Kết quả và ngưỡng áp dụng |
|---|---|---|---|---|
| MH-01 | Chi phí AI tối đa trên mỗi resolution | Giá bán đề xuất 24.000 đ/resolution; Gross Margin mục tiêu 70%; Chi phí hạ tầng và Vector DB 1.200 đ/resolution | 24.000 × (1 − 70%) − 1.200 = 6.000 | Xanh khi Chi phí AI ≤ 6.000 đ/resolution; Vàng 6.001–8.000 đ; Đỏ khi > 8.000 đ áp dụng cho đèn O-02 và G-01 |
| MH-02 | Tỷ lệ Containment tối thiểu của AI Agent | Giá bán 24.000 đ ($0.99); Biến phí LLM v = 650 đ ($0.02687); Chi phí QA q = 360 đ ($0.015); Chi phí 1 ca escalation e = 21.600 đ ($0.90); Ngưỡng trần Cost/Job để đạt GM 60% là 9.600 đ ($0.396) | (650 + 360 + 21.600 × (1 − R)) ÷ (24.000 × R) = 0.40 ⟺ 22.610 ÷ 31.200 = 0.7247 | Xanh khi Containment ≥ 80%; Vàng 73–79%; Đỏ khi < 73% vì chạm ngưỡng hòa vốn kinh tế áp dụng cho đèn L-02 |

## Ghi nhận AI critique

| Phản biện | Chấp nhận hay bác bỏ | Thay đổi đã thực hiện | Lý do |
|---|---|---|---|
| Định nghĩa Time-to-first-value cần cụ thể hóa mốc hoàn tất thay vì chỉ tính thời gian cài đặt | Chấp nhận | Quy định rõ mốc 20 resolution thật đạt chuẩn QA kiểm duyệt | Giúp dữ liệu đo lường nhất quán giữa 2 người đo khác nhau |
| Nên lấy benchmark NRR 101% của SaaS truyền thống làm ngưỡng đỏ | Bác bỏ | Đặt ngưỡng đỏ NRR < 100% và xanh ≥ 110% bám sát đặc thù AI Agent chốt đơn có hệ số expansion theo mùa mua sắm | Sản phẩm giải quyết bài toán cốt lõi trực tiếp tạo doanh thu nên kỳ vọng expansion cao hơn SaaS tiện ích thông thường |
| Chi phí AI mỗi job nên tính theo số hội thoại tiếp nhận thay vì số job hoàn thành | Bác bỏ | Giữ nguyên công thức chia cho số resolution hoàn tất thành công (Biến thể B Day 25) | Đảm bảo phản ánh chính xác kinh tế học của mô hình Outcome-based pricing |
