# KHUNG DỰ ÁN AI FREE — BỘ SƯỜN SỐNG

*Tài liệu sống duy nhất mô tả sơ đồ hệ thống và luồng hoạt động hiện tại.
Người sáng lập chỉ cần bổ sung ý tưởng — việc "lắp" vào khung là việc của trợ
lý. Quy tắc: **Lời ngỏ** (tầm nhìn, nguyên tắc) là bất biến — đổi phải được
người sáng lập duyệt. **Khung này** là sống — tự điều chỉnh cho khớp kiến thức
mới và báo lại thay đổi.*

*Bản công khai này giữ nguyên kiến trúc và luồng đã thống nhất; changelog dưới
đây đã lược các chi tiết vận hành nội bộ (đường dẫn máy cục bộ, mã triển khai).
Bản đầy đủ lưu trong workspace làm việc.*

---

## 1. Sơ đồ 6 thành phần

```
                    ┌─────────────────────┐
                    │  AI FREE ASSISTANT  │  ← mặt tiền duy nhất user thấy
                    │  (hiểu tiếng Việt)  │
                    └─────────┬───────────┘
                              │ mọi yêu cầu
                    ┌─────────▼───────────┐
                    │   NGƯỜI GÁC CỔNG    │  ← phân loại rủi ro A1–A4 (ROUTER)
                    │ (duyệt / chặn / ghi │     A3 hỏi OK/HỦY, A4 cấm
                    │  nhật ký kiểm toán) │
                    └─────────┬───────────┘
                              │ việc đã duyệt
              ┌───────────────▼────────────────┐
              │       CỖ MÁY TỰ ĐỘNG           │  ← thực thi 24/7
              │ (capability + heartbeat/cron)  │
              └───────────────┬────────────────┘
                              │ kết quả
                    ┌─────────▼───────────┐
                    │  AI FREE ASSISTANT  │  → trả lời user
                    └─────────────────────┘

  ┌────────────┐   nuôi tri thức    ┌──────────────┐
  │ MẸO WIKI   │ ◄──────────────── │ CỖ MÁY / GÁC │
  │ (kho tri   │   field journal   │    CỔNG      │
  │  thức)     │                   └──────────────┘
  └────────────┘
        ▲
        │ hội đồng AI "lọc vàng"
        │ (ủng hộ / phản biện / trọng tài)
  ┌─────┴──────┐
  │  VẬN HÀNH  │  ← brief sáng, giao việc, báo cáo tuần (chạy định kỳ)
  └────────────┘

  ┌──────────────┐
  │  BÁC TÍ AI   │  ← workload đầu tiên cho tiểu thương (dùng chung khung trên)
  └──────────────┘
```

## 2. Công cụ theo thành phần (trạng thái tại thời điểm nguồn)

| Thành phần | Công cụ đang dùng / đánh giá | Trạng thái |
|------------|------------------------------|------------|
| AI Free Assistant | Chưa chốt — ứng viên: NanoBot (Telegram), Paperclip UI. Tóm tắt hội thoại dài kiểu sandwich (quan trọng ở đầu+cuối); system prompt (Lời ngỏ rút gọn) luôn giữ đầu ngữ cảnh | Đang đánh giá |
| Người Gác Cổng | ROUTER (luật) + học pattern Paperclip (approval, audit, budget hard-stop). Áp dụng Luật 3 chống bịa đặt — kiểm chứng theo tầng A1→A4; câu không gắn được nguồn = tín hiệu bịa đặt | Luật xong; implementation học Paperclip |
| Cỗ Máy Tự Động | NanoBot + dsh + Experiential; heartbeat/cron học Paperclip. Pre-compaction flush — trước khi nén ngữ cảnh, trích sự kiện/quyết định ra kho ngoài; xóa kết quả tool cũ thành placeholder | Đang đánh giá |
| Mẹo Wiki | Kho tri thức vận hành nội bộ; mô hình vận hành public sau này: **"Bot học — cộng đồng dạy"** (người dùng góp mẹo → hội đồng AI lọc vàng → nhập kho). Đóng vai **archival memory** (bộ nhớ 3 tầng) — kho ngoài không giới hạn, mỗi mục đánh số = request ID | Đang xây |
| Vận Hành | Chưa chốt (n8n là ứng viên) | Ý tưởng |
| Bác Tí AI | Nguyên tắc UX: **"AI tha thứ theo ngón tay"** — tự sửa lỗi gõ phím mobile, chữ to, tương phản rõ, ít chữ, thao tác đơn giản | Ý tưởng tại thời điểm nguồn |

## 3. Luồng hoạt động chuẩn (mọi việc đều đi qua)

1. User ra lệnh (tiếng Việt) → AI Free Assistant.
2. Người Gác Cổng phân loại A1–A4 → A1/A2 chạy, A3 hỏi OK/HỦY, A4 chặn.
3. Cỗ Máy Tự Động thực thi bằng capability đã đăng ký (kiểm tra rủi ro lại).
4. Kết quả trả về user; nhật ký ghi vào audit; bài học ghi vào Mẹo Wiki.
5. Việc định kỳ (brief, nhắc deal, báo cáo) do Vận Hành kích hoạt qua cron/heartbeat.

## 4. Chuẩn xử lý ngữ cảnh & chống bịa đặt

**5 luật bắt buộc:**
1. Không đủ căn cứ → nói "không chắc" / gắn nhãn `[chưa xác minh]`. Không bịa.
2. Mọi khẳng định về dự án phải gắn được nguồn (mục wiki, ID, hoặc kết quả tool).
3. Việc càng quan trọng, kiểm chứng càng sâu — ánh xạ ROUTER: A1 trả lời thẳng;
   A2 + gắn nguồn; A3 + nhãn `[chưa xác minh]` cho phần không chắc + hỏi OK/HỦY;
   A4 cấm.
4. Việc quan trọng: AI tự tách câu trả lời thành ý nhỏ, đối chiếu từng ý với
   nguồn trước khi chốt.
5. Nếu không kiểm chứng được (hết quota, quá tải ngữ cảnh) → nói thẳng, không
   im lặng làm như đã kiểm chứng.

**Quản trị ngữ cảnh dài** (5 bước): tóm tắt có cấu trúc 4 mục
(việc/trạng thái/quyết định/bước tiếp theo) + xóa kết quả tool cũ thành
placeholder trước → gắn ID mọi khẳng định → lưu 3 tầng (core: Khung + Lời ngỏ,
luôn mang theo / archival: Mẹo Wiki + bộ nhớ dài hạn, kho ngoài / recall: lịch
sử chat, tìm khi cần) → truyền đạt kiểu sandwich (thông tin quan trọng đặt ở
đầu VÀ cuối) → tham chiếu bằng ID, mỗi lần 3–5 mục liên quan nhất.

**Checklist no-code** (người dùng tự bắt lỗi AI bịa): hỏi "thông tin này lấy từ
đâu?" → phải chỉ được nguồn cụ thể; AI quá tự tin về thứ nó không thể biết
= đèn đỏ; bắt AI tự đọc lại và chỉ chỗ không chắc; đối chiếu với Khung /
Lời ngỏ / Mẹo Wiki — mâu thuẫn thì tin tài liệu.

## 5. Changelog khung (lược)

| Phiên bản | Ngày | Thay đổi |
|-----------|------|----------|
| v1.0 | 2026-09-27 | Khởi tạo từ Lời ngỏ v1.0 + pattern Paperclip. Trạng thái ban đầu của 6 thành phần. |
| v1.0.1 | 2026-09-27 | Áp dụng checklist anti-slop cho mọi web UI của dự án. |
| v1.0.2 | 2026-09-27 | Khởi tạo Capability Registry: 5 skill đầu chuẩn hóa theo motip Agent Skills. |
| v1.0.3 | 2026-09-27 | Ban hành khung hình thành & phê duyệt skill (8 mục chung, khối phê duyệt, checklist 10 điểm). |
| v1.0.4 | 2026-09-27 | Quy trình xử lý skill trùng lặp (ma trận 8 tiêu chí, 3 kết cục loại/tích hợp/thay thế). |
| v1.0.5–v1.0.6 | 2026-09-27 | Nhập kho thêm 4 skill (GUI agent, Mẹo Wiki, MobileRun, anti-slop-frontend). Registry: 9 skill. |
| v1.0.7 | 2026-09-27 | Nhập 7 mục tri thức mới vào Mẹo Wiki từ tài liệu của người sáng lập. |
| v1.0.8–v1.0.9 | 2026-09-27 | Hấp thu phác thảo NLP gốc: sơ đồ "Bot học — Cộng đồng dạy", sửa lỗi gõ phím, vòng học cộng đồng; nâng skill DevOps lên v1.1. |
| v1.0.10 | 2026-09-27 | Triết lý "càng dùng càng rẻ" thành nguyên tắc chung: tầng miễn phí trước, API trả phí làm fallback. |
| v1.0.11–v1.0.12 | 2026-09-28 | Ban hành và phê duyệt chuẩn xử lý ngữ cảnh + chống bịa đặt (mục 4); ROUTER lên v2.2. |
| v1.0.13–v1.0.15 | 2026-09-28 → 2026-10-04 | Quy ước "context pack": 5 pack tra cứu nhanh (Skill, Ưu đãi, Mẹo Wiki, Kiến trúc & Luật, Quyết định); Mẹo Wiki thêm mục phòng thủ tráo dữ liệu phía trình duyệt. |
| v1.0.16 | 2026-10-04 | Cập nhật UX dichvuso.store (nút pill "Nhắn tư vấn", popup 3 cam kết, lời chào theo giờ). Mã nguồn tham khảo chỉ lấy nguyên tắc UX chung. |
| v1.0.17 | 2026-10-04 | Thêm hướng dịch vụ "Xây app bằng AI theo yêu cầu" cho Dịch Vụ Số (bảng giá mở bán, mốc đơn đầu ~02/11). |
| v1.0.18 | 2026-10-05 | Mẹo Wiki thêm phân tích phòng thủ thẻ jailbreak "JIRNYAK" (mẫu vật cách ly). Bài học: mặt trận đầu tiên là tầng chỉ thị; ROUTER A4 là lớp khóa. |

---
*Cập nhật bởi trợ lý. Người sáng lập không cần đụng vào file này — chỉ cần
paste ý tưởng, trợ lý sẽ "lắp" vào đúng chỗ và báo lại.*
