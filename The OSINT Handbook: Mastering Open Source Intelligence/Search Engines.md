# Tầm quan trọng của việc lựa chọn phương pháp phù hợp

Trong OSINT, việc chọn đúng kỹ thuật cho một nhiệm vụ cụ thể cũng giống như việc chọn đúng công cụ để làm việc. Ví dụ:

* **Ngăn chặn gián điệp doanh nghiệp:** Nếu bạn là một chuyên gia an ninh mạng bảo vệ bí mật thương mại, việc rà soát mạng xã hội có thể giúp giám sát hoạt động trực tuyến của nhân sự để ngăn chặn rò rỉ dữ liệu. (Đóng vai trò như một tin tặc mũ trắng - Whitehat hacker).
* **Ứng phó thảm họa:** Sau một thảm họa thiên nhiên, phân tích không gian địa lý thông qua ảnh vệ tinh giúp xác định chính xác các khu vực bị ảnh hưởng để lên kế hoạch cứu hộ hiệu quả.
* **Nghiên cứu thị trường:** Phân tích các xu hướng và luồng ý kiến trên mạng xã hội giúp đánh giá chính xác cảm nhận của người dùng về một thương hiệu hoặc sản phẩm.

Lựa chọn đúng phương pháp OSINT không chỉ là thu thập dữ liệu, mà là thu thập **đúng** dữ liệu, đồng thời luôn phải tuân thủ các chuẩn mực đạo đức nghề nghiệp.

---

## Tìm kiếm và Khai thác Web Bề mặt (Surface Web)

Web bề mặt là phần của internet được các công cụ tìm kiếm lập chỉ mục (index). Đây là một nguồn tài nguyên quan trọng trong OSINT. Để khai thác hiệu quả, bạn cần nắm vững các kỹ thuật duyệt web và tìm kiếm nâng cao.

### Kỹ thuật Sử dụng Công cụ Tìm kiếm Nâng cao

Để khai phá tối đa sức mạnh của [Google Search](https://www.google.com) hoặc các công cụ tìm kiếm khác, việc sử dụng các toán tử (operators) là bắt buộc. Chúng giúp bạn thu hẹp phạm vi và lọc ra chính xác thông tin cần tìm giữa biển dữ liệu rác.

* **Toán tử `site:`**: Dùng để tìm kiếm thông tin chỉ giới hạn bên trong một tên miền cụ thể. Rất hữu ích khi bạn muốn tra cứu dữ liệu chi tiết từ một nguồn đã biết.
    ```text
    site:daledumbsitdown.com "cyber security"
    ```
    *Kết quả sẽ chỉ hiển thị các trang thuộc tên miền `daledumbsitdown.com` có chứa cụm từ "cyber security".*

* **Toán tử `intext:`**: Dùng để tìm các trang web có chứa một cụm từ cụ thể bên trong nội dung văn bản.
    ```text
    intext:"recent cyber attacks"
    ```
    *Kết quả sẽ trả về các trang web chứa chính xác cụm từ "recent cyber attacks", giúp truy xuất nhanh các sự kiện tấn công mạng gần đây.*

Việc kết hợp thành thạo các toán tử này là kỹ năng cốt lõi trong OSINT, giúp đẩy nhanh tốc độ trích xuất dữ liệu.



### Google Hacking (Google Dorking)

Google Hacking (hay Google Dorking) là kỹ thuật sử dụng các toán tử tìm kiếm nâng cao để tìm ra các thông tin nhạy cảm, dữ liệu bị rò rỉ, hoặc các lỗ hổng bảo mật trên các trang web đã được Google lập chỉ mục. 

Dưới đây là các kỹ thuật và ví dụ thực tiễn:

* **Tìm tài liệu nhạy cảm với `filetype:`**
    ```text
    filetype:pdf "annual security report"
    ```
    *Câu lệnh này chỉ tìm các file PDF có chứa cụm từ "annual security report" (Báo cáo an ninh thường niên). Tin tặc thường dùng cách này để thu thập tài liệu nội bộ bị lộ.*

* **Tìm trang quản trị với `inurl:`**
    ```text
    inurl:"admin login"
    ```
    *Tìm kiếm các đường dẫn URL có chứa từ "admin" và "login", thường dẫn thẳng đến các cổng đăng nhập quản trị hệ thống.*

* **Kết hợp toán tử để tìm lỗ hổng**
    ```text
    intext:"Login" inurl:/secure
    ```
    *Giải thích: Lệnh này tìm các trang có chữ "Login" trong nội dung (`intext`), và URL của trang đó phải có đoạn "/secure" (`inurl`). Sự kết hợp này nhằm mục đích dò tìm các trang đăng nhập bảo mật có khả năng tồn tại lỗ hổng.*

* **Dò tìm file cấu hình và khóa SSH bị lộ**
    ```text
    intitle:"index of" .ssh OR ssh_config OR ssh_known_hosts OR authorized_keys OR id_rsa OR id_dsa
    ```
    *Đây là một truy vấn cực kỳ nguy hiểm và phức tạp, bao gồm:*
    * `intitle:"index of"`: Tìm các trang bị lỗi Directory Listing (liệt kê thư mục), khiến máy chủ phơi bày toàn bộ cấu trúc file ra ngoài web.
    * `.ssh`: Thư mục thường chứa các cấu hình và khóa SSH.
    * `ssh_config`: File cấu hình máy khách SSH.
    * `ssh_known_hosts`: File lưu trữ host keys để xác thực máy chủ.
    * `authorized_keys`: File chứa public keys cho phép đăng nhập không cần mật khẩu.
    * `id_rsa` / `id_dsa`: Các file chứa **Private Key** (khóa riêng tư). Nếu tin tặc lấy được file này, chúng có thể đăng nhập thẳng vào máy chủ.
    * Toán tử `OR`: Yêu cầu Google trả về kết quả nếu trang web có chứa BẤT KỲ từ khóa nào trong danh sách trên.

Google Dorking có thể được sử dụng để tìm kiếm các camera an ninh bị hớ hênh, các thiết bị IoT không có mật khẩu, các cổng đăng nhập SharePoint, và thậm chí là can thiệp vào các máy in kết nối mạng của một công ty.

### Công cụ Tìm kiếm Học thuật (Academic Search Engines)

Đây là kho lưu trữ các tài liệu nghiên cứu chuyên sâu, nơi bạn có thể tìm thấy những thông tin mang tính nền tảng hoặc các báo cáo phân tích kỹ thuật chất lượng cao:

* **[Google Scholar](https://scholar.google.com/)**: Đây là nơi hội tụ các bài báo khoa học, luận văn, sách, tài liệu hội nghị và bằng sáng chế. Nó giúp bạn tìm kiếm các tài liệu được nghiên cứu kỹ lưỡng mà không bị nhiễu bởi các trang web rác.
* **[PubMed](https://pubmed.ncbi.nlm.nih.gov/)**: Chuyên trang hàng đầu về y sinh học và khoa học đời sống.
* **[IEEE Xplore](https://ieeexplore.ieee.org/Xplore/home.jsp)**: Thư viện kỹ thuật số cung cấp quyền truy cập toàn diện vào các tài liệu chuyên ngành về kỹ thuật điện, khoa học máy tính và điện tử.

### Công cụ Tìm kiếm Mã nguồn (Code Search Engines)

Các nền tảng này không chỉ lưu trữ các dự án mã nguồn mở mà đôi khi còn vô tình chứa các dữ liệu nhạy cảm hoặc làm lộ các lỗ hổng phần mềm của tổ chức:

* **[GitHub](https://github.com)**: Kho lưu trữ mã nguồn mở phổ biến nhất thế giới
* **[SourceForge](https://sourceforge.net)**: Một nền tảng lâu đời cho phép người dùng tìm kiếm, tạo và xuất bản các phần mềm mã nguồn mở

### Công cụ Tìm kiếm Bằng sáng chế (Patent Search Engines)

Bằng sáng chế cung cấp cái nhìn chi tiết về các công nghệ đang được phát triển, bản thiết kế hạ tầng và định hướng tương lai của một tổ chức:

* **[Google Patents](https://patents.google.com/)**: Cung cấp thông tin chi tiết về các bằng sáng chế, giúp người phân tích hiểu rõ các tiến bộ công nghệ và mức độ cạnh tranh trên thị trường của mục tiêu.
* **[Cơ sở dữ liệu USPTO](https://www.uspto.gov)** (United States Patent and Trademark Office): Hệ thống dữ liệu cấp cao của Mỹ, cung cấp thông tin cực kỳ chi tiết bao gồm mô tả kỹ thuật, các yêu cầu bồi thường và trích dẫn liên quan đến các phát minh.

### Công cụ Tìm kiếm Hình ảnh (Image Search Engines)

Hình ảnh có thể vô tình tiết lộ hạ tầng hệ thống, mạng lưới thiết bị

* **[TinEye](https://tineye.com/)**: Công cụ tìm kiếm hình ảnh đảo ngược (Reverse image search). Chuyên dùng để xác minh tính xác thực của một bức ảnh, tìm ra nguồn gốc ban đầu hoặc các trang web khác đang sử dụng hình ảnh đó.
* **[Google Images](https://images.google.com/)**: Sở hữu cơ sở dữ liệu hình ảnh khổng lồ. Trong OSINT và bảo mật, tin tặc có thể khai thác kho dữ liệu này để tìm kiếm các sơ đồ mạng bị rò rỉ, hình ảnh chụp cấu hình hệ thống, từ đó vạch ra kế hoạch tấn công.

