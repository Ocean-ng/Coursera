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
# Aircrack-ng Suite

Aircrack-ng không chỉ là bộ công cụ kiểm tra bảo mật Wi-Fi mà còn là công cụ OSINT mạnh mẽ — giúp thu thập thông tin từ các nguồn công khai như mạng Wi-Fi để tìm hiểu về chúng.

Trong OSINT, Aircrack-ng được dùng để:

- Xác định các điểm yếu trong mạng và nhận diện các mạng có nguy cơ bị tấn công cao
- Quan sát cách mạng hoạt động — ví dụ thời điểm mạng hoạt động mạnh nhất hoặc phát hiện tín hiệu bất thường
- Lập bản đồ mạng Wi-Fi trong một khu vực — hữu ích cho việc hiểu mật độ phân bố mạng trong một thành phố hoặc khu dân cư
- Thu thập dữ liệu thực tế phục vụ nghiên cứu bảo mật

---

## Các Công Cụ Trong Bộ Aircrack-ng

| Công cụ | Chức năng |
|---|---|
| **airmon-ng** | Bật chế độ monitor trên card Wi-Fi để bắt đầu thu thập lưu lượng mạng |
| **airodump-ng** | Thu thập lưu lượng mạng, tìm kiếm các mạng Wi-Fi và gói dữ liệu |
| **airgraph-ng** | Tạo biểu đồ trực quan từ lưu lượng mạng thu thập được |
| **aireplay-ng** | Tạo lưu lượng mạng và thực hiện các tấn công như deauthentication và packet injection |
| **aircrack-ng** | Công cụ chính — bẻ khóa mã hóa WEP và WPA/WPA2 để đánh giá bảo mật mạng |
| **airbase-ng** | Tạo Access Point (AP) giả cho tấn công Man-in-the-Middle (MitM) hoặc social engineering |

Ngoài ra còn có `airdecap-ng`, `airdecloak-ng` và `airtun-ng` nhưng không được đề cập trong phần này.

> Lưu ý: **Aircrack-ng (suite)** và **aircrack-ng (tool)** là hai thứ khác nhau. Kali Linux tích hợp sẵn bộ suite này.

Nếu cần cài đặt:

```bash
sudo apt install aircrack-ng -y
```

---

## Airmon-ng

Airmon-ng hoạt động như một công tắc chuyển card Wi-Fi của bạn sang **chế độ monitor (monitor mode)**. Ở chế độ bình thường (managed mode), card Wi-Fi chỉ nhận các gói tin có địa chỉ MAC của chính nó. Ở chế độ monitor, card sẽ nhận tất cả các gói tin trong phạm vi, kể cả những gói không gửi đến thiết bị của bạn.

### Các bước bật monitor mode:

**1. Kiểm tra tên interface:**

```bash
ip a
```

hoặc:

```bash
iwconfig
```

Ghi lại tên interface (thường là `wlan0`).

**2. Kiểm tra các tiến trình có thể gây xung đột:**

```bash
airmon-ng check
```

**3. Tắt các tiến trình gây xung đột:**

```bash
airmon-ng check kill
```

**4. Bật chế độ monitor:**

```bash
airmon-ng start wlan0
```

**5. Xác nhận interface đã chuyển sang monitor mode:**

```bash
iwconfig
```

Sau khi bật, tên interface sẽ thay đổi từ `wlan0` thành `wlan0mon`.

### Các lệnh bổ sung:

```bash
# Tắt monitor mode
airmon-ng stop wlan0mon

# Bật monitor mode trên channel cụ thể
airmon-ng start wlan0 --channel 6
```

---

## Airodump-ng

Airodump-ng được dùng để thu thập thông tin về các mạng Wi-Fi xung quanh. Công cụ này có thể:

- Thu thập dữ liệu Wi-Fi: lắng nghe và bắt toàn bộ lưu lượng mạng trong phạm vi, không chỉ lưu lượng gửi đến thiết bị của bạn
- Hiển thị chi tiết mạng: danh sách các mạng Wi-Fi tìm được kèm thông tin về cường độ tín hiệu, channel đang dùng, và loại bảo mật đang áp dụng
- Theo dõi thiết bị: nhận diện các thiết bị (điện thoại, laptop) đang kết nối vào từng mạng

Chạy airodump-ng sau khi đã bật monitor mode:

```bash
airodump-ng wlan0mon
```

### Thu hẹp phạm vi bắt gói:

```bash
airodump-ng --channel 6 --bssid AA:BB:CC:DD:EE:FF -w output_file wlan0mon
```

Giải thích các flag:

- `--channel` : Chỉ lắng nghe trên channel cụ thể
- `--bssid` : Lọc theo BSSID (địa chỉ MAC của AP mục tiêu)
- `-w` : Chỉ định tiền tố file đầu ra để lưu kết quả
- `--encrypt` : Lọc theo loại mã hóa (ví dụ: WPA, WEP)
- `--showack` : Hiển thị thống kê ACK của client để xác định lỗ hổng injection

## Aireplay-ng

Aireplay-ng thực hiện các tấn công **deauthentication** — phá vỡ kết nối không dây giữa client và AP bằng cách gửi các gói deauthentication. Kỹ thuật này được dùng để kiểm tra khả năng chịu đựng của mạng trước các cuộc tấn công DoS và để bắt WPA/WPA2 handshake.

Để dùng aireplay-ng, cần cung cấp:

- Loại tấn công (ví dụ: `--deauth`)
- Mạng mục tiêu qua switch `-a` kèm BSSID của AP
- Interface đang ở monitor mode (ví dụ: `wlan0mon`)
- MAC address của AP và/hoặc client mục tiêu

Ví dụ lệnh deauthentication — gửi 10 gói deauth đến một client cụ thể:

```bash
aireplay-ng --deauth 10 -a AA:BB:CC:DD:EE:FF -c 11:22:33:44:55:66 wlan0mon
```

Để deauth tất cả client trên AP (broadcast):

```bash
aireplay-ng --deauth 10 -a AA:BB:CC:DD:EE:FF wlan0mon
```

Các flag phổ biến:

- `--deauth` : Tấn công deauthentication
- `--fakeauth` : Tấn công fake authentication
- `--arpreplay` : Tấn công ARP request replay
- `-a` : Chỉ định BSSID của AP mục tiêu
- `-c` : Chỉ định MAC address của client mục tiêu

---

## Aircrack-ng (Tool)

Aircrack-ng (tool) được dùng để bẻ khóa mã hóa WEP và WPA/WPA2.

- **WEP** — Giao thức cũ, bảo mật yếu, dễ bị bẻ do các lỗ hổng cố hữu trong thuật toán.
- **WPA/WPA2** — Bảo mật hơn nhưng vẫn có thể bị bẻ, đặc biệt với mật khẩu yếu.

Aircrack-ng dùng hai phương pháp chính để crack WPA/WPA2:

- **Dictionary attack:** Thử các mật khẩu từ một wordlist có sẵn.
- **Brute-force attack:** Thử tất cả tổ hợp ký tự cho đến khi tìm được mật khẩu đúng.

Để crack WPA/WPA2, bắt buộc phải có file `.cap` chứa dữ liệu handshake thu thập được từ airodump-ng. Aircrack-ng phân tích các gói tin trong handshake để giải mã khóa mạng.

Ví dụ lệnh crack WPA/WPA2:

```bash
aircrack-ng -w /usr/share/wordlists/rockyou.txt -b AA:BB:CC:DD:EE:FF capture-01.cap
```

Để crack mạng ẩn (hidden network) cần chỉ định thêm ESSID:

```bash
aircrack-ng -w /usr/share/wordlists/rockyou.txt -e "TenMangMucTieu" -a 2 capture-01.cap
```

Các flag phổ biến:

- `-w` : Chỉ định file wordlist/dictionary
- `-b` : Chỉ định BSSID của AP mục tiêu
- `-e` : Chỉ định ESSID của mạng mục tiêu
- `-a 2` : Chỉ định chế độ tấn công (2 = WPA/WPA2-PSK)

---

## Airbase-ng

Airbase-ng cho phép tạo các **Access Point giả (fake AP)** — dùng trong kiểm tra bảo mật mạng và mô phỏng tấn công Man-in-the-Middle (MitM). Fake AP trông giống như một mạng Wi-Fi hợp lệ, thu hút các thiết bị kết nối vào — từ đó kẻ tấn công có thể nghe lén hoặc can thiệp vào luồng dữ liệu.

Để tạo fake AP cần: ESSID (tên mạng), channel, loại mã hóa (nếu có), và interface đang ở monitor mode.

Ví dụ tạo fake AP có WPA2:

```bash
airbase-ng --essid "FreeWiFi" --channel 6 -z 2 wlan0mon
```

Ví dụ tạo fake AP không mã hóa (open network):

```bash
airbase-ng --essid "FreeWiFi" --channel 6 wlan0mon
```

Các flag phổ biến:

- `-a` : Đặt BSSID cho fake AP
- `--essid` : Đặt tên mạng (ESSID) cho fake AP
- `--channel` : Đặt channel
- `-W 1` : Bật WEP
- `-z 2` : Bật WPA2

---

## Airgraph-ng

Airgraph-ng chuyển đổi dữ liệu mạng phức tạp thu thập được từ airodump-ng thành các biểu đồ trực quan, dễ đọc. Các biểu đồ này hiển thị lưu lượng mạng, thiết bị đang kết nối và các vấn đề bảo mật tiềm ẩn.

Bước đầu tiên là thu thập dữ liệu bằng airodump-ng với output lưu ra file CSV:

```bash
airodump-ng -w output wlan0mon
```

Tạo biểu đồ **CAPR (Client to AP Relationship)** — hiển thị kết nối giữa client và AP:

```bash
airgraph-ng -i output-01.csv -o capr_graph.png -g CAPR
```

Tạo biểu đồ **CPG (Common Probe Graph)** — hiển thị các mạng mà client đã từng kết nối:

```bash
airgraph-ng -i output-01.csv -o cpg_graph.png -g CPG
```

Các flag phổ biến:

- `-i` : File CSV đầu vào từ airodump-ng
- `-o` : File đầu ra cho biểu đồ
- `-g` : Loại biểu đồ (`CAPR` hoặc `CPG`)
- `-c` : Lọc theo channel
- `--essid` : Lọc theo ESSID

Biểu đồ từ Airgraph-ng giúp phát hiện các mẫu bất thường — ví dụ lưu lượng tăng đột biến tại một thời điểm cụ thể, hoặc phát hiện thiết bị lạ đang kết nối vào mạng.
