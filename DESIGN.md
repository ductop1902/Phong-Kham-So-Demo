# DESIGN.md: Nhịp Khám, giao diện nhân viên

File này ghi các quyết định thiết kế để mọi bản sau giữ nhất quán. Sửa giao diện thì đọc file này trước.

## Hai bản đang chạy song song

| Bản | Đường dẫn | Trạng thái |
|---|---|---|
| Bản 19 | `/index.html` | Bản đã khóa (Hướng 1, 05/11/2026). Không sửa trong đợt này. |
| Bản mới | `/ban-moi/index.html` | Bản thử khung Dark Sidebar, 06/11/2026, để so với bản 19. |

Hai bản dùng chung dữ liệu mẫu trong trình duyệt (khóa `phongkhamso-thu-v5`), nên thao tác ở bản này hiện luôn ở bản kia trên cùng máy. Logic, dữ liệu và luồng của bản mới giữ nguyên như bản 19; chỉ đổi cách bày ba màn đã duyệt.

## Thương hiệu (không đổi)

- Tên: Nhịp Khám. Trong app ưu tiên tên phòng khám, chữ Nhịp Khám nhỏ bên dưới, icon chữ N.
- Màu chính tím mận `#5A2D6E`, nền tím nhạt `#F5F0F7`.
- Chữ Be Vietnam Pro. Chỉ giao diện sáng.
- Đỏ chỉ dùng cho cảnh báo (dị ứng, quá giờ, nợ). Vàng chỉ để đánh dấu khách đang có mặt ở phòng khám.
- Sơ đồ răng: SVG tự vẽ bản 4 là bản chính thức, không thay bằng hình trên mạng.

## Bộ mặt bản mới: Dark Sidebar

| Trục | Chọn |
|---|---|
| Khung | Thanh bên tối cố định 244px (từ 1024px), nội dung nền xám ấm `#F4F3F5`, khối nội dung là thẻ trắng |
| Màu thanh bên | `--sb-bg #231A2A` (tím than), chữ `--sb-fg`, mục đang chọn nền sáng hơn, số đếm bên phải |
| Bo góc | 12px cho thẻ lớn, 10px cho thẻ con |
| Viền | 1px `--nm-line`, không đổ bóng |
| Mật độ | Vừa: hàng 44px trở lên, nút nhỏ 32px |
| Dưới 1024px | Không có thanh bên; thanh điều hướng dưới đáy như bản 19 |

## Ba màn đã duyệt (06/11/2026)

1. **Hôm nay của lễ tân, phương án A "Dòng chảy khách".** Bốn cột theo bước của khách: Sắp đến, Đã đến chờ khám, Đang khám, Chờ thu tiền. Mỗi thẻ có một nút cho bước kế tiếp. Từ 821 đến 1180px còn 2 cột; từ 820px trở xuống thành thẻ tab, mỗi lần một cột. Thẻ tiếp nhận QR nằm dưới bảng.
2. **Khám, phương án A.** Sơ đồ răng bên trái, phiếu bên phải chia ba thẻ: Chẩn đoán, Kế hoạch, Đơn thuốc. Thanh "Hoàn tất" (ký và chuyển thu ngân) dính ở đáy phiếu.
3. **Thu ngân, phương án A.** Danh sách bên trái (thẻ Chờ thu, Còn nợ, kèm Phiếu thu hôm nay), phiếu thu mở ngay bên phải, không dùng hộp thoại. Vào màn là tự mở phiếu đầu tiên. Nút Đối soát cuối ngày thay phiếu thu bằng bảng đối soát.

## Chỗ khác với wireframe (có lý do)

- Sơ đồ răng cần khoảng 750px mới đọc rõ, nên Khám chỉ chia hai cột từ 1500px. Dưới 1500px sơ đồ răng ở trên, phiếu ở dưới.
- Hôm nay của lễ tân bỏ khối "Tình trạng ghế"; thay bằng nhãn "Ghế X trống, mời vào" trên thẻ khách đang chờ. Khối "Hẹn tái khám" bỏ khỏi màn này vì đã có ở Chăm sóc khách.
- Thu ngân giữ ô "Hình thức" và "Khách trả lần này" như bản 19 (wireframe vẽ nút chọn và ô khách đưa/trả lại) để không đổi logic thu tiền.
- Chỉ màn Hôm nay của lễ tân đổi bố cục. Hôm nay của bác sĩ, thu ngân, tư vấn và chủ giữ như bản 19, chỉ mặc khung mới.

## Quy tắc khi làm tiếp

- Dùng lại lớp có sẵn (`.btn`, `.tg`, `.panel`, `.sub`, `.acts2`), không tạo lớp trùng.
- Thẻ trong cột hẹp: chữ dài phải xuống dòng, nút co giãn, không tràn khỏi thẻ. Tên bác sĩ không ngắt giữa chừng.
- Ghi chú dài trên thẻ cắt ở 2 dòng, rê chuột xem đủ.
- Vòng focus khi bấm Tab giữ như bản 19 để dùng được bằng bàn phím.
- Kiểm tra ở 375, 1280 và 1440px trước khi giao.
