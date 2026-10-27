# AI Free — Trợ lý cá nhân miễn phí cho người Việt

> **Sản phẩm miễn phí, chất xám tính phí.**

AI Free là trợ lý cá nhân cho người Việt: nghe hiểu tiếng Việt, làm việc tự động
24/7, phổ cập tri thức số đến tầng lớp lao động phổ thông, và tự nuôi sống chính
nó. Người dùng chỉ cần nhắn tin bằng câu nói đời thường — mọi công đoạn phía sau
là của hệ thống. Không cần biết code, không cần thẻ, chi phí tiệm cận 0.

Thước đo duy nhất của mọi thiết kế trong dự án này:

> *"Người không biết code như tôi có dùng được không?" — nếu câu trả lời là không,
> thiết kế đó sai.*

## 4 trụ cột

1. **Hiểu câu lệnh ngôn ngữ tự nhiên** — ra lệnh bằng chat tiếng Việt như nhắn
   tin cho người quen.
2. **Thực thi quy trình tự động hóa** — tra cứu, theo dõi, nhắc việc, xử lý công
   việc lặp lại thay người dùng, 24/7.
3. **Phổ cập tri thức số đến tầng lớp lao động phổ thông** — tiểu thương, lao
   động tự do, học sinh, những người đang bị bỏ lại phía sau.
4. **Tự vận hành kiếm tiền để duy trì dự án** — không phụ thuộc tài trợ hay ví
   của người sáng lập.

## 6 thành phần

| # | Thành phần | Vai trò |
|---|-----------|---------|
| 1 | AI Free Assistant | Mặt tiền duy nhất user thấy: hiểu tiếng Việt, điều phối |
| 2 | Người Gác Cổng | Phân loại rủi ro A1–A4, phê duyệt, nhật ký kiểm toán, kill switch |
| 3 | Cỗ Máy Tự Động | Thực thi automation 24/7 bằng capability đã đăng ký |
| 4 | Mẹo Wiki | Kho tri thức: SOP, thủ thuật AI, bài học thực chiến |
| 5 | Vận Hành | Việc hằng ngày: brief sáng, giao việc, báo cáo tuần |
| 6 | Bác Tí AI | Sản phẩm cho tiểu thương — mũi nhọn trụ cột 3 |

Mọi yêu cầu đều đi qua Người Gác Cổng rồi mới đến Cỗ Máy Tự Động. Tên kỹ thuật
bên trong giữ ở tầng implementation; người dùng phổ thông chỉ thấy 6 tên trên.

## Mô hình freemium

- **AI Free** — thương hiệu cộng đồng: nội dung và công cụ miễn phí.
- **Dịch Vụ Số (dichvuso.store)** — cánh tay thương mại: setup, tư vấn, gói duy
  trì. Miễn phí cho người dùng phổ thông, người đóng góp cộng đồng và mục đích
  học tập/phi lợi nhuận; tính phí cho setup riêng, workflow đặt làm theo yêu cầu,
  gói duy trì và đào tạo.

## Tài liệu

- [Lời ngỏ](docs/loi-ngo.md) — tầm nhìn, mục đích, 7 nguyên tắc bất di bất dịch.
  Tài liệu gốc bất biến; mọi thay đổi phải được người sáng lập duyệt.
- [Khung dự án](docs/khung.md) — sơ đồ hệ thống, luồng hoạt động chuẩn, chuẩn
  chống bịa đặt và quản trị ngữ cảnh. Tài liệu sống, cập nhật kèm changelog.
- [ROUTER](docs/router.md) — bộ định tuyến hành động A1–A4: phân loại trước mọi
  hành động, phê duyệt OK/HỦY cho A3, cấm A4.
- [Đồng bộ 2 nơi](docs/dong-bo.md) — quy tắc cập nhật song song giữa chat làm
  việc và repo này.

## Trạng thái

Phiên bản công khai đầu tiên (v0.1.0) là repo tài liệu: hiến chương, kiến trúc
và luật vận hành đã thống nhất. Sản phẩm đang chạy: bot Bác Tí AI trên
Cloudflare Workers và gian hàng Dịch Vụ Số tại
[dichvuso.store](https://dichvuso.store). Code sản phẩm và kho skill sẽ được
công khai theo từng bước riêng, sau khi rà soát.

## Đóng góp

Xem [CONTRIBUTING.md](CONTRIBUTING.md). Nguyên tắc chung: tiếng Việt mặc định,
chi phí tiệm cận 0 cho tier miễn phí, không secret trong repo, mọi việc liên
quan tiền phải được người sáng lập duyệt trước.

## Giấy phép

[MIT](LICENSE).
