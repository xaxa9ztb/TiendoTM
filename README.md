# Lift Schedule Builder — Bảng tiến độ thi công thang máy

Ứng dụng web **tĩnh 100%** (chỉ 1 file `index.html`) — chạy hoàn toàn trên trình duyệt, không cần server, phù hợp GitHub Pages. Dữ liệu hợp đồng KHÔNG được gửi đi bất cứ đâu.

## Tính năng

| Bước | Chức năng |
|---|---|
| 1. Nhập liệu | Kéo thả **file scan hợp đồng (PDF/ảnh)** → tự OCR tiếng Việt (Tesseract.js) và trích xuất: tên dự án, số hợp đồng, Bên Mua/Bên Bán, thiết bị, thời gian các giai đoạn, cách tính ngày, điều kiện thi công. Nhập **ngày ký phê duyệt bản vẽ**, chọn **ngày làm việc / ngày lịch**, khai báo ngày nghỉ lễ, chọn **thành phần ký** (nhà thầu, TVGS, Ban QLDA, CĐT, tổng thầu — thêm/bớt tự do). |
| 2. Kiểm tra | Toàn bộ dữ liệu OCR hiển thị lại để người dùng **xác nhận và sửa tay** (trường nhận diện tự động có nhãn ●OCR). Bảng 14 bước lắp đặt thêm/bớt/sửa được, tổng tự cộng. |
| 3. Xuất | **Preview** bảng tiến độ đúng mẫu A3 ngang (Gantt theo tuần, chú giải, ghi chú điều kiện, khối chữ ký) → xuất **Excel (.xlsx)** đã cài sẵn in A3 ngang 1 trang, hoặc **PDF** qua nút In (Ctrl+P, khổ A3 landscape). |

## Đưa lên GitHub Pages (5 phút)

1. Tạo repository mới trên GitHub (ví dụ `lift-schedule`).
2. Upload 2 file `index.html` và `README.md` vào nhánh `main`
   (kéo thả trực tiếp trên web GitHub: **Add file → Upload files**).
3. Vào **Settings → Pages** → Source: chọn `Deploy from a branch`,
   Branch: `main` / thư mục `/ (root)` → **Save**.
4. Chờ ~1 phút, ứng dụng chạy tại:
   `https://<tên-user>.github.io/lift-schedule/`

> Không cần build, không cần Node.js — GitHub Pages phục vụ thẳng file HTML.

## Thư viện (tải qua CDN, khai báo trong `index.html`)

- [PDF.js 3.11](https://mozilla.github.io/pdf.js/) — đọc PDF, ưu tiên lớp text nếu có, nếu là bản scan thì render trang ra canvas.
- [Tesseract.js 5](https://tesseract.projectnaptha.com/) — OCR tiếng Việt (`vie`), model tải tự động lần chạy đầu (~15 MB, cache lại).
- [ExcelJS 4.4](https://github.com/exceljs/exceljs) — sinh file .xlsx có định dạng đầy đủ (merge, màu, khổ in A3 ngang fit 1 trang).
- [FileSaver.js](https://github.com/eligrey/FileSaver.js) — tải file về máy.

## Lưu ý sử dụng

- OCR bản scan chất lượng thấp có thể nhận sai — bước 2 luôn cho phép sửa tay mọi trường.
- Ngày nghỉ lễ nhập dạng `yyyy-mm-dd`, phân cách dấu phẩy (mặc định 01–02/09/2026).
- Xuất PDF: trình duyệt sẽ mở hộp thoại in — chọn khổ **A3**, hướng **Ngang (Landscape)**, đích **Save as PDF**.
- Trình duyệt khuyến nghị: Chrome/Edge bản mới.
