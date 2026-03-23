# Khai thác Mạng xã hội trong OSINT (SOCMINT)

Tình báo Mạng xã hội (SOCMINT - Social Media Intelligence) có thể được xem là một nhánh chuyên sâu của OSINT, tập trung vào việc khai quật thông tin từ thế giới nền tảng mạng xã hội nhộn nhịp. Trong khi OSINT truyền thống thường hài lòng với các dữ liệu tĩnh có sẵn trên web công cộng, SOCMINT tiến sâu hơn một bước, tiếp cận vào các luồng thông tin thường xuyên biến động và đôi khi nằm trong các vòng kết nối mang tính khép kín hơn.

Các nền tảng này cung cấp lượng dữ liệu khổng lồ có thể được phân tích cho nhiều mục đích bảo mật khác nhau. Dưới đây là cách các nhà phân tích biến các nền tảng phổ biến thành nguồn thông tin tình báo:

## Khai thác các Nền tảng Mạng xã hội Phổ biến

* **[X (trước đây là Twitter)](https://twitter.com)**
  * **Trạm phát sóng tin tức:** Đây là điểm nóng cho mọi tin tức và sự kiện nóng hổi. Các nhà phân tích thường xuyên theo dõi nền tảng này để nắm bắt thông tin theo thời gian thực (real-time).
  * **Tìm kiếm có chọn lọc:** Nền tảng này sở hữu bộ lọc tìm kiếm cực mạnh, cho phép người phân tích rà soát các bài đăng (tweet) và trích xuất chính xác thông tin họ cần.
  * **Tích hợp API:** Khả năng kết nối API của X là một công cụ tiết kiệm thời gian tuyệt vời, hỗ trợ việc tự động hóa thu thập dữ liệu hàng loạt mà không tốn nhiều công sức.

* **[Facebook](https://www.facebook.com)**
  * **Cộng đồng và Hội nhóm:** Một không gian khổng lồ chứa các nhóm và diễn đàn nơi người dùng thảo luận mọi chủ đề. Đây là nơi lý tưởng để thu thập dữ liệu thô và nắm bắt tâm lý đám đông.
  * **Thị trường Marketplace:** Nơi ghi nhận các hoạt động mua bán nhộn nhịp, giúp nhà phân tích đánh giá các xu hướng thị trường và hành vi tiêu dùng của một nhóm đối tượng.
  * **Sự kiện (Events):** Tính năng này giúp các nhà nghiên cứu thu thập thông tin tình báo về các sự kiện thực tế sắp diễn ra và lập danh sách những người có khả năng sẽ tham dự.

* **[LinkedIn](https://www.linkedin.com)**
  * **Mạng lưới chuyên gia:** Trung tâm của các kết nối công việc. Nơi đây cung cấp cái nhìn chi tiết về cơ cấu tổ chức của các công ty, các ngành công nghiệp và những nhân sự chủ chốt, phục vụ đắc lực cho việc nghiên cứu doanh nghiệp.
  * **Bảng tin tuyển dụng:** Các bài đăng tuyển dụng là nguồn tình báo cực kỳ giá trị, cho phép "nhìn trộm" vào các công nghệ (technology stack) mà mục tiêu đang sử dụng và định hướng kinh doanh của họ.
  * **Nội dung chuyên môn:** Người dùng tại đây thường xuyên chia sẻ các bài viết học thuật, slide thuyết trình, tạo ra một kho dữ liệu kiến thức phong phú để phân tích.

* **[Instagram](https://www.instagram.com)**
  * **Dữ liệu trực quan:** Nền tảng xoay quanh hình ảnh và video, hoàn hảo cho các phân tích nhằm phát hiện xu hướng hoặc đánh giá cảm xúc (sentiment analysis).
  * **Sức mạnh của Thẻ (Tag):** Tính năng Hashtag và Geotag (thẻ vị trí địa lý) giúp người phân tích dễ dàng phân loại nội dung và truy vết thông tin theo các khu vực vật lý cụ thể.
  * **Theo dõi Influencer:** Giám sát các cá nhân có sức ảnh hưởng giúp nhà phân tích nắm bắt được các luồng dư luận và chiến lược truyền thông xã hội hiện hành.

## Phân tích Chuyên sâu các Khái niệm trong SOCMINT

Để thực hiện SOCMINT hiệu quả, bạn cần nắm vững ba yếu tố cốt lõi cấu thành nên hồ sơ mạng của một mục tiêu:

* **Chi tiết hồ sơ người dùng (Profile details):** Đây là các **dữ liệu tĩnh**, cung cấp cái nhìn tổng quan về danh tính mà người dùng xây dựng trên mạng. Ví dụ: Trên LinkedIn, họ có thể khai báo chức danh "Windows Admin", liệt kê kỹ năng "Exchange 2013" hoặc "SharePoint". Trên X, phần tiểu sử (bio) có thể tiết lộ sở thích cá nhân.
* **Lịch sử tương tác (Interactions):** Đây là các **hoạt động động** (dynamic activities). Ví dụ: Một người tham gia bình luận trong nhóm an ninh mạng trên Facebook, hoặc chia sẻ một bài viết về hội thảo tấn công mạng (ethical hacking). Tương tác cung cấp cái nhìn thực tế về quan điểm, mối quan tâm và vòng kết nối của người dùng.
* **Siêu dữ liệu (Metadata):** Là phần dữ liệu ngữ cảnh đi kèm theo nội dung được đăng tải. Một bức ảnh có thể chứa các thông tin ẩn như tọa độ địa lý, thời gian đăng, và loại thiết bị sử dụng (iPhone, Android). Siêu dữ liệu giúp xây dựng một hồ sơ theo dõi hành vi cực kỳ chi tiết. 

## Phân loại Dữ liệu trong SOCMINT

Dưới góc độ kỹ thuật, dữ liệu thu thập được chia làm hai loại chính:

* **Thông tin tường minh (Explicit information):** Đây là dữ liệu người dùng **chủ động và cố ý** chia sẻ trên mạng. Nó tạo nên lớp vỏ bọc danh tính trực tuyến rõ ràng nhất. Ví dụ: Đăng một dòng trạng thái bày tỏ quan điểm về bảo mật, cập nhật chứng chỉ IT mới lấy được lên LinkedIn, hoặc khai báo nơi làm việc hiện tại. Nó là cánh cửa trực tiếp nhìn vào đời sống và chuyên môn của mục tiêu.
* **Thông tin ngầm định (Implicit information):** Đây là loại dữ liệu tinh vi hơn, thường bị người dùng **vô tình tiết lộ**. Bằng cách phân tích thói quen nhấn "Thích" (Like) hoặc "Chia sẻ" (Share), nhà phân tích có thể suy ra xu hướng chính trị, sự ủng hộ ngầm cho một nhóm nào đó. Tương tự, thông tin ngầm cũng nằm trong thẻ vị trí hoặc loại thiết bị đăng bài, giúp xác định thói quen di chuyển của mục tiêu.


---

## Truy Vết Người Dùng Với Sherlock

Sherlock là một công cụ giúp bạn tìm kiếm tên người dùng (username) của một cá nhân hoặc tổ chức trên hàng loạt nền tảng mạng xã hội khác nhau. Bạn chỉ cần nhập tên người dùng, và nó sẽ quét để tìm ra mọi hồ sơ mạng xã hội có liên kết với cái tên đó.

Hướng dẫn cài đặt Sherlock trên Kali Linux:

- **Cập nhật hệ thống:** Trước khi cài đặt, hãy đảm bảo hệ thống đã được cập nhật:

```bash
sudo apt update && sudo apt upgrade -y
```

- **Cài đặt Git:**

```bash
sudo apt install git -y
```

- **Sao chép kho lưu trữ Sherlock từ GitHub:**

```bash
git clone https://github.com/sherlock-project/sherlock.git
```

- **Cài đặt các gói phụ thuộc:** Di chuyển vào thư mục Sherlock và cài đặt các thư viện cần thiết. Lưu ý: trên Kali Linux hiện đại cần thêm flag `--break-system-packages` do PEP 668:

```bash
cd sherlock
python3 -m pip install -r requirements.txt --break-system-packages
```

- **Chạy thử nghiệm:** Quét một username (ví dụ: dalemeredith):

```bash
python3 sherlock dalemeredith
```

Ngoài ra, nếu cài qua apt thì chỉ cần:

```bash
sudo apt install sherlock -y
sherlock dalemeredith
```

---

## Phân Tích Hashtag và Định Vị Địa Lý

### Khai Thác Hashtag

Hashtag (ký tự #) giúp dẫn bạn đến trung tâm của các cuộc trò chuyện và chủ đề đang thịnh hành. Các cách sử dụng hiệu quả:

- **Phân tích xu hướng:** Các công cụ như [Hashtagify](https://hashtagify.me/) và [RiteTag](https://ritetag.com/) giúp xác định các hashtag đang hot và đề xuất các hashtag tối ưu để mở rộng phạm vi tìm kiếm.

- **Tương tác cộng đồng:** Các nền tảng giám sát mạng xã hội giúp theo dõi các cộng đồng xoay quanh những hashtag cụ thể. Lưu ý: TweetDeck đã chuyển thành **X Pro** (yêu cầu đăng ký X Premium trả phí từ tháng 8/2023). Có thể thay thế bằng [Tweetdeck.twitter.com](https://tweetdeck.twitter.com) nếu có tài khoản X Premium, hoặc dùng công cụ thay thế miễn phí như [TweetBeaver](https://tweetbeaver.com/).

- **Khám phá nội dung:** [BuzzSumo](https://buzzsumo.com/) là công cụ tìm kiếm các nội dung phổ biến dựa trên hashtag.

### Định Vị Địa Lý (Geolocation)

Định vị địa lý cho phép xác định tọa độ (vĩ độ và kinh độ) của thiết bị kết nối internet. Có ba loại chính:

- **Truy vết IP (Server-based):** Theo dõi vị trí vật lý liên kết với địa chỉ IP. Độ chính xác phụ thuộc vào nhà cung cấp dịch vụ mạng, nên đôi khi mang tính phỏng đoán.

- **Định vị GPS (Device-based):** Dựa vào tín hiệu GPS và mạng di động. Độ chính xác cao ở khu vực đông dân, nhưng có thể sai lệch ở vùng hẻo lánh.

- **Kết hợp (Hybrid):** Phương pháp tối ưu, kết hợp cả dữ liệu IP và GPS để cho ra thông tin vị trí toàn diện và chính xác nhất.


---

## Phân Tích EXIF — Siêu Dữ Liệu Ẩn Trong Ảnh

Dữ liệu EXIF trong một bức ảnh âm thầm ghi lại các thông tin như tọa độ GPS, ngày giờ, cài đặt máy ảnh và thiết bị chụp. Tuy nhiên, hầu hết các nền tảng mạng xã hội đều tự động xóa thông tin này khi tải ảnh lên để bảo vệ người dùng.

Nếu có tệp ảnh gốc, có thể trích xuất siêu dữ liệu bằng:

- **Công cụ trực tuyến:** [Jimpl](https://jimpl.com/) cho phép tải ảnh lên và bóc tách dữ liệu EXIF trực tiếp trên trình duyệt.

- **ExifTool trên Kali Linux:** ExifTool được tích hợp sẵn trong Kali để đọc và chỉnh sửa metadata. Lệnh đọc siêu dữ liệu của một tệp ảnh:

```bash
exiftool yourmasterpiece.jpg
```

---

## Các Tầng Internet: Surface Web, Deep Web và Dark Web

Internet có nhiều tầng, thường được hình dung như một tảng băng trôi:

- **Surface Web (Web Bề Mặt):** Phần nổi của tảng băng. Đây là nơi bạn truy cập qua Google, Bing — YouTube, Wikipedia, các trang tin tức. Được các công cụ tìm kiếm lập chỉ mục đầy đủ.

- **Deep Web (Web Sâu):** Phần chìm khổng lồ. Chứa cơ sở dữ liệu, tài khoản email cá nhân, dịch vụ đăng ký trả phí, dữ liệu nội bộ doanh nghiệp. Không được Google lập chỉ mục và yêu cầu quyền truy cập cụ thể.

- **Dark Web (Web Tối):** Khu vực sâu nhất, ẩn danh hoàn toàn, chỉ có thể truy cập bằng các trình duyệt đặc thù. Do tính ẩn danh, đây cũng là điểm nóng của nhiều hoạt động phi pháp.

Để truy cập Dark Web an toàn:

- **Dùng VPN** để ẩn địa chỉ IP thật.
- **Cài đặt Tor Browser** — trình duyệt chuyên dụng duy nhất hỗ trợ truy cập các trang `.onion`. Tải tại [torproject.org](https://www.torproject.org/).
- **Dùng công cụ tìm kiếm riêng:** Google không hoạt động trên Dark Web. Có thể dùng phiên bản Onion của [DuckDuckGo](https://duckduckgogg42xjoc72x3sjasowoarfbgcmvfimaftt6twagswzczad.onion/).

> Cảnh báo: Luôn đặt tính an toàn và đạo đức nghề nghiệp lên hàng đầu khi hoạt động trong môi trường này.

---

## Thu Thập Thông Tin Với TheHarvester

TheHarvester là công cụ tích hợp sẵn trong Kali Linux, chuyên dùng để tự động thu thập địa chỉ email, tên miền phụ (subdomains), tên máy chủ (hostnames) và tên nhân viên từ nhiều nguồn như Google, Bing, máy chủ PGP, LinkedIn. Đây là công cụ chuẩn mực cho giai đoạn trinh sát (Reconnaissance).

Cú pháp cơ bản:

```bash
theHarvester -d [tên_miền] -l [giới_hạn_kết_quả] -b [nguồn_tìm_kiếm]
```

Trong đó:

- `-d` : Tên miền mục tiêu muốn quét.
- `-l` : Giới hạn số lượng kết quả trả về.
- `-b` : Nguồn tìm kiếm (ví dụ: `google`, `bing`, `pgp`, `linkedin`). Một số nguồn yêu cầu cấu hình API key, nếu không sẽ báo lỗi.

Ví dụ thực tế:

```bash
theHarvester -d example.com -l 500 -b google
```

Kết quả trả về thường là danh sách các URL, địa chỉ IP và email liên quan đến mục tiêu mà công cụ thu thập được từ công cụ tìm kiếm.

---

## Shodan

[Shodan](https://shodan.io) được ví như Google dành cho các thiết bị IoT. Trong khi người dùng thông thường dùng Shodan để kiểm tra xem webcam của mình có bị hack không, các chuyên gia bảo mật dùng nó để tìm kiếm lỗ hổng trên hàng loạt thiết bị kết nối internet — từ web server cho đến hệ thống kiểm soát công nghiệp (ICS).

Cách sử dụng cơ bản nhất là nhập tên miền vào giao diện web để quét. Ví dụ, gõ `os:windows 7` để tìm tất cả các hệ thống vẫn đang chạy Windows 7 — một hệ điều hành đã hết hỗ trợ và là mục tiêu tiềm ẩn của nhiều cuộc tấn công.

Các tính năng nổi bật của Shodan phục vụ công tác bảo mật:

- **Phát hiện thiết bị mới:** Giám sát một dải IP cụ thể để phát hiện khi có thiết bị mới kết nối vào mạng, từ đó nhận biết thiết bị trái phép hoặc rogue device.

- **Xác định lỗ hổng:** Shodan cung cấp thông tin về các lỗ hổng đã biết (CVE) liên quan đến thiết bị trong dải IP được giám sát, cho phép xử lý chủ động trước khi bị khai thác.

- **Theo dõi thay đổi và bất thường:** Giám sát các thay đổi về cấu hình mạng, cổng mở, dịch vụ đang chạy hoặc phiên bản firmware. Bất thường trong các yếu tố này có thể là dấu hiệu của một sự cố bảo mật.

- **Phân tích dữ liệu lịch sử:** Shodan lưu trữ dữ liệu theo thời gian, hữu ích cho việc phân tích xu hướng và theo dõi sự thay đổi trong tình trạng bảo mật của mạng.

- **Cài đặt cảnh báo:** Có thể cấu hình alert để nhận thông báo khi một điều kiện cụ thể xảy ra, ví dụ khi xuất hiện thiết bị mới hoặc một dịch vụ lạ được phát hiện trong dải IP đang theo dõi.

Quy trình giám sát một dải IP trên Shodan gồm 4 bước: thiết lập dải IP cần giám sát, định nghĩa tiêu chí cảnh báo, thường xuyên xem xét báo cáo, và phản hồi kịp thời khi alert được kích hoạt.
