# Vở Ô Li Lớp 5

Ứng dụng học, luyện tập và kiểm tra **Toán – Tiếng Việt lớp 5**, bám theo sách *Kết nối tri thức với cuộc sống* (chương trình GDPT 2018).

- **Học tập:** tóm tắt kiến thức, công thức phải nhớ, lỗi hay gặp, cách suy nghĩ, ví dụ mẫu, hình minh họa và hình có thanh trượt để con tự thao tác.
- **Luyện tập:** 3 cấp độ (Chuẩn SGK · Mở rộng tư duy · Nâng cao HSG). Câu hỏi được tự sinh nên luyện không hết đề, mỗi câu có lời giải và sơ đồ.
- **Kiểm tra:** đề theo học kì hoặc cả năm, có đồng hồ đếm ngược, chấm thang điểm 10.
- **Góc phụ huynh:** tỉ lệ đúng theo từng chủ đề và cấp độ, biểu đồ điểm, lịch sử bài làm kèm câu sai, nhận xét định hướng.

Ứng dụng chỉ gồm HTML, CSS, JavaScript thuần: không cần cài đặt, không cần máy chủ, không có quảng cáo.

## Cấu trúc thư mục

```
index.html                    Trang chính
favicon.svg                   Biểu tượng
.nojekyll                     Để GitHub Pages phục vụ file nguyên trạng
css/style.css                 Giao diện (tự đổi theo chế độ sáng/tối)
js/toan-chu-de.js             Lý thuyết + bộ sinh bài 10 chủ đề Toán
js/toan-bo-sung.js            Dạng bài bổ sung + chủ đề "Các dạng toán điển hình"
js/tieng-viet-chu-de.js       Lý thuyết + ngân hàng câu hỏi Tiếng Việt, bài đọc hiểu
js/tieng-viet-bo-sinh.js      Bộ sinh câu hỏi Tiếng Việt + chủ đề Từ loại, Vốn từ, Chính tả
js/hinh-ve.js                 Thư viện vẽ hình, sơ đồ lời giải
js/hinh-bai-giang.js          Hình minh họa bài giảng, hình tương tác
js/app.js                     Giao diện, chấm điểm, lưu kết quả
```

Các file JS phải nạp đúng thứ tự như trong `index.html`.

## Đưa lên GitHub Pages

1. Tạo repository mới trên GitHub, ví dụ `vo-o-li-lop5` (chọn **Public**; tài khoản miễn phí chỉ bật Pages được cho repo public).
2. Tải toàn bộ file trong thư mục này lên repo (**Add file → Upload files**, kéo cả thư mục `css`, `js` và các file lẻ vào), rồi bấm **Commit changes**.
   - Lưu ý tải cả file `.nojekyll`. Nếu trình duyệt ẩn file bắt đầu bằng dấu chấm thì có thể bỏ qua, ứng dụng vẫn chạy.
3. Vào **Settings → Pages**. Ở mục *Build and deployment*, chọn **Source: Deploy from a branch**, **Branch: main**, thư mục **/ (root)**, bấm **Save**.
4. Chờ 1–2 phút, trang sẽ có địa chỉ dạng `https://<tên-tài-khoản>.github.io/vo-o-li-lop5/`.

Muốn cập nhật nội dung: sửa file trong repo rồi commit, GitHub Pages tự cập nhật sau ít phút (có thể cần tải lại trang bằng Ctrl + F5).

## Chạy thử trên máy

Mở thẳng `index.html` bằng trình duyệt là chạy được. Hoặc chạy máy chủ tĩnh:

```bash
python -m http.server 8000
# rồi mở http://localhost:8000
```

## Lưu kết quả học

- Kết quả được lưu trong **trình duyệt của máy đang dùng** (localStorage), không gửi đi đâu.
- Mỗi máy, mỗi trình duyệt có dữ liệu riêng. Nếu xoá dữ liệu trình duyệt hoặc dùng chế độ ẩn danh, kết quả sẽ mất.
- Vì vậy, trong **Góc phụ huynh → Cài đặt** có nút **Tải file sao lưu** (file `.json`) và **Khôi phục từ file sao lưu**. Nên sao lưu định kỳ, và dùng file này để chuyển kết quả sang máy khác (khôi phục sẽ gộp, không xoá kết quả đang có).

## Sửa hoặc thêm nội dung

- **Câu hỏi Tiếng Việt cố định:** thêm vào mảng `q` của chủ đề trong `js/tieng-viet-chu-de.js` theo dạng
  `[cấp, 'câu hỏi', ['đáp án đúng', 'nhiễu 1', 'nhiễu 2', 'nhiễu 3'], 'lời giải']`. Đáp án đúng luôn đặt đầu tiên, ứng dụng tự xáo trộn.
- **Dữ liệu sinh câu Tiếng Việt** (nhóm từ đồng nghĩa, câu ghép, cặp kết từ, chính tả…): các mảng ở đầu mỗi phần trong `js/tieng-viet-bo-sinh.js`.
- **Bài đọc hiểu mới:** thêm vào `PASSAGES` rồi thêm câu hỏi có mã bài đọc ở cuối, ví dụ `[1,'câu hỏi',[...],'lời giải','mabaidoc']`.
- **Dạng toán mới:** thêm một hàm sinh vào `gen[cấp]` của chủ đề (xem các ví dụ trong `js/toan-bo-sung.js`).
