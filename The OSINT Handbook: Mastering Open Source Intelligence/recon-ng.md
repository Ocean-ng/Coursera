# Recon-ng: Thu Thập Thông Tin Với Hệ Thống Module

Recon-ng là một framework kết hợp nhiều công cụ và kỹ thuật, tổ chức chúng thành một hệ thống module có cấu trúc. Mỗi module — từ phân tích tên miền đến scraping mạng xã hội — được thiết kế để cung cấp thông tin cụ thể về mục tiêu.

---

## Workspaces (Không Gian Làm Việc)

Sau khi cài đặt Recon-ng, điều đầu tiên cần nắm là **workspaces**. Đây là tính năng thiết yếu của framework.

Tạo một workspace mới:

```bash
workspaces create [tên_workspace]
```

Ví dụ:

```bash
workspaces create my_investigation
```

Workspace trong Recon-ng hoạt động như một thư mục dự án riêng biệt. Lý do cần dùng workspace:

- **Cô lập dự án:** Mỗi workspace là một container độc lập cho dữ liệu của một dự án. Khi làm nhiều điều tra song song, mỗi điều tra có workspace riêng với dữ liệu, module và cấu hình tách biệt — không có nguy cơ ô nhiễm chéo giữa các dự án.
- **Duy trì sự tập trung:** Phân tách dữ liệu vào các workspace giúp bạn tập trung vào nhiệm vụ hiện tại mà không bị phân tâm bởi dữ liệu không liên quan.
- **Toàn vẹn dữ liệu:** Dữ liệu của dự án cũ không bị ảnh hưởng bởi các hoạt động của dự án mới.
- **Báo cáo hiệu quả:** Khi cần tổng hợp kết quả, toàn bộ dữ liệu liên quan đã nằm gọn trong một workspace — không cần lọc qua thông tin không liên quan.
- **Linh hoạt cộng tác:** Workspace có thể chia sẻ giữa các thành viên trong nhóm, cho phép làm việc song song trên các dự án khác nhau mà không ảnh hưởng đến dữ liệu của nhau.

---

## Modules và API Keys

Recon-ng có marketplace tích hợp với nhiều module trinh sát khác nhau

Thêm API key (ví dụ Shodan):

```bash
keys add shodan_api [your_api_key]
```

---

## Quy Trình Sử Dụng Module

### 1. Tìm kiếm module trên marketplace

```bash
marketplace search [từ_khóa]
```

Ví dụ:

```bash
marketplace search hackertarget
```

### 2. Xem các module hiện có

```bash
modules search
```

Lệnh này hiển thị các danh mục và module — bao gồm module theo tên miền, theo vị trí địa lý, và nhiều loại khác, mỗi loại phục vụ một mục đích riêng.

### 3. Cài đặt và tải module

Tải và cài đặt module từ marketplace:

```bash
marketplace install recon/domains-hosts/hackertarget
```

Sau đó tải module vào phiên làm việc:

```bash
modules load recon/domains-hosts/hackertarget
```

### 4. Xem và cấu hình các tùy chọn

Xem các tùy chọn hiện có của module:

```bash
options list
```

Mỗi module có các tùy chọn riêng cần cấu hình — thông thường là tên miền hoặc địa chỉ IP mục tiêu. Ví dụ:

```bash
options set SOURCE packtpub.com
```

### 5. Chạy module

Khi đã cấu hình xong, chạy module:

```bash
run
```

Module sẽ thực hiện thu thập thông tin theo thiết kế của nó.

### 6. Xem kết quả

Sau khi module hoàn thành, xem kết quả đã lưu:

```bash
show hosts
```

Kết quả trả về thường là danh sách gồm row ID, hostname và địa chỉ IP liên quan đến mục tiêu.

Để xem toàn bộ dữ liệu đã thu thập theo từng loại:

```bash
show contacts
show ports
show vulnerabilities
```
