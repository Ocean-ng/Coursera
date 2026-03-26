
## Tìm Mạng Wi-Fi Ẩn

Một mạng Wi-Fi ẩn (hidden network) không phát sóng SSID công khai, nhưng điều đó không có nghĩa là nó vô hình. Bất kỳ thiết bị nào đang kết nối với mạng ẩn đó đều liên tục gửi probe request để duy trì kết nối — và các probe request này chứa SSID thật.

### Quy trình phát hiện mạng ẩn:

**1. Bật monitor mode:**

```bash
airmon-ng start wlan0
```

**2. Bắt đầu quét tất cả mạng trong phạm vi:**

```bash
airodump-ng wlan0mon
```

Trong danh sách hiện ra, các mạng ẩn sẽ hiển thị SSID là `<length: x>` thay vì tên thật.

**3. Ép thiết bị đang kết nối gửi probe request bằng cách ngắt kết nối tạm thời:**

```bash
aireplay-ng -0 30 -a [BSSID_của_AP] -c [MAC_của_client] wlan0mon
```

Flag `-0` gửi tín hiệu deauthentication, `30` là số gói tin gửi đi.

**4. Chuyển lại airodump-ng** — SSID ẩn sẽ xuất hiện trong kết quả khi client gửi probe request để kết nối lại.

> Lưu ý bảo mật: Việc ẩn SSID không cung cấp bảo mật thực sự. Luôn kết hợp với mã hóa mạnh (WPA3 hoặc WPA2), mật khẩu phức tạp và các biện pháp bảo vệ khác.

Ẩn SSID cũng là điểm khởi đầu cho tấn công **Evil Twin** — kẻ tấn công deauth client khỏi mạng thật, dựng fake AP cùng tên, client kết nối nhầm vào fake AP và toàn bộ dữ liệu bị intercepted (tấn công MitM).

---

## SpiderFoot

[SpiderFoot](https://github.com/smicallef/spiderfoot) là công cụ tự động hóa OSINT tích hợp hơn 200 module, thu thập và tổng hợp thông tin về một mục tiêu cụ thể — có thể là địa chỉ IP, tên miền, email hoặc username.

### Cài đặt:

Trên Kali Linux (đã tích hợp sẵn):

```bash
sudo apt install spiderfoot -y
```

Hoặc cài từ GitHub:

```bash
git clone https://github.com/smicallef/spiderfoot.git
cd spiderfoot
pip3 install -r requirements.txt --break-system-packages
```

### Khởi động SpiderFoot:

```bash
spiderfoot -l 127.0.0.1:5001
```

Sau đó mở trình duyệt và truy cập:

```
http://127.0.0.1:5001
```

### Sử dụng qua giao diện web:

1. Click tab **New Scan**
2. Nhập thông tin mục tiêu (ví dụ: `hackthissite.org`)
3. Chọn loại scan: **Footprint**, **Investigate** hoặc **Passive**
4. Click **Run Scan Now** và chờ kết quả

SpiderFoot sẽ trả về một lượng lớn thông tin: tên miền phụ, địa chỉ IP, email, thông tin DNS, dữ liệu WHOIS và nhiều hơn nữa.

### Sử dụng qua command line:

```bash
spiderfoot -s hackthissite.org -u footprint -o csv
```

Có thể zoom vào từng cột trong kết quả để xem thêm chi tiết về từng loại dữ liệu thu thập được.

---

## Twint

> **Cảnh báo quan trọng:** Twint (Twitter Intelligence Tool) đã **ngừng hoạt động**. Repository chính thức trên GitHub đã bị archive ngày 30/3/2023 (read-only) và không còn được phát triển. Công cụ này không còn hoạt động được do Twitter/X thay đổi cấu trúc API vào năm 2023.
>
> Các thông tin bên dưới được ghi lại để hiểu về khái niệm và lịch sử của công cụ. Nếu cần scraping X/Twitter, hiện tại có thể cân nhắc các thay thế như [twint-zero](https://github.com/twintproject/twint-zero) (đang phát triển) hoặc các wrapper API chính thức của X.

### Giới thiệu (lịch sử)

Twint là công cụ scraping Twitter nâng cao viết bằng Python, cho phép trích xuất tweets từ các profile Twitter mà **không cần sử dụng Twitter API**. Điểm mạnh so với API chính thức:

- Không bị giới hạn rate limit
- Không cần xác thực
- Có thể lấy toàn bộ tweet của một tài khoản (API chính thức giới hạn 3.200 tweet gần nhất)

### Các lệnh cơ bản (tham khảo):

```bash
# Cài đặt (không còn hoạt động với X hiện tại)
git clone --depth=1 https://github.com/twintproject/twint.git
cd twint
pip3 install . -r requirements.txt --break-system-packages

# Lấy tất cả tweet của một user
twint -u username

# Tìm tweet chứa từ khóa trong timeline của user
twint -u username -s batman

# Tìm kiếm toàn bộ Twitter theo từ khóa
twint -s batman

# Lấy thông tin profile
twint -u username --user-info

# Lấy danh sách followers
twint -u username --followers

# Lấy danh sách following
twint -u username --following

# Lấy thông tin đầy đủ của người dùng đang follow
twint -u username --followers --user-full
twint -u username --following --user-full

# Lưu kết quả ra file
twint -u username -o file.txt
twint -u username -o file.csv --csv
twint -u username -o file.json --json

# Lưu vào SQLite
twint -u username --database tweets.db
```
