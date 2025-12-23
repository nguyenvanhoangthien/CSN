## 3. THỰC HIỆN HÓA NGHIÊN CỨU

### 3.1. Mô tả bài toán

Hiện tại, việc quản lý và đặt phòng họp tại Khoa Công nghệ thông tin - Trường Đại học Trà Vinh đang gặp phải nhiều khó khăn:

**Vấn đề hiện tại:**
- **Quản lý thủ công:** Việc đăng ký sử dụng phòng chủ yếu thông qua giấy tờ hoặc email, dễ thất lạc và khó theo dõi
- **Trùng lịch:** Thường xảy ra tình trạng nhiều người đặt cùng một phòng trong cùng thời gian
- **Thiếu minh bạch:** Không có cách nào để kiểm tra lịch sử dụng phòng một cách nhanh chóng
- **Khó quản lý:** Cán bộ quản lý khó nắm bắt tình hình sử dụng phòng, không thể thống kê hiệu quả
- **Không linh hoạt:** Không thể đăng ký hoặc hủy đăng ký từ xa, phải đến trực tiếp

**Nhu cầu thực tế:**
- Giảng viên cần đặt phòng cho các hoạt động giảng dạy, họp khoa, hội thảo
- Cán bộ quản lý cần theo dõi và kiểm soát việc sử dụng phòng
- Cần hệ thống tự động kiểm tra trùng lịch và thông báo
- Cần giao diện thân thiện, dễ sử dụng trên nhiều thiết bị

**Giải pháp đề xuất:**
Xây dựng hệ thống web quản lý đặt phòng họp với các tính năng:
- Đăng ký/đăng nhập an toàn với phân quyền rõ ràng
- Quản lý thông tin phòng họp (Admin)
- Đăng ký sử dụng phòng với kiểm tra trùng lịch tự động
- Tự động duyệt đăng ký, Admin có quyền từ chối khi cần thiết
- Giao diện responsive, hoạt động trên mọi thiết bị

### 3.2. Đặc tả yêu cầu hệ thống

#### 3.2.1. Yêu cầu chức năng

**RF-01: Quản lý người dùng**
- RF-01.1: Đăng ký tài khoản mới với thông tin: username, password, email, fullname
- RF-01.2: Đăng nhập hệ thống với username/password
- RF-01.3: Đăng xuất an toàn và xóa session
- RF-01.4: Xem và cập nhật thông tin cá nhân
- RF-01.5: Phân quyền người dùng: Admin và User (Giảng viên)

**RF-02: Quản lý phòng họp (Chỉ Admin)**
- RF-02.1: Thêm phòng họp mới với thông tin: tên phòng, địa điểm, sức chứa, mô tả
- RF-02.2: Xem danh sách tất cả phòng họp
- RF-02.3: Sửa thông tin phòng họp
- RF-02.4: Xóa phòng họp (khi không còn sử dụng)

**RF-03: Quản lý đăng ký sử dụng phòng**
- RF-03.1: Xem danh sách phòng có sẵn
- RF-03.2: Đăng ký sử dụng phòng với thông tin: phòng, ngày sử dụng, giờ bắt đầu/kết thúc, mục tiêu
- RF-03.3: Kiểm tra trùng lịch tự động trước khi lưu
- RF-03.4: Tự động duyệt đăng ký (trạng thái "Đã duyệt")
- RF-03.5: Xem lịch sử đăng ký của bản thân
- RF-03.6: Sửa/hủy đăng ký của mình

**RF-04: Quản lý duyệt đăng ký (Chỉ Admin)**
- RF-04.1: Xem tất cả đăng ký trong hệ thống
- RF-04.2: Từ chối đăng ký khi cần sử dụng phòng cho mục đích khác
- RF-04.3: Sửa/xóa bất kỳ đăng ký nào trong hệ thống

**RF-05: Validation và bảo mật**
- RF-05.1: Kiểm tra thời gian đăng ký phải là tương lai (không cho phép đăng ký quá khứ)
- RF-05.2: Validation dữ liệu đầu vào (required fields, format)
- RF-05.3: Mã hóa mật khẩu bằng MD5
- RF-05.4: Quản lý session và timeout

#### 3.2.2. Yêu cầu phi chức năng

**NRF-01: Hiệu suất (Performance)**
- Thời gian phản hồi trang web < 3 giây
- Hỗ trợ đồng thời tối thiểu 20 người dùng
- Database query được tối ưu với index
- Kích thước trang < 2MB

**NRF-02: Khả năng sử dụng (Usability)**
- Giao diện trực quan, dễ hiểu cho người dùng không chuyên
- Responsive design hoạt động tốt trên desktop, tablet, mobile
- Thông báo lỗi rõ ràng, hướng dẫn người dùng
- Không cần training phức tạp

**NRF-03: Tương thích (Compatibility)**
- Hoạt động trên các trình duyệt: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- Tương thích với PHP 7.4+ và MySQL 8.0+
- Responsive trên các độ phân giải: 320px - 1920px

**NRF-04: Bảo mật (Security)**
- Mã hóa mật khẩu trước khi lưu database
- Validation input để tránh SQL Injection và XSS
- Session timeout sau 30 phút không hoạt động
- Phân quyền truy cập rõ ràng

**NRF-05: Khả năng bảo trì (Maintainability)**
- Code có cấu trúc rõ ràng theo mô hình MVC
- Comment đầy đủ cho các function quan trọng
- Naming convention nhất quán
- Dễ dàng thêm tính năng mới

### 3.3. Thiết kế dữ liệu

Hệ thống sử dụng cơ sở dữ liệu quan hệ MySQL với 3 bảng chính được thiết kế để đảm bảo tính toàn vẹn và hiệu suất:

**Nguyên tắc thiết kế:**
- Tuân thủ chuẩn hóa database đến dạng chuẩn 3NF
- Sử dụng khóa chính tự tăng (AUTO_INCREMENT) cho mỗi bảng
- Thiết lập khóa ngoại để đảm bảo tính tham chiếu
- Sử dụng ENUM cho các trường có giá trị cố định
- Đặt index cho các trường thường xuyên tìm kiếm

**Cấu trúc database:**
```sql
CREATE DATABASE room_booking_system 
CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

### 3.4. Mô hình dữ liệu

#### 3.4.1. Danh sách các thực thể và mối kết hợp

**Các thực thể chính:**

1. **USERS (Người dùng)**
   - Lưu trữ thông tin tài khoản người dùng
   - Phân quyền Admin và User
   - Quản lý thông tin cá nhân

2. **PHONGHOP (Phòng họp)**
   - Lưu trữ thông tin các phòng họp
   - Thông tin vật lý: tên, địa điểm, sức chứa
   - Mô tả trang thiết bị

3. **DANGKY (Đăng ký sử dụng)**
   - Lưu trữ lịch đăng ký sử dụng phòng
   - Liên kết giữa người dùng và phòng họp
   - Quản lý thời gian và trạng thái

**Các mối kết hợp:**

1. **USERS - DANGKY (1:N)**
   - Một người dùng có thể có nhiều đăng ký
   - Mỗi đăng ký thuộc về một người dùng duy nhất
   - Khóa ngoại: dangky.user_id → users.id

2. **PHONGHOP - DANGKY (1:N)**
   - Một phòng có thể được đăng ký nhiều lần
   - Mỗi đăng ký chỉ liên quan đến một phòng
   - Khóa ngoại: dangky.id_phong → phonghop.id

#### 3.4.2. Chi tiết các thực thể và mối kết hợp

**Thực thể USERS:**
```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    email VARCHAR(100),
    fullname VARCHAR(100),
    role ENUM('admin', 'user') DEFAULT 'user',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_login TIMESTAMP NULL,
    
    -- Indexes
    INDEX idx_username (username),
    INDEX idx_role (role)
);
```

**Thuộc tính:**
- `id`: Khóa chính, tự tăng
- `username`: Tên đăng nhập, duy nhất, không null
- `password`: Mật khẩu đã mã hóa MD5
- `email`: Địa chỉ email (tùy chọn)
- `fullname`: Họ tên đầy đủ
- `role`: Vai trò (admin/user), mặc định là user
- `created_at`: Thời gian tạo tài khoản
- `last_login`: Lần đăng nhập cuối

**Thực thể PHONGHOP:**
```sql
CREATE TABLE phonghop (
    id INT PRIMARY KEY AUTO_INCREMENT,
    tenphong VARCHAR(100) NOT NULL,
    diadiem VARCHAR(200),
    succhua INT DEFAULT 0,
    mota TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    -- Indexes
    INDEX idx_tenphong (tenphong)
);
```

**Thuộc tính:**
- `id`: Khóa chính, tự tăng
- `tenphong`: Tên phòng họp, không null
- `diadiem`: Địa điểm phòng (tầng, tòa nhà)
- `succhua`: Sức chứa (số người), mặc định 0
- `mota`: Mô tả chi tiết về phòng và trang thiết bị
- `created_at`: Thời gian thêm phòng vào hệ thống

**Thực thể DANGKY:**
```sql
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
    
    -- Foreign Keys
    FOREIGN KEY (id_phong) REFERENCES phonghop(id) ON DELETE CASCADE,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
    
    -- Indexes
    INDEX idx_ngaysudung (ngaysudung),
    INDEX idx_trangthai (trangthai),
    INDEX idx_user_booking (user_id, ngaysudung),
    INDEX idx_room_booking (id_phong, ngaysudung)
);
```

**Thuộc tính:**
- `id`: Khóa chính, tự tăng
- `id_phong`: Khóa ngoại tham chiếu phonghop.id
- `user_id`: Khóa ngoại tham chiếu users.id
- `ngaydat`: Ngày thực hiện đăng ký
- `ngaysudung`: Ngày dự kiến sử dụng phòng
- `giobatdau`: Giờ bắt đầu sử dụng
- `gioketthuc`: Giờ kết thúc sử dụng
- `muctieu`: Mục tiêu/lý do sử dụng phòng
- `trangthai`: Trạng thái đăng ký (Đã duyệt/Từ chối)
- `created_at`: Thời gian tạo đăng ký

**Ràng buộc toàn vẹn:**
- Primary Key: Mỗi bảng có khóa chính duy nhất
- Foreign Key: Đảm bảo tính tham chiếu với CASCADE DELETE
- Unique: username không trùng lặp
- Check: gioketthuc > giobatdau (được validate ở application layer)
- Not Null: Các trường quan trọng không được để trống

### 3.5. Thiết kế xử lý

Hệ thống được thiết kế theo mô hình MVC với các module xử lý chính dựa trên cấu trúc file thực tế của dự án:

**Module Authentication (Xác thực):**
- `login.php`: Xử lý đăng nhập, tạo session
- `register.php`: Xử lý đăng ký tài khoản mới
- `logout.php`: Xóa session và đăng xuất
- `check_admin.php`: Kiểm tra quyền admin

**Module Room Management (Quản lý phòng - Admin):**
- `lietke.php`: Hiển thị danh sách phòng với chức năng CRUD
- `datphong.php`: Xử lý thêm phòng mới
- `edit.php`: Form sửa thông tin phòng
- `update.php`: Xử lý cập nhật phòng
- `xoa.php`: Xử lý xóa phòng

**Module Booking Management (Quản lý đăng ký):**
- `dangkyphong.php`: Form đăng ký sử dụng phòng
- `xulyDangky.php`: Xử lý đăng ký mới (kiểm tra trùng lịch, validation)
- `phonghop.php`: Hiển thị lịch sử đăng ký
- `edit_dangky.php`: Form sửa đăng ký
- `update_dangky.php`: Xử lý cập nhật đăng ký
- `xoa_dangky.php`: Xử lý xóa đăng ký
- `duyet_dangky.php`: Xử lý từ chối đăng ký (Admin)

**Module Core:**
- `index.php`: Trang chủ sau khi đăng nhập
- `profile.php`: Quản lý thông tin cá nhân
- `ketnoi.php`: Kết nối cơ sở dữ liệu
- `style.css`: Styling và responsive design

**Luồng xử lý chính:**

1. **Đăng ký phòng:**
```
User → dangkyphong.php (form) → xulyDangky.php → 
Validation → Check conflict → Save to DB → Redirect to phonghop.php
```

2. **Kiểm tra trùng lịch:**
```sql
SELECT * FROM dangky 
WHERE id_phong = ? 
AND ngaysudung = ? 
AND trangthai = 'Đã duyệt'
AND (giobatdau < ? AND gioketthuc > ?)
```

3. **Validation thời gian:**
- Client-side: JavaScript trong `dangkyphong.php` và `edit_dangky.php`
- Server-side: PHP trong `xulyDangky.php` và `update_dangky.php`

### 3.6. Thiết kế giao diện

**Nguyên tắc thiết kế UI/UX:**
- **Mobile-first approach:** Thiết kế ưu tiên cho mobile, sau đó mở rộng lên desktop
- **Responsive design:** Sử dụng Bootstrap Grid System
- **Consistent branding:** Màu sắc và typography nhất quán với thương hiệu trường
- **User-friendly:** Giao diện trực quan, dễ sử dụng

**Hệ thống màu sắc:**
- **Primary Color:** #03487c (Navy Blue) - Màu chủ đạo của trường
- **Secondary Color:** #f9a602 (Orange) - Màu nhấn
- **Background:** #f5f7fa (Light Gray) - Nền trang
- **Text:** #333333 (Dark Gray) - Màu chữ chính
- **Success:** #28a745 (Green) - Thông báo thành công
- **Warning:** #ffc107 (Yellow) - Cảnh báo
- **Danger:** #dc3545 (Red) - Lỗi

**Typography:**
- **Font Family:** Arial, sans-serif
- **Heading:** Font-weight bold, sizes từ h1 (2rem) đến h6 (1rem)
- **Body Text:** Font-size 14px, line-height 1.5
- **Small Text:** Font-size 12px cho caption và note

**Layout Structure:**
```
┌─────────────────────────────────────────────────────────┐
│  HEADER: Logo + Title + Navigation Menu                 │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  MAIN CONTENT AREA                                      │
│  - Page Title                                           │
│  - Content Body                                         │
│  - Action Buttons                                       │
│                                                         │
├─────────────────────────────────────────────────────────┤
│  FOOTER: Contact Info + Copyright                       │
└─────────────────────────────────────────────────────────┘
```

**Responsive Breakpoints:**
- **Mobile:** < 576px
- **Tablet:** 576px - 768px
- **Desktop:** 768px - 992px
- **Large Desktop:** > 992px

**Component Design:**

1. **Navigation Menu:**
   - Horizontal menu trên desktop
   - Dropdown menu cho user actions
   - Active state cho trang hiện tại

2. **Forms:**
   - Bootstrap form styling
   - Validation states (success/error)
   - Required field indicators
   - Date/time pickers cho đăng ký phòng

3. **Tables:**
   - Responsive table với horizontal scroll
   - Striped rows cho dễ đọc
   - Action buttons trong cột cuối
   - Badge cho trạng thái đăng ký

4. **Buttons:**
   - Primary: Hành động chính (Đăng ký, Lưu)
   - Secondary: Hành động phụ (Hủy, Quay lại)
   - Success: Xác nhận (Duyệt)
   - Warning: Cảnh báo (Từ chối)
   - Danger: Xóa

**Tính năng UX đặc biệt:**
- Chuyển hướng tự động sau thao tác (không cần click OK)
- Real-time validation cho form đăng ký
- Loading states và feedback
- Error handling thân thiện với người dùng

### 3.7. Kết chương

Chương 3 đã trình bày chi tiết quá trình thực hiện hóa nghiên cứu cho hệ thống quản lý đặt phòng họp, bao gồm:

**Những công việc đã hoàn thành:**
- Phân tích bài toán và xác định yêu cầu hệ thống một cách chi tiết và cụ thể
- Thiết kế cơ sở dữ liệu với 3 thực thể chính và các mối quan hệ được chuẩn hóa
- Xây dựng kiến trúc hệ thống theo mô hình MVC phù hợp với quy mô dự án
- Thiết kế giao diện người dùng responsive và thân thiện
- Triển khai đầy đủ các module chức năng theo yêu cầu đã đặt ra

**Kết quả đạt được:**
- Hệ thống đáp ứng đầy đủ 5 nhóm yêu cầu chức năng và 5 yêu cầu phi chức năng
- Database được thiết kế tối ưu với các ràng buộc toàn vẹn và index phù hợp
- Giao diện responsive hoạt động tốt trên desktop, tablet và mobile
- Code có cấu trúc rõ ràng theo MVC, dễ bảo trì và mở rộng
- Các tính năng đặc biệt: kiểm tra trùng lịch, validation thời gian, tự động duyệt

**Đóng góp của nghiên cứu:**
- Giải quyết triệt để vấn đề quản lý phòng họp thủ công tại Khoa CNTT
- Tạo ra quy trình đăng ký tự động, minh bạch và hiệu quả
- Cung cấp công cụ quản lý hiện đại cho cán bộ và giảng viên
- Làm cơ sở để phát triển các hệ thống quản lý khác trong trường
- Thể hiện khả năng ứng dụng công nghệ web vào giải quyết bài toán thực tế

**Tính khả thi và khả năng mở rộng:**
Hệ thống đã sẵn sàng để triển khai thực tế với chi phí thấp và có thể mở rộng thêm các tính năng như:
- Thông báo email tự động
- Báo cáo thống kê sử dụng phòng
- Tích hợp với hệ thống quản lý khác của trường
- API cho ứng dụng mobile
- Tính năng đặt phòng định kỳ

Kết quả nghiên cứu cho thấy việc áp dụng công nghệ web trong quản lý tài nguyên giáo dục mang lại hiệu quả cao và có thể nhân rộng cho các đơn vị khác.