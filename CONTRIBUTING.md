# Đóng góp cho AI Free

## Ngôn ngữ và thước đo

- Mọi nội dung mặc định bằng tiếng Việt.
- Mọi đề xuất phải trả lời được: "người không biết code có dùng được không?"
  Nếu không, đề xuất đó sai hướng.

## Những gì được thay đổi — và bởi ai

- **Lời ngỏ (`docs/loi-ngo.md`) là bất biến.** Mọi thay đổi phải được người sáng
  lập duyệt và ghi changelog.
- **Khung (`docs/khung.md`) là tài liệu sống.** Cập nhật cho khớp kiến thức mới,
  ghi changelog, báo lại thay đổi bằng một dòng.
- **ROUTER (`docs/router.md`) không được tự sửa.** Mọi thay đổi phải do người
  sáng lập duyệt tay và ghi changelog ở đầu file.
- Mọi việc liên quan tiền phải được người sáng lập duyệt trước.

## Quy tắc nội dung

- Không commit secret (password, API key, token, mã 2FA) hay dữ liệu cá nhân,
  tài chính, thông tin tài khoản nội bộ vào repo này. Xem `.gitignore`.
- Không đưa nội dung vi phạm ranh giới đạo đức của dự án: spam, multi-account
  né khóa, vượt captcha/bảo mật, nội dung lừa dối.
- Khẳng định về dự án phải gắn được nguồn (mục tài liệu, ID, hoặc kết quả kiểm
  chứng). Không gắn được nguồn thì gắn nhãn `[chưa xác minh]` hoặc nói rõ
  "không chắc" — không bịa đặt.
- Chi phí tiệm cận 0 cho tier miễn phí là ràng buộc thiết kế, không phải khẩu
  hiệu. Đề xuất mới phải trả lời "tầng miễn phí nào xử lý được trước khi gọi
  API trả phí?"

## Quy trình

1. Mở issue mô tả đề xuất bằng tiếng Việt, kèm lý do và nguồn đối chiếu.
2. Thảo luận và thống nhất trong issue hoặc khung chat làm việc.
3. Khi đã thống nhất, cập nhật cả hai nơi theo
   [docs/dong-bo.md](docs/dong-bo.md): khung chat làm việc và repo này.
4. Pull request nhỏ, một chủ đề, ghi rõ thay đổi trong changelog khi cần.
