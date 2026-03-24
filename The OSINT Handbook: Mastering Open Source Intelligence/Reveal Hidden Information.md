

## Phân Tích Tên Miền và Địa Chỉ IP

### Giao Thức WHOIS

WHOIS là cơ chế giúp tra cứu thông tin đăng ký tên miền.

**Cách thức WHOIS hoạt động:**

1. **Gửi lệnh:** Bạn kích hoạt lệnh WHOIS. Yêu cầu của bạn sẽ được định tuyến đến máy chủ WHOIS quản lý Tên miền cấp cao nhất (TLD) tương ứng (như `.com`, `.org`, `.vn`).
2. **Xử lý:** Máy chủ WHOIS tìm kiếm trong cơ sở dữ liệu của nó các thông tin liên quan đến tên miền hoặc IP bạn yêu cầu.
3. **Trả kết quả:** Máy chủ tổng hợp một bản ghi dưới dạng văn bản thuần túy (plain text) và gửi về màn hình của bạn.

**Bản ghi WHOIS thường chứa các thông tin sau:**

- **Registrant (Người đăng ký):** Tên, địa chỉ, email và số điện thoại của chủ sở hữu tên miền.
- **Registrar (Nhà đăng ký):** Tên công ty cung cấp dịch vụ bán tên miền đó.
- **Name servers (Máy chủ phân giải tên miền):** Hệ thống máy chủ quản lý bản ghi DNS của tên miền.
- **Ngày tháng:** Ngày tên miền được tạo và ngày hết hạn.
- **Trạng thái:** Tên miền đang hoạt động, bị treo, hay đang chờ chuyển nhượng.

Ví dụ chạy lệnh WHOIS trên Terminal (Kali Linux / macOS):

```bash
whois daledumbsitdown.com
```

### Áp Dụng Cho Cả Các Khối IP

WHOIS không chỉ dành cho tên miền. Mọi thiết bị và máy chủ trên mạng đều có một địa chỉ IP duy nhất. Các tổ chức lớn thường sở hữu cả một "khối" (block) các địa chỉ IP liên tiếp nhau.

Khi bạn dùng lệnh WHOIS lên một địa chỉ IP — ví dụ `8.8.8.8` của Google — nó sẽ trả về thông tin về toàn bộ khối IP đó (ví dụ dải mạng CIDR `8.8.8.0/24`), tổ chức nào đang quản lý và khu vực địa lý được phân bổ.

### Các Nền Tảng Tra Cứu WHOIS Trực Tuyến

Ngoài việc dùng dòng lệnh, bạn có thể sử dụng các nền tảng trực tuyến:

- **[DomainTools](https://www.domaintools.com/):** Cung cấp công cụ tra cứu cực kỳ chi tiết, lấy dữ liệu từ cơ sở dữ liệu WHOIS có thẩm quyền cho từng TLD. Lưu ý: đây là dịch vụ trả phí (khoảng $99/tháng cho gói cá nhân), tra cứu đơn lẻ miễn phí.

- **[Whois.com](https://www.whois.com/):** Giao diện gọn gàng, cung cấp thông tin đăng ký cốt lõi miễn phí.

### Bài Toán Quyền Riêng Tư và Lịch Sử WHOIS

Hiện nay, nhiều chủ sở hữu trang web trả tiền cho các dịch vụ bảo mật thông tin (Privacy/Proxy services). Khi đó, thông tin trên WHOIS sẽ hiển thị tên của công ty bảo mật thay vì tên thật của chủ web.

**Khai thác lịch sử WHOIS:**

Nếu một người ẩn danh thông tin của họ ở hiện tại, thì trong quá khứ lúc mới lập web, rất có thể họ đã quên làm điều đó. Công cụ [WHOXY](https://www.whoxy.com/) cho phép tra cứu lịch sử đăng ký của một tên miền

------

- **Bắt đầu với tên miền chính:** Truy vấn cơ sở dữ liệu WHOIS cho tên miền mục tiêu để lấy thông tin sở hữu và đăng ký.

```bash
whois example.com
```

- **Tìm kiếm Name Servers:** Trong kết quả trả về, chú ý đến các mục Name Server (ví dụ: `ns1.example.com`, `ns2.example.com`). Đây là các máy chủ chịu trách nhiệm lưu trữ bản ghi DNS của tên miền.

- **Điều tra sâu vào Name Servers:** Thực hiện truy vấn WHOIS cho chính các name server vừa tìm được.

```bash
whois ns1.example.com
```

Kỹ thuật này giúp phát hiện ra các tên miền khác đang sử dụng chung một hệ thống name server, từ đó xác định cụm hạ tầng liên quan.

- **Tìm kiếm sự trùng lặp (Common Registrants):** Đối chiếu kết quả WHOIS để tìm các tổ chức hoặc cá nhân đăng ký chung. Nếu cùng một email hoặc thông tin liên hệ xuất hiện trên nhiều tên miền, đó là bằng chứng rõ ràng về mối liên hệ sở hữu.

- **Mở rộng ra Subdomains:** Tiếp tục áp dụng phương pháp trên cho các tên miền phụ để mở rộng bề mặt tấn công (attack surface).

```bash
whois sub.example.com
```

---

## Góc Khuất: Khi Tin Tặc Lợi Dụng WHOIS

Dữ liệu WHOIS không chỉ dành cho những nhà điều tra phòng thủ. Tin tặc thường xuyên khai thác nguồn dữ liệu này để phục vụ các mục đích độc hại:

- **Tấn công Phishing có chủ đích (Spear Phishing):** Thu thập được email và tên thật của người đăng ký tên miền là mồi nhử hoàn hảo. Một email chứa tên người thật, việc thật luôn dễ lừa nạn nhân click hơn.

- **Chiếm đoạt tên miền hết hạn (Domain Sniping):** Kẻ tấn công liên tục theo dõi các tên miền sắp hết hạn. Ngay khi chủ sở hữu quên gia hạn, chúng sẽ đăng ký lại để phát tán mã độc hoặc chuyển hướng lưu lượng truy cập hợp pháp sang các trang lừa đảo.

- **Tấn công Kỹ thuật xã hội (Social Engineering):** Sử dụng các thông tin liên hệ trên WHOIS để giả danh, lừa các nhà cung cấp dịch vụ chuyển nhượng quyền sở hữu tên miền bất hợp pháp.

- **DDoS và DNS Hijacking:** WHOIS phơi bày cấu trúc Name Server. Với thông tin này, tin tặc có thể tấn công từ chối dịch vụ (DDoS) vào máy chủ phân giải, hoặc làm giả bản ghi DNS để định tuyến sai toàn bộ lưu lượng truy cập của một tổ chức.

Để che giấu hành tung, những kẻ tấn công thường sử dụng máy chủ proxy và liên tục cào dữ liệu từ máy chủ WHOIS để tìm kiếm lỗ hổng.

---

## Phân Tích DNS và IP: Lập Bản Đồ Hạ Tầng

Các kỹ thuật OSINT cho phép tận dụng dữ liệu DNS và IP để làm sáng tỏ các kết nối ẩn giữa tên miền và hạ tầng vật lý.

Tra cứu DNS trên Linux để hiển thị địa chỉ IP được liên kết:

```bash
dig hackthissite.org
```

Sau khi có IP, thực hiện tra cứu DNS ngược (Reverse DNS lookup) để tìm các tên máy chủ (hostnames) trỏ về địa chỉ IP đó:

```bash
dig -x 137.74.187.102
```

> Lưu ý: Nếu một IP đang cung cấp dịch vụ Shared Hosting (lưu trữ chia sẻ), lệnh này có thể trả về hàng chục, thậm chí hàng trăm tên miền đang nằm chung trên một máy chủ vật lý.

Trên Windows, công cụ tương đương là `nslookup`:

```dos
nslookup hackthissite.org
```

---

## Khai Thác Sâu Hơn Với Các Bản Ghi DNS

Bản ghi DNS cung cấp vô số thông tin tình báo. Bằng cách truy vấn các loại bản ghi khác nhau, nhà phân tích có thể lập bản đồ toàn bộ tài sản internet của một tổ chức. Trong các bài tập thực chiến hay thử thách CTF, việc liệt kê (enumeration) DNS thường làm lộ ra các cấu hình sai (misconfigurations) — bước đệm hoàn hảo để thâm nhập hệ thống.

### Bản Ghi A và AAAA

Bản ghi A ánh xạ một tên miền sang địa chỉ IPv4, trong khi bản ghi AAAA ánh xạ sang địa chỉ IPv6. Tìm ra bản ghi này giúp xác định chính xác địa chỉ IP đang lưu trữ trang web.

```bash
nslookup
> set type=A
> example.com
```

### Bản Ghi MX (Mail Exchange)

Bản ghi MX chỉ định các máy chủ email chịu trách nhiệm nhận thư cho một tên miền. Việc liệt kê bản ghi MX làm lộ ra cơ sở hạ tầng email cốt lõi — thường là mục tiêu béo bở cho các chiến dịch phishing. Máy chủ MX có số thứ tự ưu tiên (preference) càng nhỏ thì mức độ ưu tiên càng cao.

```bash
nslookup
> set type=MX
> daledumbsitdown.com
```

### Bản Ghi TXT (Text Records)

Bản ghi TXT cho phép quản trị viên chèn các văn bản tự do. Trong bảo mật, nó cực kỳ quan trọng vì thường được dùng để chứa cấu hình SPF (Sender Policy Framework). SPF liệt kê danh sách các máy chủ được phép gửi email thay mặt cho tên miền đó. Thu thập dữ liệu SPF giúp hiểu rõ hệ thống nào — như Google Workspace, Office 365, hay máy chủ tự lưu trữ — đang được tổ chức cấp quyền nội bộ.

```bash
nslookup
> set type=TXT
> example.com
```

### Bản Ghi CNAME (Canonical Name)

Bản ghi CNAME tạo ra một bí danh (alias), trỏ tên miền này sang một tên miền thực (đích) khác. Phân tích CNAME thường làm lộ ra các nhà cung cấp dịch vụ lưu trữ đám mây (upstream providers) hoặc các nền tảng của bên thứ ba như CDN, dịch vụ marketing mà mục tiêu đang sử dụng.

---


# Traceroute

Traceroute là một công cụ chẩn đoán mạng dùng để lập bản đồ đường đi của gói tin từ máy nguồn đến máy đích trên mạng IP. Công cụ này hoạt động bằng cách gửi các gói UDP hoặc ICMP với giá trị TTL (Time To Live) tăng dần và ghi lại địa chỉ nguồn của các gói phản hồi.

---

## Cơ Chế Hoạt Động

Khi một gói traceroute được gửi đi, router đầu tiên sẽ giảm giá trị TTL xuống 1 và chuyển tiếp đến router kế tiếp. Khi TTL về 0, router nhận được gói đó sẽ hủy gói và gửi lại một thông báo **ICMP Time Exceeded** về máy nguồn.

Nhờ cơ chế này, traceroute có thể xác định từng hop trên đường đi thông qua địa chỉ IP nguồn của gói ICMP nhận được. Quá trình bắt đầu với TTL nhỏ và tăng dần cho đến khi đến đích.

**Ví dụ minh họa:** Traceroute từ Host A đến Host B:

1. Host A gửi gói UDP với TTL = 1 đến Host B.
2. Router đầu tiên (R1) nhận gói, giảm TTL xuống 0, hủy gói và gửi ICMP Time Exceeded về A. R1 được xác định.
3. Host A gửi gói mới với TTL = 2. R1 giảm xuống 1 và chuyển tiếp đến R2. R2 giảm xuống 0, hủy gói và gửi ICMP về A. R2 được xác định.
4. Quá trình tiếp tục tăng TTL cho đến khi đến đích là Host B.

Trong suốt quá trình đó, traceroute ghi lại địa chỉ IP và độ trễ (latency) của mỗi hop, từ đó lập được bản đồ đường đi và hiệu năng mạng giữa nguồn và đích.

## Lý Do Xuất Hiện Dấu `*`

- **Firewall chặn:** Router có tường lửa chặn gói ICMP TTL Expired hoặc gói UDP/TCP của traceroute, không cho phản hồi.
- **Rate limiting:** Một số router giới hạn số lượng gói traceroute sẽ phản hồi. Khi đạt giới hạn, chúng ngừng trả lời.
- **Mất gói (Packet loss):** Tắc nghẽn mạng hoặc mất gói khiến gói traceroute không đến được hop đó.
- **Địa chỉ không hợp lệ:** IP của router bị cấu hình sai hoặc không thể truy cập.
- **Router bị down:** Router đang ngoại tuyến hoặc không khả dụng.

----  


## Wireshark
Wireshark là một công cụ phân tích gói tin (packet analyzer) mã nguồn mở, cho phép kiểm tra sâu lưu lượng mạng, các luồng giao tiếp và giao thức. Công cụ này hoạt động như một kính hiển vi mạng, cho phép người dùng bắt các gói tin đi qua giao diện có dây, không dây và ảo.

## Website Reconnaissance

Kali Linux cung cấp một bộ công cụ phong phú cho phân tích và thu thập thông tin từ website. Các kỹ thuật cốt lõi bao gồm: scraping website, phân tích metadata với Metagoofil, xem lịch sử website với Wayback Machine, và dò tìm các thư mục và file ẩn.

### Web Page Scraping

Web scraping là kỹ thuật tự động trích xuất và thu thập dữ liệu từ các website. Nó cho phép thu thập quy mô lớn các nội dung văn bản, hình ảnh, tài liệu và dữ liệu có cấu trúc từ khắp nơi trên internet. Dữ liệu thô sau đó có thể được phân tích để tìm ra các thông tin ẩn, theo dõi thay đổi theo thời gian, hoặc xây dựng bộ dữ liệu cho các ứng dụng khác.

### Metagoofil

Metagoofil là công cụ tìm kiếm Google để xác định và tải về các tài liệu công khai (pdf, doc, xls, ppt, docx, pptx, xlsx) thuộc về một tên miền mục tiêu.

**Cú pháp và ví dụ thực tế:**

```bash
metagoofil -d packtpub.com -t doc,pdf -l 20 -n 10 -o scans -f results.html
```

Giải thích các flag:

- `-d packtpub.com` : Tên miền mục tiêu
- `-t doc,pdf` : Loại file cần tìm
- `-l 20` : Giới hạn 20 kết quả tìm kiếm
- `-n 10` : Giới hạn tải về tối đa 10 file
- `-o scans` : Thư mục lưu file tải về
- `-f results.html` : Lưu danh sách link kết quả vào file HTML

Sau khi chạy, mở file `results.html` trong thư mục output để xem danh sách tài liệu tìm được. Để xem metadata, chạy thêm `exiftool` trên các file đã tải về.

**Xử lý HTTP 429 — Google chặn IP:**

Khi Google phát hiện lưu lượng tự động, nó sẽ trả về lỗi HTTP 429 và chặn IP của bạn. Giải pháp là dùng proxychains để xoay vòng qua nhiều proxy.

Cài đặt proxychains:

```bash
sudo apt install proxychains4 -y
```

Cấu hình file `/etc/proxychains4.conf`, bật chế độ round_robin để xoay vòng qua các proxy ngẫu nhiên:

```
round_robin_chain
proxy_dns

[ProxyList]
socks4 192.168.0.1 8000
socks4 192.168.0.2 8001
socks4 192.168.0.3 8002
```

Chạy Metagoofil qua proxychains:

```bash
proxychains4 metagoofil -d example.com -t pdf,doc -l 100 -o output -f results.html
```

Càng nhiều proxy trong danh sách, thời gian scraping không bị gián đoạn càng dài. Luôn tôn trọng điều khoản sử dụng của trang web, giới hạn dữ liệu và file `robots.txt`.

### Phân Tích Với grep

Sau khi có dữ liệu, dùng `grep` để lọc và tìm kiếm thông tin theo từ khóa hoặc pattern cụ thể:

```bash
grep -ri "pattern" /path/to/downloaded/website/data
```

Giải thích:

- `grep` : Công cụ dòng lệnh tìm kiếm pattern trong file (viết tắt của Global Regular Expression Print)
- `-r` : Tìm kiếm đệ quy trong thư mục và tất cả thư mục con
- `-i` : Tìm kiếm không phân biệt chữ hoa/thường
- `"pattern"` : Pattern văn bản cần tìm — thay bằng từ khóa thực tế
- `/path/to/downloaded/website/data` : Thư mục bắt đầu tìm kiếm

---

## Wayback Machine và Web Archives

[Wayback Machine](https://web.archive.org/) cho phép khám phá lịch sử của các website qua thời gian. Nó lưu trữ các bản snapshot định kỳ của các trang web, cung cấp quyền truy cập vào các phiên bản cũ của trang và nội dung có thể đã bị xóa khỏi web hiện tại.

- **Truy cập nội dung đã bị xóa hoặc thay đổi:** Wayback Machine lưu trữ các phiên bản trang không còn tồn tại. Bạn có thể scrape nội dung đã bị gỡ khỏi các website.
- **Phân tích thay đổi website:** So sánh các phiên bản khác nhau của code và cấu trúc trang theo thời gian để xác định các thay đổi.
- **Nghiên cứu tên miền:** Xem lịch sử sở hữu, các trang liên quan đến email hoặc tên cụ thể, và các tên miền tiền thân.
- **Khám phá các trang ẩn hoặc bị lãng quên:** Kho lưu trữ chứa các trang đã biến mất khỏi web hiện tại.
- **Xây dựng dataset:** Trích xuất dữ liệu từ các nguồn hiện tại và lịch sử với số lượng lớn.



