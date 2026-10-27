# LỜI NGỎ DỰ ÁN AI FREE — 2026-09-27

*Gửi bạn — người lao động đang tò mò về AI nhưng chưa biết bắt đầu từ đâu,
không biết viết code, và không muốn tốn nhiều tiền. Lời ngỏ này cũng là tài liệu
gốc của toàn dự án: tầm nhìn, mục đích, động lực phát triển và lý do tồn tại.
Mọi tài liệu kỹ thuật khác đều đối chiếu vào đây. Đã thống nhất ngày 2026-09-27.*

*Bản công khai này giữ nguyên nội dung thỏa thuận; các tham chiếu vận hành nội
bộ đã được chuyển thành tham chiếu chung (xem [Đồng bộ 2 nơi](dong-bo.md)).*

---

## 1. Tầm nhìn — chúng ta xây dựng gì

**AI Free**: một trợ lý cá nhân cho người Việt, gồm 4 trụ cột:

1. **Hiểu câu lệnh ngôn ngữ tự nhiên** — nghe hiểu tiếng Việt, ra lệnh bằng chat
   như nhắn tin cho người quen. Không cần biết code.
2. **Thực thi quy trình tự động hóa** — làm việc 24/7 thay người dùng: tra cứu,
   theo dõi, nhắc việc, xử lý công việc lặp lại.
3. **Phổ cập tri thức số đến tầng lớp lao động phổ thông** — đưa tiện ích AI đến
   những người đang bị bỏ lại phía sau: tiểu thương, lao động tự do, học sinh.
4. **Tự vận hành kiếm tiền để duy trì dự án** — dự án tự nuôi sống chính nó,
   không phụ thuộc tài trợ hay ví của người sáng lập.

## 2. Mục đích — phục vụ ai

Chân dung người dùng duy nhất mà mọi quyết định phải phục vụ:

- **Mới tiếp xúc với AI**, không rành công nghệ.
- **Không biết viết code** — mọi tương tác bằng ngôn ngữ tự nhiên.
- **Nhạy cảm về chi phí** — không có lý do bỏ ra khoản tiền lớn cho AI.
- **Cần tiếng Việt** — rào cản ngôn ngữ là rào cản thật.

Người sáng lập chính là người dùng đầu tiên và là thước đo:
*"người không biết code như tôi có dùng được không?"* — nếu câu trả lời là không,
thiết kế đó sai.

## 3. Động lực phát triển — vì sao dự án ra đời

Dự án bắt đầu từ nhu cầu thật của một người dùng thật: cần tiện ích AI mang lại
nhưng không đủ lý do chi nhiều tiền → tự tìm hiểu, tự xây trợ lý cho mình.

Hành trình 110 file phác thảo là quá trình tìm hướng: từ kiến trúc no-code, hệ
quản trị, kho tri thức, đến các thử nghiệm kiếm tiền. Những gì không phù hợp đã
bị loại bỏ hoặc cách ly; những gì còn lại hội tụ thành hiến chương này.

Triết lý **0 đồng** không phải chiêu marketing — nó là điều kiện sinh tồn:
người dùng mục tiêu không trả tiền cho AI, nên dự án buộc phải chạy được ở chi
phí tiệm cận 0 (API miễn phí, hạ tầng miễn phí, model local).

## 4. Động cơ tồn tại — vì sao dự án xứng đáng tồn tại

1. **Khoảng trống thật:** AI đang phục vụ người rành công nghệ và doanh nghiệp.
   Tầng lớp lao động phổ thông — đông nhất — gần như đứng ngoài cuộc.
2. **Sứ mệnh thật:** phổ cập tri thức số không phải khẩu hiệu; Mẹo Wiki và
   Bác Tí AI là công cụ cụ thể đưa AI đến tay tiểu thương, người lao động.
3. **Mô hình thật:** freemium "sản phẩm miễn phí, chất xám tính phí" — cộng đồng
   dùng free, dịch vụ chuyên sâu nuôi dự án. Không đốt tiền, không phụ thuộc.
4. **Con người thật:** dự án do người dùng thật xây cho người dùng thật, không
   phải phòng lab vẽ ra.

## 5. Thương hiệu & mô hình freemium

### 5.1. Hai thương hiệu

| Thương hiệu | Vai trò | Slogan |
|-------------|---------|--------|
| **AI Free** — *"AI miễn phí cho người Việt"* | Thương hiệu cộng đồng: xin ưu đãi hệ sinh thái, nội dung & công cụ miễn phí | Phổ cập tri thức số |
| **Dịch Vụ Số (dichvuso.store)** | Cánh tay thương mại: dịch vụ setup, tư vấn, gói duy trì | *"Sản phẩm miễn phí, chất xám tính phí"* |

### 5.2. Ai được miễn phí

1. **Người dùng phổ thông** (lao động, tiểu thương, học sinh): trợ lý chat cơ bản
   + toàn bộ Mẹo Wiki. Không cần biết code, không cần thẻ.
2. **Người đóng góp cộng đồng** (viết mẹo, kiểm chứng, dịch): quyền dùng rộng hơn
   + ghi nhận tên tuổi.
3. **Mục đích học tập / phi lợi nhuận**: trường học, nhóm cộng đồng.

### 5.3. Tính phí cái gì

- Setup riêng cho shop / doanh nghiệp nhỏ.
- Workflow đặt làm theo yêu cầu.
- Gói duy trì + hỗ trợ ưu tiên.
- Đào tạo, hướng dẫn sử dụng.

### 5.4. Giữ tier miễn phí không lỗ

Model free-tier + quota/ngày + cache câu hỏi phổ biến (trả lời 1 lần, ngàn người
dùng lại). Mọi yêu cầu — miễn phí hay trả phí — đều chạy qua Người Gác Cổng.

## 6. Kiến trúc tổng thể — 6 thành phần, tên gọi thống nhất

| # | Tên thống nhất | Tên cũ trong tài liệu | Chức năng |
|---|----------------|----------------------|-----------|
| 1 | **AI Free Assistant** | (trợ lý tổng) | Giao diện duy nhất người dùng thấy: hiểu tiếng Việt, điều phối |
| 2 | **Người Gác Cổng** | Nexus ACP / ROUTER | Phân loại rủi ro A1–A4, phê duyệt, nhật ký kiểm toán, kill switch |
| 3 | **Cỗ Máy Tự Động** | Nexus AgentOS/Core, NanoBot, dsh | Thực thi automation 24/7; AI viết capability, AI khác nạp và chạy |
| 4 | **Mẹo Wiki** | Mẹo Wiki | Kho tri thức: SOP, thủ thuật AI, bài học thực chiến; hội đồng AI "lọc vàng" trước khi nhập kho |
| 5 | **Vận Hành** | Nexus Ops (n8n...) | Việc hằng ngày: brief sáng, giao việc, báo cáo tuần |
| 6 | **Bác Tí AI** | Bác Tí AI | Sản phẩm cho tiểu thương — mũi nhọn trụ cột 3 |

Quy tắc: tên kỹ thuật bên trong giữ ở tầng implementation; người dùng phổ thông
chỉ thấy 6 tên trên. Các tên "Nexus*" nghỉ hưu, chỉ giữ trong tài liệu lịch sử.

## 7. Nguyên tắc bất di bất dịch

1. **Người dùng không biết code** là thước đo mọi thiết kế.
2. **Tiếng Việt** là ngôn ngữ mặc định của mọi giao diện.
3. **Chi phí tiệm cận 0** cho tier miễn phí — không bao giờ phá vỡ.
4. **Người Gác Cổng** phê duyệt mọi hành động A3 trở lên; không có ngoại lệ.
5. **Trụ cột 4 tuân thủ cùng đạo đức với 3 trụ cột còn lại** — không spam,
   không multi-account né khóa, không vượt captcha/bảo mật, không nội dung lừa dối.
   Tài liệu vi phạm xem danh mục cách ly, không dùng để triển khai.
6. **Không lưu secret** (password, API key, token, 2FA) trong chat hay file thường.
7. Mọi việc liên quan tiền đều phải được người sáng lập duyệt trước.

## 8. Tài liệu liên quan

- [Khung dự án](khung.md) — bộ sườn sống của hệ thống.
- [ROUTER](router.md) — bộ định tuyến hành động A1–A4.
- Kho ưu đãi phục vụ dự án, danh mục cách ly đạo đức AI và lời tri ân các nguồn
  mở: tài liệu vận hành nội bộ, chưa công khai trong repo này.

---
*Lời ngỏ v1.0 — thống nhất ngày 2026-09-27. Mọi thay đổi phải được người sáng
lập duyệt và ghi changelog.*
