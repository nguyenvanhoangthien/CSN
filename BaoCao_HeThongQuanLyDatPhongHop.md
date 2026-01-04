# BÁO CÁO ĐỒ ÁN
## HỆ THỐNG QUẢN LÝ ĐẶT PHÒNG HỌP - KHOA CÔNG NGHỆ THÔNG TIN

---

### THÔNG TIN SINH VIÊN
- **Họ và tên:** [Tên sinh viên]
- **Mã số sinh viên:** [MSSV]
- **Lớp:** [Lớp]
- **Khoa:** Công nghệ thông tin
- **Trường:** Đại học Trà Vinh

### THÔNG TIN ĐỒ ÁN
- **Tên đề tài:** Hệ thống Quản lý Đặt phòng họp
- **Môn học:** [Tên môn học]
- **Giảng viên hướng dẫn:** [Tên giảng viên]
- **Thời gian thực hiện:** [Thời gian]

---

## 1. GIỚI THIỆU ĐỀ TÀI

### 1.1. Lý do chọn đề tài
Trong bối cảnh giáo dục hiện đại, việc quản lý và sử dụng hiệu quả các phòng học, phòng họp là một nhu cầu thiết yếu. Khoa Công nghệ thông tin với nhiều hoạt động học tập, nghiên cứu và hội thảo cần một hệ thống quản lý đặt phòng chuyên nghiệp, giúp:

- Tối ưu hóa việc sử dụng tài nguyên phòng học
- Tránh xung đột lịch sử dụng phòng
- Quản lý thông tin đăng ký một cách có hệ thống
- Nâng cao hiệu quả công tác quản lý

### 1.2. Mục tiêu đề tài
- **Mục tiêu chính:** Xây dựng hệ thống web quản lý đặt phòng họp hoàn chỉnh
- **Mục tiêu cụ thể:**
  - Phát triển giao diện thân thiện, dễ sử dụng
  - Xây dựng hệ thống phân quyền rõ ràng (Admin/User)
  - Tự động hóa quy trình đăng ký và quản lý
  - Đảm bảo tính bảo mật và ổn định của hệ thống

### 1.3. Phạm vi đề tài
- **Đối tượng sử dụng:** Giảng viên, cán bộ Khoa CNTT
- **Phạm vi ứng dụng:** Quản lý phòng họp trong phạm vi Khoa
- **Công nghệ sử dụng:** PHP, MySQL, HTML, CSS, JavaScript, Bootstrap

---

## 2. CƠ SỞ LÝ THUYẾT

### 2.1. Công nghệ sử dụng

#### 2.1.1. PHP (PHP: Hypertext Preprocessor)

**1. Khái niệm và bản chất của PHP**

PHP (PHP: Hypertext Preprocessor) là một ngôn ngữ kịch bản phía máy chủ (server-side scripting language) được thiết kế đặc biệt cho phát triển web. Khác với HTML, CSS và JavaScript hoạt động ở phía client (trình duyệt), PHP thực thi hoàn toàn trên máy chủ web và chỉ gửi kết quả HTML về cho trình duyệt.

Trong mô hình ứng dụng web, PHP đóng vai trò là tầng xử lý logic nghiệp vụ (business logic), tương tác với cơ sở dữ liệu, xử lý dữ liệu từ người dùng và tạo ra phản hồi động cho trình duyệt. Điều này giúp phân biệt rõ ràng PHP với các công nghệ client-side, tránh nhầm lẫn về bản chất và vai trò của từng công nghệ.

**2. Lịch sử hình thành và phát triển**

PHP ra đời năm 1995 từ nhu cầu thực tế của Rasmus Lerdorf trong việc xử lý form và tạo nội dung web động cho trang cá nhân. Ban đầu chỉ là một tập hợp các script Perl đơn giản, PHP đã phát triển thành một ngôn ngữ lập trình hoàn chỉnh và trở thành một trong những công nghệ phổ biến nhất cho phát triển web.

Các mốc phát triển quan trọng:
- **PHP 5 (2004):** Giới thiệu mô hình lập trình hướng đối tượng hoàn chỉnh
- **PHP 7 (2015):** Cải thiện hiệu suất đáng kể, giảm tiêu thụ bộ nhớ
- **PHP 8 (2020):** Thêm nhiều tính năng mới như JIT compiler, union types

Sự phát triển liên tục này cho thấy tính ổn định, trưởng thành và khả năng thích nghi của PHP với các yêu cầu công nghệ hiện đại, điều quan trọng khi đánh giá một công nghệ để sử dụng trong hệ thống thực tế.

**3. Vai trò của PHP trong phát triển web**

PHP đóng vai trò then chốt trong việc xây dựng các ứng dụng web động, đặc biệt phù hợp với:

- **Xử lý dữ liệu từ biểu mẫu:** Nhận và validate dữ liệu từ form HTML
- **Tương tác cơ sở dữ liệu:** Kết nối và thao tác với MySQL, MariaDB, PostgreSQL
- **Quản lý phiên làm việc:** Xử lý đăng nhập, phân quyền, session, cookie
- **Xây dựng hệ thống quản lý:** Website nội bộ, CMS, hệ thống quản lý doanh nghiệp

Trong đề tài này, PHP được sử dụng để xây dựng hệ thống quản lý đặt phòng họp với các chức năng đăng nhập, phân quyền, quản lý dữ liệu phòng và lịch đăng ký - những ứng dụng điển hình thể hiện sức mạnh của PHP trong phát triển hệ thống quản lý nội bộ.

**4. Đặc điểm và cơ chế hoạt động**

PHP hoạt động theo nguyên lý server-side processing với các đặc điểm:

- **Bảo mật mã nguồn:** PHP chạy trên máy chủ, mã nguồn không hiển thị cho người dùng cuối
- **Tích hợp HTML:** PHP có thể nhúng trực tiếp vào HTML để tạo nội dung động
- **Quy trình xử lý:** Người dùng gửi request → Web server → PHP engine xử lý → Trả về HTML

Cơ chế này đặc biệt phù hợp với các hệ thống cần bảo mật cao và xử lý dữ liệu phức tạp như hệ thống quản lý sinh viên, giảng viên, hay đặt phòng họp, nơi logic nghiệp vụ và dữ liệu nhạy cảm cần được bảo vệ ở phía server.

**5. Ưu điểm và hạn chế**

**Ưu điểm:**
- **Dễ tiếp cận:** Cú pháp đơn giản, dễ học cho người mới bắt đầu
- **Mã nguồn mở:** Miễn phí, cộng đồng phát triển lớn và tích cực
- **Tích hợp tốt:** Hỗ trợ nhiều hệ quản trị cơ sở dữ liệu và web server
- **Triển khai đơn giản:** Hầu hết hosting đều hỗ trợ PHP
- **Tài liệu phong phú:** Documentation đầy đủ, nhiều framework hỗ trợ

**Hạn chế:**
- **Hiệu suất:** Phụ thuộc nhiều vào cách viết code và cấu hình server
- **Bảo mật:** Dễ mắc lỗi bảo mật nếu không tuân thủ best practices
- **Kiểu dữ liệu:** Tính linh hoạt của weak typing có thể gây lỗi logic
- **Đa luồng:** Hạn chế trong xử lý đồng thời so với một số ngôn ngữ khác

#### 2.1.2. MySQL

**1. Khái niệm và bản chất của MySQL**

MySQL là một hệ quản trị cơ sở dữ liệu quan hệ (Relational Database Management System - RDBMS) mã nguồn mở, được phát triển dựa trên mô hình cơ sở dữ liệu quan hệ và sử dụng ngôn ngữ truy vấn có cấu trúc SQL (Structured Query Language). MySQL hoạt động theo kiến trúc client-server, cho phép nhiều người dùng truy cập đồng thời và quản lý dữ liệu một cách hiệu quả.

Trong kiến trúc ứng dụng web, MySQL đóng vai trò là tầng lưu trữ dữ liệu (Data Layer), chịu trách nhiệm lưu trữ, tổ chức và cung cấp dữ liệu cho tầng ứng dụng (PHP) thông qua các câu lệnh SQL.

**2. Lịch sử phát triển và vị thế**

MySQL được phát triển bởi công ty Thụy Điển MySQL AB từ năm 1995, sau đó được Oracle Corporation mua lại năm 2010. Sự phát triển của MySQL gắn liền với sự bùng nổ của Internet và nhu cầu xây dựng các ứng dụng web động.

Các mốc phát triển quan trọng:
- **MySQL 5.0 (2005):** Giới thiệu stored procedures, triggers, views
- **MySQL 5.7 (2015):** Cải thiện hiệu suất, hỗ trợ JSON data type
- **MySQL 8.0 (2018):** Window functions, Common Table Expressions (CTE)

MySQL hiện là một trong những RDBMS phổ biến nhất thế giới, được sử dụng bởi các tập đoàn lớn như Facebook, Google, Twitter, và hàng triệu website trên toàn cầu.

**3. Vai trò của MySQL trong hệ thống web**

MySQL đóng vai trò then chốt trong việc xây dựng các ứng dụng web, đặc biệt trong mô hình LAMP (Linux, Apache, MySQL, PHP):

- **Lưu trữ dữ liệu:** Quản lý thông tin người dùng, nội dung, cấu hình hệ thống
- **Đảm bảo tính toàn vẹn:** Thông qua các ràng buộc (constraints) và quan hệ (relationships)
- **Hỗ trợ truy vấn phức tạp:** JOIN, subquery, aggregate functions
- **Quản lý phiên làm việc:** Lưu trữ session data, user preferences

Trong đề tài hệ thống quản lý đặt phòng họp, MySQL được sử dụng để lưu trữ thông tin người dùng, phòng họp, lịch đăng ký và quản lý các mối quan hệ phức tạp giữa các thực thể này.

**4. Tính năng nổi bật của MySQL**

**4.1. Hiệu suất và khả năng mở rộng**
- **Storage Engines:** InnoDB (ACID compliant), MyISAM (tốc độ cao)
- **Query Optimization:** Query cache, index optimization
- **Partitioning:** Phân vùng dữ liệu để cải thiện hiệu suất
- **Replication:** Master-slave, master-master replication

**4.2. Tính năng bảo mật**
- **User Management:** Hệ thống phân quyền chi tiết theo user, host, database
- **SSL/TLS Encryption:** Mã hóa kết nối client-server
- **Data Masking:** Che giấu dữ liệu nhạy cảm trong môi trường development
- **Audit Logging:** Ghi log các hoạt động truy cập và thay đổi dữ liệu

**4.3. Tính năng dữ liệu nâng cao**
- **ACID Compliance:** Đảm bảo tính nhất quán dữ liệu
- **Foreign Key Constraints:** Duy trì tính toàn vẹn tham chiếu
- **Triggers và Stored Procedures:** Tự động hóa logic nghiệp vụ
- **Views:** Tạo bảng ảo để đơn giản hóa truy vấn phức tạp

**4.4. Khả năng tích hợp**
- **Multi-platform:** Chạy trên Linux, Windows, macOS
- **Language Support:** Hỗ trợ nhiều ngôn ngữ lập trình
- **Cloud Integration:** MySQL as a Service trên AWS, Google Cloud, Azure
- **Backup và Recovery:** mysqldump, binary logging, point-in-time recovery

**5. Ưu điểm và hạn chế trong ứng dụng thực tế**

**Ưu điểm:**
- **Hiệu suất cao:** Tối ưu cho các ứng dụng web với lượng truy cập lớn
- **Ổn định và tin cậy:** Được kiểm nghiệm qua hàng triệu deployment
- **Dễ sử dụng:** Cú pháp SQL chuẩn, công cụ quản lý trực quan
- **Cộng đồng lớn:** Tài liệu phong phú, hỗ trợ kỹ thuật tốt
- **Chi phí thấp:** Mã nguồn mở, không phí license

**Hạn chế:**
- **Giới hạn tính năng:** Một số tính năng enterprise chỉ có trong phiên bản thương mại
- **Xử lý dữ liệu lớn:** Hiệu suất giảm với dataset rất lớn so với NoSQL
- **Phụ thuộc Oracle:** Quyết định phát triển phụ thuộc vào chiến lược Oracle

**6. Ứng dụng MySQL trong đề tài**

Trong hệ thống quản lý đặt phòng họp, MySQL được sử dụng để:
- **Quản lý người dùng:** Lưu trữ thông tin đăng nhập, phân quyền
- **Quản lý phòng họp:** Thông tin phòng, sức chứa, trang thiết bị
- **Quản lý lịch đăng ký:** Thời gian, trạng thái, mối quan hệ với user và phòng
- **Đảm bảo tính toàn vẹn:** Foreign key constraints ngăn chặn dữ liệu không hợp lệ
- **Tối ưu truy vấn:** Index trên các trường thường xuyên tìm kiếm

#### 2.1.3. Bootstrap Framework

**1. Khái niệm và bản chất của Bootstrap**

Bootstrap là một framework front-end mã nguồn mở được phát triển bởi Twitter, cung cấp một bộ sưu tập các thành phần CSS và JavaScript được thiết kế sẵn để xây dựng giao diện web responsive và mobile-first. Bootstrap hoạt động theo nguyên tắc "write once, run everywhere", cho phép developers tạo ra giao diện nhất quán trên mọi thiết bị và trình duyệt.

Khác với việc viết CSS thuần từ đầu, Bootstrap cung cấp một hệ thống grid linh hoạt, các component UI được chuẩn hóa và utility classes, giúp tăng tốc độ phát triển và đảm bảo tính nhất quán trong thiết kế.

**2. Lịch sử phát triển và tầm ảnh hưởng**

Bootstrap được ra mắt năm 2011 bởi Mark Otto và Jacob Thornton tại Twitter như một công cụ nội bộ để đồng bộ hóa giao diện các sản phẩm. Sau khi được mở mã nguồn, Bootstrap nhanh chóng trở thành framework CSS phổ biến nhất thế giới.

Các phiên bản quan trọng:
- **Bootstrap 3 (2013):** Mobile-first approach, flat design
- **Bootstrap 4 (2018):** Flexbox grid system, Sass support
- **Bootstrap 5 (2021):** Loại bỏ jQuery dependency, CSS custom properties

Hiện tại, Bootstrap được sử dụng bởi hàng triệu website và được coi là tiêu chuẩn de facto cho phát triển giao diện web responsive.

**3. Vai trò của Bootstrap trong phát triển web hiện đại**

Bootstrap đóng vai trò quan trọng trong việc giải quyết các thách thức của phát triển giao diện web:

- **Responsive Design:** Tự động điều chỉnh layout cho desktop, tablet, mobile
- **Cross-browser Compatibility:** Đảm bảo hiển thị nhất quán trên các trình duyệt
- **Rapid Prototyping:** Tạo prototype nhanh chóng với các component có sẵn
- **Design Consistency:** Duy trì tính nhất quán trong thiết kế toàn hệ thống

Trong đề tài hệ thống quản lý đặt phòng họp, Bootstrap được sử dụng để tạo giao diện chuyên nghiệp, thân thiện với người dùng và hoạt động tốt trên mọi thiết bị, từ máy tính để bàn đến điện thoại di động.

**4. Tính năng và thành phần chính**

**4.1. Grid System**
- **12-column layout:** Hệ thống lưới linh hoạt với 12 cột
- **Breakpoints:** xs, sm, md, lg, xl cho các kích thước màn hình khác nhau
- **Flexbox-based:** Sử dụng CSS Flexbox để căn chỉnh và phân bố không gian

**4.2. Components**
- **Navigation:** Navbar, breadcrumb, pagination
- **Forms:** Input groups, validation states, custom controls
- **Buttons:** Đa dạng style, size và state
- **Cards:** Container linh hoạt cho nội dung
- **Modals:** Dialog boxes và popup windows

**4.3. Utilities**
- **Spacing:** Margin và padding với hệ thống số chuẩn
- **Typography:** Font sizes, weights, text alignment
- **Colors:** Bảng màu nhất quán cho text và background
- **Display:** Responsive display utilities

**4.4. JavaScript Components**
- **Interactive Elements:** Dropdown, tooltip, popover
- **Navigation:** Tab, accordion, carousel
- **Feedback:** Alert, toast, modal

**5. Ưu điểm và hạn chế trong ứng dụng thực tế**

**Ưu điểm:**
- **Tốc độ phát triển:** Giảm thời gian coding CSS từ 60-80%
- **Responsive tự động:** Mobile-first approach đảm bảo tương thích đa thiết bị
- **Cộng đồng lớn:** Tài liệu phong phú, themes và plugins đa dạng
- **Maintainability:** Code dễ đọc, dễ bảo trì nhờ naming convention chuẩn
- **Browser Support:** Tương thích với tất cả trình duyệt hiện đại

**Hạn chế:**
- **File size:** CSS và JS file khá lớn nếu không tối ưu
- **Generic look:** Nhiều website có giao diện tương tự nhau
- **Learning curve:** Cần thời gian để nắm vững grid system và components
- **Customization:** Khó tùy chỉnh sâu mà không override nhiều CSS

**6. Ứng dụng Bootstrap trong đề tài**

Trong hệ thống quản lý đặt phòng họp, Bootstrap được sử dụng để:
- **Layout responsive:** Đảm bảo giao diện hoạt động tốt trên mọi thiết bị
- **Form styling:** Tạo các form đăng nhập, đăng ký, đặt phòng đẹp mắt
- **Table components:** Hiển thị danh sách phòng và lịch đăng ký
- **Navigation:** Menu điều hướng và breadcrumb
- **Feedback UI:** Alert messages và confirmation dialogs

### 2.2. Mô hình kiến trúc phần mềm

#### 2.2.1. Mô hình MVC (Model-View-Controller)

**1. Giới thiệu mô hình MVC**

MVC (Model-View-Controller) là một mô hình kiến trúc phần mềm (architectural pattern) được phát triển từ những năm 1970 tại Xerox PARC và trở thành một trong những pattern phổ biến nhất trong phát triển ứng dụng web hiện đại. Mô hình MVC được thiết kế dựa trên nguyên tắc "Separation of Concerns" - tách biệt các mối quan tâm khác nhau trong ứng dụng.

Bản chất của MVC là chia ứng dụng thành ba thành phần độc lập:
- **Model:** Quản lý dữ liệu và logic nghiệp vụ
- **View:** Chịu trách nhiệm hiển thị giao diện người dùng
- **Controller:** Điều phối tương tác giữa Model và View

Mô hình này đặc biệt phù hợp với các ứng dụng web vì nó phản ánh chính xác cách thức hoạt động của web: người dùng gửi request (Controller xử lý), hệ thống truy xuất dữ liệu (Model), và trả về giao diện (View).

Trong bối cảnh phát triển web với PHP, MVC giúp tổ chức code một cách có hệ thống, tách biệt logic xử lý dữ liệu khỏi logic hiển thị, từ đó tạo ra các ứng dụng dễ bảo trì, mở rộng và tái sử dụng.

**2. Nguyên tắc hoạt động của mô hình MVC**

**2.1. Ba thành phần chính trong hệ thống đặt phòng**

**Model - Xử lý dữ liệu:**
- Làm việc với database (users, phonghop, dangky)
- Kiểm tra đăng nhập có đúng không
- Kiểm tra phòng có trùng giờ không
- Lưu thông tin đăng ký mới
- **Ví dụ:** File `ketnoi.php`, `xulyDangky.php`

**View - Hiển thị giao diện:**
- Tạo ra trang web mà người dùng nhìn thấy
- Form đăng nhập, danh sách phòng, lịch đăng ký
- Không xử lý dữ liệu, chỉ hiển thị
- **Ví dụ:** File `login.html`, `lietke.php`, `phonghop.php`

**Controller - Điều khiển luồng:**
- Nhận yêu cầu từ người dùng
- Quyết định gọi Model nào để xử lý
- Chọn View nào để hiển thị kết quả
- **Ví dụ:** File `login.php`, `datphong.php`, `register.php`

**2.2. Cách hoạt động đơn giản**

Khi người dùng đăng ký phòng:

```
1. Người dùng điền form đăng ký phòng (View: dangkyphong.php)
2. Click nút "Đăng ký" → gửi dữ liệu đến Controller
3. Controller (xulyDangky.php) nhận dữ liệu
4. Controller gọi Model kiểm tra:
   - Phòng có trùng giờ không?
   - Thời gian có hợp lệ không?
5. Model lưu vào database nếu OK
6. Controller chọn View (phonghop.php) để hiển thị kết quả
7. Người dùng thấy danh sách đăng ký đã cập nhật
```

**2.3. Tại sao tách ra 3 phần?**

- **Dễ sửa:** Muốn thay đổi giao diện chỉ cần sửa View
- **Dễ bảo trì:** Lỗi database chỉ cần tìm trong Model
- **Làm việc nhóm:** Người này làm giao diện, người kia làm xử lý dữ liệu
- **Tái sử dụng:** Cùng một Model có thể dùng cho nhiều View khác nhau

**3. Ưu điểm và nhược điểm của mô hình MVC**

**Ưu điểm:**
- **Dễ bảo trì:** Muốn sửa giao diện chỉ cần sửa View, sửa database chỉ cần sửa Model
- **Làm việc nhóm hiệu quả:** Nhiều người có thể làm cùng lúc mà không xung đột
- **Tái sử dụng code:** Một Model có thể dùng cho nhiều View khác nhau
- **Dễ mở rộng:** Thêm tính năng mới không ảnh hưởng code cũ
- **Dễ test:** Có thể test từng phần riêng biệt

**Nhược điểm:**
- **Phức tạp hơn:** Dự án nhỏ có thể không cần thiết
- **Nhiều file hơn:** Cần tổ chức nhiều file và thư mục
- **Học tập:** Cần thời gian để hiểu và áp dụng đúng
- **Performance:** Có thể chậm hơn một chút do nhiều layer

**Kết luận:** MVC phù hợp với hệ thống quản lý đặt phòng vì có nhiều chức năng (đăng nhập, quản lý phòng, đăng ký) và cần bảo trì lâu dài.

---

## 3. THỰC HIỆN HÓA NGHIÊN CỨU

### 3.1. Quy trình nghiên cứu và phát triển

#### 3.1.1. Các bước nghiên cứu đã tiến hành

**Bước 1: Khảo sát và phân tích hiện trạng**
- Khảo sát quy trình đặt phòng hiện tại tại Khoa CNTT
- Phỏng vấn giảng viên và cán bộ quản lý về nhu cầu sử dụng phòng
- Phân tích các vấn đề tồn tại: trùng lịch, khó quản lý, thiếu minh bạch
- Nghiên cứu các hệ thống tương tự để rút kinh nghiệm

**Bước 2: Xác định yêu cầu hệ thống**
- Thu thập và phân loại yêu cầu chức năng/phi chức năng
- Xác định các actor và use case chính
- Định nghĩa ràng buộc kỹ thuật và nghiệp vụ
- Lập ma trận truy xuất yêu cầu

**Bước 3: Nghiên cứu công nghệ và kiến trúc**
- So sánh các công nghệ web: PHP vs Python vs Node.js
- Lựa chọn RDBMS phù hợp: MySQL vs PostgreSQL
- Nghiên cứu mô hình kiến trúc: MVC vs MVP vs MVVM
- Đánh giá framework frontend: Bootstrap vs Foundation

**Bước 4: Thiết kế hệ thống**
- Thiết kế kiến trúc tổng thể
- Thiết kế cơ sở dữ liệu chi tiết
- Thiết kế giao diện người dùng
- Thiết kế API và luồng dữ liệu

**Bước 5: Hiện thực hóa và kiểm thử**
- Triển khai từng module theo thứ tự ưu tiên
- Kiểm thử đơn vị và tích hợp
- Kiểm thử chấp nhận người dùng
- Tối ưu hóa hiệu suất và bảo mật

### 3.2. Đặc tả nhu cầu hệ thống

#### 3.2.1. Phân tích stakeholder

**Stakeholder chính:**
- **Giảng viên:** Người sử dụng chính, cần đặt phòng cho giảng dạy/họp
- **Cán bộ quản lý:** Quản trị hệ thống, phê duyệt/từ chối đăng ký
- **Sinh viên:** Người thụ hưởng gián tiếp từ việc tối ưu sử dụng phòng
- **Ban lãnh đạo Khoa:** Giám sát hiệu quả sử dụng tài nguyên

#### 3.2.2. Đặc tả yêu cầu chức năng

**FR-01: Quản lý người dùng**
- FR-01.1: Đăng ký tài khoản mới
- FR-01.2: Đăng nhập/đăng xuất hệ thống
- FR-01.3: Quản lý thông tin cá nhân
- FR-01.4: Phân quyền Admin/User

**FR-02: Quản lý phòng họp (Admin)**
- FR-02.1: Thêm phòng họp mới
- FR-02.2: Cập nhật thông tin phòng
- FR-02.3: Xóa phòng không sử dụng
- FR-02.4: Xem danh sách tất cả phòng

**FR-03: Quản lý đăng ký sử dụng**
- FR-03.1: Đăng ký sử dụng phòng
- FR-03.2: Xem lịch sử đăng ký
- FR-03.3: Sửa/hủy đăng ký
- FR-03.4: Kiểm tra trùng lịch tự động

**FR-04: Quản lý duyệt đăng ký (Admin)**
- FR-04.1: Xem tất cả đăng ký
- FR-04.2: Từ chối đăng ký khi cần thiết
- FR-04.3: Thống kê sử dụng phòng

#### 3.2.3. Đặc tả yêu cầu phi chức năng

**NFR-01: Hiệu suất**
- Thời gian phản hồi < 3 giây
- Hỗ trợ đồng thời 50 người dùng
- Uptime ≥ 99%

**NFR-02: Bảo mật**
- Mã hóa mật khẩu
- Session timeout 30 phút
- Validation đầu vào nghiêm ngặt
- Phân quyền truy cập rõ ràng

**NFR-03: Khả năng sử dụng**
- Giao diện trực quan, dễ sử dụng
- Responsive trên mobile/tablet
- Hỗ trợ các trình duyệt phổ biến
- Thông báo lỗi rõ ràng

**NFR-04: Khả năng bảo trì**
- Code có cấu trúc rõ ràng
- Documentation đầy đủ
- Dễ dàng mở rộng tính năng
- Backup dữ liệu định kỳ

### 3.3. Phân tích và thiết kế hệ thống

#### 3.3.1. Mô hình Use Case

**Use Case Diagram:**
```
                    Hệ thống Quản lý Đặt phòng họp
    
    Giảng viên                                    Admin
        |                                           |
        |-- Đăng nhập                              |-- Quản lý phòng
        |-- Xem danh sách phòng                    |-- Xem tất cả đăng ký  
        |-- Đăng ký phòng                          |-- Từ chối đăng ký
        |-- Xem lịch sử đăng ký                    |-- Quản lý người dùng
        |-- Sửa/Hủy đăng ký                        |-- Thống kê báo cáo
        |-- Cập nhật thông tin cá nhân             |
```

**Use Case chi tiết - Đăng ký phòng:**
- **Actor:** Giảng viên
- **Precondition:** Đã đăng nhập hệ thống
- **Main Flow:**
  1. Chọn phòng từ danh sách
  2. Nhập thông tin: ngày, giờ, mục đích
  3. Hệ thống kiểm tra trùng lịch
  4. Hệ thống tự động duyệt đăng ký
  5. Hiển thị thông báo thành công
- **Alternative Flow:** Trùng lịch → Thông báo lỗi
- **Postcondition:** Đăng ký được lưu với trạng thái "Đã duyệt"

#### 3.3.2. Thiết kế kiến trúc hệ thống

**Kiến trúc 3-tier:**

```
┌─────────────────────────────────────────────────────────┐
│                 PRESENTATION TIER                        │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐     │
│  │   Browser   │  │   Mobile    │  │   Tablet    │     │
│  └─────────────┘  └─────────────┘  └─────────────┘     │
└─────────────────────────────────────────────────────────┘
                            │
                    HTTP/HTTPS Request
                            │
┌─────────────────────────────────────────────────────────┐
│                  APPLICATION TIER                        │
│  ┌─────────────────────────────────────────────────────┐ │
│  │              Web Server (Apache)                    │ │
│  │  ┌─────────┐  ┌─────────┐  ┌─────────┐            │ │
│  │  │  View   │  │Controller│  │  Model  │            │ │
│  │  │ (HTML/  │  │  (PHP)   │  │ (PHP)   │            │ │
│  │  │CSS/JS)  │  │          │  │         │            │ │
│  │  └─────────┘  └─────────┘  └─────────┘            │ │
│  └─────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────┘
                            │
                      SQL Queries
                            │
┌─────────────────────────────────────────────────────────┐
│                    DATA TIER                            │
│  ┌─────────────────────────────────────────────────────┐ │
│  │                MySQL Database                       │ │
│  │  ┌─────────┐  ┌─────────┐  ┌─────────┐            │ │
│  │  │  users  │  │phonghop │  │ dangky  │            │ │
│  │  └─────────┘  └─────────┘  └─────────┘            │ │
│  └─────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────┘
```

#### 3.3.3. Thiết kế cơ sở dữ liệu chi tiết

**Sơ đồ ERD mở rộng:**

```
┌─────────────────────────────────┐
│            USERS                │
├─────────────────────────────────┤
│ PK: id (INT, AUTO_INCREMENT)    │
│     username (VARCHAR(50))      │
│     password (VARCHAR(255))     │
│     email (VARCHAR(100))        │
│     fullname (VARCHAR(100))     │
│     role (ENUM)                 │
│     created_at (TIMESTAMP)      │
│     last_login (TIMESTAMP)      │
└─────────────────────────────────┘
                │
                │ 1:N
                │
┌─────────────────────────────────┐
│           DANGKY                │
├─────────────────────────────────┤
│ PK: id (INT, AUTO_INCREMENT)    │
│ FK: user_id (INT)               │
│ FK: id_phong (INT)              │
│     ngaydat (DATE)              │
│     ngaysudung (DATE)           │
│     giobatdau (TIME)            │
│     gioketthuc (TIME)           │
│     muctieu (TEXT)              │
│     trangthai (ENUM)            │
│     created_at (TIMESTAMP)      │
└─────────────────────────────────┘
                │
                │ N:1
                │
┌─────────────────────────────────┐
│          PHONGHOP               │
├─────────────────────────────────┤
│ PK: id (INT, AUTO_INCREMENT)    │
│     tenphong (VARCHAR(100))     │
│     diadiem (VARCHAR(200))      │
│     succhua (INT)               │
│     mota (TEXT)                 │
└─────────────────────────────────┘
```

**Ràng buộc toàn vẹn:**
- Primary Key: Mỗi bảng có khóa chính duy nhất
- Foreign Key: Đảm bảo tính tham chiếu
- Unique: username không trùng lặp
- Check: trangthai IN ('Đã duyệt', 'Từ chối')
- Not Null: Các trường bắt buộc

#### 3.3.4. Thiết kế giao diện người dùng

**Wireframe trang chính:**

```
┌─────────────────────────────────────────────────────────┐
│  [LOGO]           HỆ THỐNG QUẢN LÝ ĐẶT PHÒNG HỌP      │
│                                                         │
│  [Trang chủ] [Quản lý phòng] [Lịch sử dụng] [Profile] │
└─────────────────────────────────────────────────────────┘
│                                                         │
│  ┌─────────────────────────────────────────────────────┐ │
│  │              WELCOME MESSAGE                        │ │
│  │         Chào mừng [Tên người dùng]                  │ │
│  └─────────────────────────────────────────────────────┘ │
│                                                         │
│  ┌─────────────────────────────────────────────────────┐ │
│  │                QUICK ACTIONS                        │ │
│  │  [Xem phòng]  [Đăng ký phòng]  [Lịch sử]          │ │
│  └─────────────────────────────────────────────────────┘ │
│                                                         │
│  ┌─────────────────────────────────────────────────────┐ │
│  │              RECENT BOOKINGS                        │ │
│  │  Phòng A1 - 08:00-10:00 - 25/12/2024              │ │
│  │  Phòng B2 - 14:00-16:00 - 26/12/2024              │ │
│  └─────────────────────────────────────────────────────┘ │
│                                                         │
┌─────────────────────────────────────────────────────────┐
│  © 2025 Khoa CNTT - Trường Đại học Trà Vinh           │
└─────────────────────────────────────────────────────────┘
```

**Style Guide:**
- **Typography:** Arial, sans-serif
- **Color Palette:**
  - Primary: #03487c (Navy Blue)
  - Secondary: #f9a602 (Orange)
  - Background: #f5f7fa (Light Gray)
  - Text: #333333 (Dark Gray)
- **Spacing:** 8px grid system
- **Breakpoints:** 576px, 768px, 992px, 1200px

### 3.4. Cài đặt và hiện thực hóa

#### 3.4.1. Môi trường phát triển

**Yêu cầu hệ thống:**
- **Operating System:** Windows 10/11, macOS, Linux
- **Web Server:** Apache 2.4+ hoặc Nginx 1.18+
- **PHP:** Version 7.4 hoặc cao hơn
- **Database:** MySQL 8.0 hoặc MariaDB 10.5+
- **Browser:** Chrome 90+, Firefox 88+, Safari 14+

**Công cụ phát triển:**
- **IDE:** Visual Studio Code với extensions PHP, MySQL
- **Version Control:** Git với GitHub repository
- **Database Tool:** phpMyAdmin, MySQL Workbench
- **Testing:** Browser DevTools, Postman cho API testing

#### 3.4.2. Cấu trúc dự án theo mô hình MVC

```
LAB1/
├── config/
│   └── ketnoi.php              # Database configuration
├── controllers/
│   ├── AuthController.php      # Authentication logic
│   ├── RoomController.php      # Room management
│   └── BookingController.php   # Booking management
├── models/
│   ├── User.php               # User model
│   ├── Room.php               # Room model
│   └── Booking.php            # Booking model
├── views/
│   ├── layouts/
│   │   ├── header.php         # Common header
│   │   └── footer.php         # Common footer
│   ├── auth/
│   │   ├── login.php          # Login form
│   │   └── register.php       # Registration form
│   ├── rooms/
│   │   ├── index.php          # Room listing
│   │   └── form.php           # Room form
│   └── bookings/
│       ├── index.php          # Booking history
│       └── form.php           # Booking form
├── assets/
│   ├── css/
│   │   └── style.css          # Custom styles
│   ├── js/
│   │   └── main.js            # JavaScript functions
│   └── images/                # Image assets
├── includes/
│   ├── functions.php          # Helper functions
│   └── validation.php         # Input validation
└── index.php                  # Entry point
```

#### 3.4.3. Quy trình triển khai

**Phase 1: Core Infrastructure (Tuần 1-2)**
- Thiết lập database và tables
- Tạo connection layer
- Implement authentication system
- Basic routing và session management

**Phase 2: User Management (Tuần 3-4)**
- User registration và login
- Profile management
- Role-based access control
- Password security

**Phase 3: Room Management (Tuần 5-6)**
- CRUD operations cho phòng họp
- Admin interface
- Data validation
- Error handling

**Phase 4: Booking System (Tuần 7-8)**
- Booking form và validation
- Conflict detection
- Auto-approval logic
- Booking history

**Phase 5: UI/UX Enhancement (Tuần 9-10)**
- Responsive design implementation
- JavaScript enhancements
- Performance optimization
- Cross-browser testing

**Phase 6: Testing & Deployment (Tuần 11-12)**
- Unit testing
- Integration testing
- User acceptance testing
- Production deployment

#### 3.4.4. Hồ sơ thiết kế kỹ thuật

**Database Schema Script:**
```sql
-- Tạo database
CREATE DATABASE room_booking_system 
CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Sử dụng database
USE room_booking_system;

-- Tạo bảng users
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(100),
    fullname VARCHAR(100),
    role ENUM('admin', 'user') DEFAULT 'user',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_login TIMESTAMP NULL,
    INDEX idx_username (username),
    INDEX idx_role (role)
);

-- Tạo bảng phonghop
CREATE TABLE phonghop (
    id INT PRIMARY KEY AUTO_INCREMENT,
    tenphong VARCHAR(100) NOT NULL,
    diadiem VARCHAR(200),
    succhua INT DEFAULT 0,
    mota TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    INDEX idx_tenphong (tenphong)
);

-- Tạo bảng dangky
CREATE TABLE dangky (
    id INT PRIMARY KEY AUTO_INCREMENT,
    id_phong INT NOT NULL,
    user_id INT NOT NULL,
    ngaydat DATE NOT NULL,
    ngaysudung DATE NOT NULL,
    giobatdau TIME NOT NULL,
    gioketthuc TIME NOT NULL,
    muctieu TEXT,
    trangthai ENUM('Đã duyệt', 'Từ chối') DEFAULT 'Đã duyệt',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (id_phong) REFERENCES phonghop(id) ON DELETE CASCADE,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
    INDEX idx_ngaysudung (ngaysudung),
    INDEX idx_trangthai (trangthai),
    INDEX idx_user_booking (user_id, ngaysudung)
);

-- Thêm dữ liệu mẫu
INSERT INTO users (username, password, email, fullname, role) VALUES
('admin', MD5('admin123'), 'admin@tvu.edu.vn', 'Quản trị viên', 'admin'),
('gv001', MD5('123456'), 'gv001@tvu.edu.vn', 'Nguyễn Văn A', 'user');

INSERT INTO phonghop (tenphong, diadiem, succhua, mota) VALUES
('Phòng A1', 'Tầng 1, Tòa A', 30, 'Phòng học có máy chiếu'),
('Phòng B2', 'Tầng 2, Tòa B', 50, 'Phòng hội thảo lớn');
```

**API Documentation:**
```
POST /login.php
- Input: username, password
- Output: Redirect to index.php hoặc error message

GET /lietke.php
- Input: None (session required)
- Output: Danh sách phòng họp

POST /xulyDangky.php
- Input: id_phong, ngaysudung, giobatdau, gioketthuc, muctieu
- Output: Redirect to phonghop.php hoặc error

GET /phonghop.php
- Input: None (session required)
- Output: Lịch sử đăng ký theo role
```

---

## 4. TRIỂN KHAI HỆ THỐNG

### 4.1. Cấu trúc thư mục dự án
```
LAB1/
├── images/                 # Thư mục chứa hình ảnh
│   ├── logo_CET_2025.png
│   └── [các file ảnh khác]
├── ketnoi.php             # Kết nối database
├── index.php              # Trang chủ
├── login.html/php         # Đăng nhập
├── register.html/php      # Đăng ký tài khoản
├── logout.php             # Đăng xuất
├── profile.php            # Thông tin cá nhân
├── lietke.php             # Danh sách phòng
├── datphong.html/php      # Thêm phòng (Admin)
├── edit.php               # Sửa phòng
├── update.php             # Cập nhật phòng
├── xoa.php                # Xóa phòng
├── phonghop.php           # Lịch sử sử dụng
├── dangkyphong.php        # Form đăng ký phòng
├── xulyDangky.php         # Xử lý đăng ký
├── edit_dangky.php        # Sửa đăng ký
├── update_dangky.php      # Cập nhật đăng ký
├── xoa_dangky.php         # Xóa đăng ký
├── duyet_dangky.php       # Từ chối đăng ký (Admin)
├── check_admin.php        # Kiểm tra quyền admin
├── style.css              # File CSS chính
└── README.md              # Tài liệu dự án
```

### 4.2. Các tính năng đã triển khai

#### 4.2.1. Hệ thống xác thực và phân quyền
- **Đăng ký tài khoản:** Validation dữ liệu, mã hóa mật khẩu MD5
- **Đăng nhập:** Xác thực thông tin, tạo session
- **Phân quyền:** Admin và User với các quyền khác nhau
- **Bảo mật:** Kiểm tra session, chống truy cập trái phép

#### 4.2.2. Quản lý phòng họp (Admin)
- **Thêm phòng:** Form nhập thông tin, validation
- **Sửa phòng:** Cập nhật thông tin phòng
- **Xóa phòng:** Xác nhận trước khi xóa
- **Danh sách phòng:** Hiển thị với phân trang

#### 4.2.3. Đăng ký sử dụng phòng
- **Tự động duyệt:** Đăng ký được chấp nhận ngay lập tức
- **Kiểm tra trùng lịch:** Ngăn đặt phòng trùng giờ
- **Validation thời gian:** Chỉ cho phép đăng ký thời gian tương lai
- **Quản lý đăng ký:** Sửa/xóa đăng ký của mình

#### 4.2.4. Tính năng nâng cao
- **Responsive Design:** Tương thích mọi thiết bị
- **AJAX Validation:** Kiểm tra dữ liệu real-time
- **Chuyển hướng tự động:** Không cần click OK
- **Giao diện thân thiện:** Bootstrap components

---

## 5. KIỂM THỬ HỆ THỐNG

### 5.1. Kiểm thử chức năng

#### 5.1.1. Test Case đăng nhập
| STT | Mô tả | Input | Expected Output | Actual Output | Kết quả |
|-----|-------|-------|-----------------|---------------|---------|
| 1 | Đăng nhập thành công | admin/admin123 | Chuyển đến trang chủ | Chuyển đến index.php | ✅ Pass |
| 2 | Sai mật khẩu | admin/wrong | Thông báo lỗi | Chuyển về login với error | ✅ Pass |
| 3 | Tài khoản không tồn tại | test/test | Thông báo lỗi | Chuyển về login với error | ✅ Pass |

#### 5.1.2. Test Case đăng ký phòng
| STT | Mô tả | Input | Expected Output | Actual Output | Kết quả |
|-----|-------|-------|-----------------|---------------|---------|
| 1 | Đăng ký thành công | Thời gian hợp lệ | Tạo đăng ký mới | Chuyển đến phonghop.php | ✅ Pass |
| 2 | Đăng ký quá khứ | Ngày hôm qua | Thông báo lỗi | Chuyển về form với error | ✅ Pass |
| 3 | Trùng lịch | Giờ đã đặt | Thông báo conflict | Chuyển về form với error | ✅ Pass |

### 5.2. Kiểm thử giao diện
- **Responsive:** Hoạt động tốt trên desktop, tablet, mobile
- **Cross-browser:** Tương thích Chrome, Firefox, Edge
- **Accessibility:** Tuân thủ các tiêu chuẩn web accessibility

### 5.3. Kiểm thử bảo mật
- **SQL Injection:** Sử dụng mysqli_real_escape_string()
- **XSS:** Validate và escape dữ liệu output
- **Session Security:** Kiểm tra quyền truy cập mỗi trang

---

## 6. KẾT QUẢ ĐẠT ĐƯỢC

### 6.1. Chức năng hoàn thành
✅ **Hệ thống xác thực:** Đăng ký, đăng nhập, phân quyền  
✅ **Quản lý phòng:** CRUD phòng họp (Admin)  
✅ **Đăng ký phòng:** Tự động duyệt, kiểm tra conflict  
✅ **Quản lý đăng ký:** Xem, sửa, xóa, từ chối  
✅ **Validation:** Thời gian, dữ liệu, bảo mật  
✅ **Giao diện:** Responsive, thân thiện người dùng  

### 6.2. Điểm mạnh của hệ thống
- **Giao diện đẹp:** Sử dụng Bootstrap, responsive design
- **Logic rõ ràng:** Quy trình đăng ký đơn giản, hiệu quả
- **Bảo mật tốt:** Phân quyền, validation, escape dữ liệu
- **Dễ sử dụng:** UX/UI thân thiện, không cần training
- **Hiệu suất cao:** Code tối ưu, database được index

### 6.3. Hạn chế và hướng phát triển
**Hạn chế hiện tại:**
- Chưa có tính năng thông báo email
- Chưa có báo cáo thống kê chi tiết
- Chưa có API cho mobile app

**Hướng phát triển:**
- Tích hợp email notification
- Thêm dashboard analytics
- Phát triển mobile app
- Tích hợp calendar sync
- Thêm tính năng chat/comment

---

## 7. KẾT LUẬN

### 7.1. Tổng kết
Đồ án "Hệ thống Quản lý Đặt phòng họp" đã được hoàn thành thành công với đầy đủ các chức năng cơ bản và nâng cao. Hệ thống đáp ứng được các yêu cầu đặt ra ban đầu và có thể triển khai thực tế tại Khoa Công nghệ thông tin.

### 7.2. Kiến thức thu được
Qua quá trình thực hiện đồ án, em đã:
- Nắm vững quy trình phát triển web application
- Thành thạo PHP, MySQL, HTML/CSS/JavaScript
- Hiểu rõ về bảo mật web và best practices
- Áp dụng được mô hình MVC trong thực tế
- Phát triển kỹ năng debug và testing

### 7.3. Lời cảm ơn
Em xin chân thành cảm ơn thầy/cô [Tên giảng viên] đã hướng dẫn và hỗ trợ em trong suốt quá trình thực hiện đồ án. Cảm ơn các bạn trong lớp đã góp ý và chia sẻ kinh nghiệm.

---

## PHỤ LỤC

### Phụ lục A: Source Code chính
[Có thể đính kèm các đoạn code quan trọng]

### Phụ lục B: Screenshots giao diện
[Có thể đính kèm ảnh chụp màn hình các trang chính]

### Phụ lục C: Database Schema
[Có thể đính kèm file SQL tạo database]

---

**Ngày hoàn thành:** [Ngày tháng năm]  
**Chữ ký sinh viên:** [Chữ ký]