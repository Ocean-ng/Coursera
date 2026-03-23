**Beautiful Soup** là một thư viện Python dùng để parse (phân tích cú pháp) HTML và XML, rất phổ biến trong web scraping.
Cách hoạt động đơn giản: dùng requests để tải nội dung trang web về, rồi dùng Beautiful Soup để "bóc tách" dữ liệu từ đống HTML đó - tìm thẻ, lấy text, lấy link, v.v.

-----

## Khai thác Nền tảng Mạng xã hội (Social Media OSINT)

Các mạng xã hội ([Twitter/X](https://twitter.com), [Facebook](https://www.facebook.com), [LinkedIn](https://www.linkedin.com), [Instagram](https://www.instagram.com)) không chỉ để giải trí mà là nguồn dữ liệu khổng lồ. Việc phân tích OSINT trên mạng xã hội giúp vẽ nên bức tranh toàn cảnh về nhân sự, hoạt động của một tổ chức, từ đó phát hiện ra các lỗ hổng tiềm ẩn. Nguyên tắc của quá trình này là thu thập thụ động (không tương tác trực tiếp với mục tiêu) và tập trung vào "yếu tố con người".

Các phương pháp phân tích phổ biến bao gồm:

* **Thu thập và tổng hợp hồ sơ (Profile aggregation):** Sử dụng các công cụ như [Pipl](https://pipl.com) hoặc [Spokeo](https://www.spokeo.com) để gom nhóm dữ liệu về nhân viên (chức danh, sở thích). Dữ liệu này thường được dùng để xây dựng các kịch bản tấn công lừa đảo (phishing) có độ chính xác cao.
* **Phân tích nội dung (Content analysis):** Theo dõi thói quen đăng bài, lượt thích, bình luận. Ví dụ, một nhân viên phàn nàn về phần mềm công ty trên mạng có thể vô tình làm lộ kiến trúc hệ thống (software stack) mà tổ chức đang sử dụng.
* **Vị trí địa lý và Siêu dữ liệu (Geolocation and metadata):** Ảnh chụp thường chứa dữ liệu vị trí, có thể làm lộ vị trí hạ tầng quan trọng như phòng máy chủ. Ngoài ra, siêu dữ liệu (metadata) của ảnh có thể tiết lộ loại thiết bị phần cứng mà công ty cấp phát cho nhân viên.
* **Vẽ sơ đồ mối quan hệ (Relationship mapping):** Sử dụng các công cụ như [Maltego](https://www.maltego.com) để trực quan hóa mạng lưới liên kết giữa các cá nhân, từ đó suy ra cấu trúc tổ chức hoặc phát hiện các mối quan hệ ngầm với nhà cung cấp, đối thủ.
* **Phân tích cảm xúc (Sentiment analysis):** Đánh giá mức độ hài lòng của nhân viên qua các bài đăng. Tinh thần làm việc xuống thấp là dấu hiệu cảnh báo nguy cơ bảo mật từ nội bộ (insider threats) hoặc sự chểnh mảng trong công việc.
* **Khám phá quy luật và sự kiện (Event and pattern discovery):** Tìm kiếm thông tin về lịch nâng cấp, vá lỗi hệ thống để xác định thời điểm mà hệ thống dễ bị tấn công nhất. Thông tin về các sự kiện công ty cũng cho biết khi nào văn phòng trống người hoặc đội IT đang bận rộn.
* **Phân tích tin tuyển dụng (Recruitment and job postings):** Tin tuyển dụng trên [LinkedIn](https://www.linkedin.com) thường liệt kê chi tiết các công nghệ đang dùng, dự án đang chạy hoặc định hướng tương lai, giúp người phân tích nắm bắt được nền tảng kỹ thuật của tổ chức.

## Phân tích Không gian địa lý và Hình ảnh (Geospatial and Imagery Analysis)

Phương pháp này tập trung vào việc đặt dữ liệu vào bối cảnh địa lý để tìm ra các quy luật hoặc cấu trúc ẩn mà việc phân tích văn bản thông thường sẽ bỏ sót.

* **Phân tích ảnh vệ tinh và không ảnh:** Không chỉ dừng lại ở Google Earth, các nhà phân tích sử dụng các nền tảng chuyên dụng như [Sentinel Hub](https://www.sentinel-hub.com/) để theo dõi sự thay đổi của môi trường, cấu trúc đô thị hoặc các cơ sở vật chất không được công bố.
* **Kỹ thuật định vị (Geolocation techniques):** Sử dụng bản đồ của [Google Maps](https://www.google.com/maps), [Bing Maps](https://www.bing.com/maps), [Yandex Maps](https://yandex.com/maps) để tìm ra chính xác tọa độ nơi một bức ảnh được chụp. Tùy vào mục đích, có thể dùng thêm các công cụ theo dõi camera đường phố, hoặc radar hàng không/hàng hải để giám sát mục tiêu.
* **Phân tích hình ảnh chuyên sâu (Image analysis):** Soi xét kỹ lưỡng các chi tiết trong ảnh như bóng đổ (để đoán thời gian chụp) hoặc các mốc địa lý phía hậu cảnh. Các công cụ như [FotoForensics](https://fotoforensics.com/) được sử dụng để bóc tách và tìm kiếm dữ liệu bị ẩn giấu bên trong bức ảnh.


