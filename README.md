# Hệ thống Quản lý Đặt phòng họp - Khoa CNTT

## Cấu trúc dự án

### 📁 Files chính

#### Trang chính
- **index.php** - Trang chủ (sau khi đăng nhập)
- **login.html / login.php** - Đăng nhập
- **register.html / register.php** - Đăng ký tài khoản
- **profile.php** - Thông tin cá nhân
- **logout.php** - Đăng xuất

#### Quản lý phòng (Admin)
- **lietke.php** - Danh sách phòng họp (Quản lý phòng)
- **datphong.html / datphong.php** - Thêm phòng mới
- **edit.php** - Form sửa thông tin phòng
- **update.php** - Xử lý cập nhật phòng
- **xoa.php** - Xóa phòng

#### Lịch sử dụng phòng
- **phonghop.php** - Danh sách đăng ký sử dụng phòng (Lịch sử dụng)
- **dangkyphong.php** - Form đăng ký sử dụng phòng
- **edit_dangky.php** - Form sửa đăng ký
- **update_dangky.php** - Xử lý cập nhật đăng ký
- **xoa_dangky.php** - Xóa đăng ký
- **xulyDangky.php** - Xử lý thêm đăng ký mới
- **duyet_dangky.php** - Duyệt/Từ chối đăng ký (Admin)

#### Hệ thống
- **ketnoi.php** - Kết nối database
- **check_admin.php** - Kiểm tra quyền admin
- **style.css** - Giao diện

### 🗄️ Database

#### Bảng users
- Quản lý tài khoản người dùng
- Trường: id, username, password, email, fullname, role, created_at, last_login

#### Bảng phonghop
- Quản lý thông tin phòng họp
- Trường: id, tenphong, diadiem, succhua, mota

#### Bảng dangky
- Quản lý lịch đăng ký sử dụng phòng
- Trường: id, id_phong, user_id, ngaydat, ngaysudung, giobatdau, gioketthuc, muctieu, trangthai, created_at

### 👥 Phân quyền

#### Admin
- Quản lý phòng: Thêm/Sửa/Xóa phòng
- Duyệt đăng ký: Duyệt/Từ chối đăng ký sử dụng phòng
- Xem tất cả lịch đăng ký
- Sửa/Xóa tất cả đăng ký

#### User (Teacher)
- Đăng ký sử dụng phòng
- Xem lịch sử dụng phòng
- Sửa/Xóa đăng ký của mình (khi chờ duyệt)

### 🔐 Tài khoản mặc định
- Username: admin
- Password: admin123
- Role: admin

### 📝 Ghi chú
- Hệ thống kiểm tra trùng giờ khi đăng ký
- Đăng ký phải được admin duyệt mới có hiệu lực
- Mật khẩu được mã hóa MD5
