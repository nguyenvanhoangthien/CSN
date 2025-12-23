# SƠ ĐỒ ERD - HỆ THỐNG QUẢN LÝ ĐẶT PHÒNG HỌP

## 1. Sơ đồ ERD tổng quan

```
┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐
│     USERS       │         │     DANGKY      │         │    PHONGHOP     │
├─────────────────┤         ├─────────────────┤         ├─────────────────┤
│ PK: id          │    1    │ PK: id          │    N    │ PK: id          │
│    username     │ ────────┤ FK: user_id     │ ────────┤    tenphong     │
│    password     │         │ FK: id_phong    │         │    diadiem      │
│    email        │         │    ngaydat      │         │    succhua      │
│    fullname     │         │    ngaysudung   │         │    mota         │
│    role         │         │    giobatdau    │         └─────────────────┘
│    created_at   │         │    gioketthuc   │
│    last_login   │         │    muctieu      │
└─────────────────┘         │    trangthai    │
                            │    created_at   │
                            └─────────────────┘
```

## 2. Mô tả chi tiết các thực thể

### 2.1. Thực thể USERS (Người dùng)
```
┌─────────────────────────────────────────────────────────┐
│                        USERS                            │
├─────────────────────────────────────────────────────────┤
│ Thuộc tính:                                             │
│ • id (PK): Khóa chính, tự tăng                         │
│ • username: Tên đăng nhập (UNIQUE, NOT NULL)           │
│ • password: Mật khẩu đã mã hóa MD5                      │
│ • email: Địa chỉ email                                  │
│ • fullname: Họ tên đầy đủ                              │
│ • role: Vai trò (admin/user)                           │
│ • created_at: Thời gian tạo tài khoản                  │
│ • last_login: Lần đăng nhập cuối                       │
└─────────────────────────────────────────────────────────┘
```

### 2.2. Thực thể PHONGHOP (Phòng họp)
```
┌─────────────────────────────────────────────────────────┐
│                      PHONGHOP                           │
├─────────────────────────────────────────────────────────┤
│ Thuộc tính:                                             │
│ • id (PK): Khóa chính, tự tăng                         │
│ • tenphong: Tên phòng họp                              │
│ • diadiem: Địa điểm phòng                              │
│ • succhua: Sức chứa (số người)                         │
│ • mota: Mô tả chi tiết phòng                           │
└─────────────────────────────────────────────────────────┘
```

### 2.3. Thực thể DANGKY (Đăng ký sử dụng)
```
┌─────────────────────────────────────────────────────────┐
│                       DANGKY                            │
├─────────────────────────────────────────────────────────┤
│ Thuộc tính:                                             │
│ • id (PK): Khóa chính, tự tăng                         │
│ • user_id (FK): Khóa ngoại tham chiếu users.id         │
│ • id_phong (FK): Khóa ngoại tham chiếu phonghop.id     │
│ • ngaydat: Ngày đăng ký                                │
│ • ngaysudung: Ngày sử dụng phòng                       │
│ • giobatdau: Giờ bắt đầu sử dụng                       │
│ • gioketthuc: Giờ kết thúc sử dụng                     │
│ • muctieu: Mục tiêu sử dụng phòng                      │
│ • trangthai: Trạng thái (Đã duyệt/Từ chối)            │
│ • created_at: Thời gian tạo đăng ký                    │
└─────────────────────────────────────────────────────────┘
```

## 3. Mối quan hệ (Relationships)

### 3.1. USERS - DANGKY (1:N)
```
Mối quan hệ: "Một người dùng có thể có nhiều đăng ký"
┌─────────┐ 1     N ┌─────────┐
│  USERS  │ ────────┤ DANGKY  │
└─────────┘         └─────────┘
• Khóa ngoại: dangky.user_id → users.id
• Ràng buộc: ON DELETE CASCADE (Xóa user → xóa tất cả đăng ký)
```

### 3.2. PHONGHOP - DANGKY (1:N)
```
Mối quan hệ: "Một phòng có thể được đăng ký nhiều lần"
┌──────────┐ 1     N ┌─────────┐
│ PHONGHOP │ ────────┤ DANGKY  │
└──────────┘         └─────────┘
• Khóa ngoại: dangky.id_phong → phonghop.id
• Ràng buộc: ON DELETE CASCADE (Xóa phòng → xóa tất cả đăng ký)
```

## 4. Sơ đồ ERD mở rộng với thuộc tính

```
                    ┌─────────────────────────────────┐
                    │            USERS                │
                    ├─────────────────────────────────┤
                    │ • id (PK) INT AUTO_INCREMENT    │
                    │ • username VARCHAR(50) UNIQUE   │
                    │ • password VARCHAR(255)         │
                    │ • email VARCHAR(100)            │
                    │ • fullname VARCHAR(100)         │
                    │ • role ENUM('admin','user')     │
                    │ • created_at TIMESTAMP          │
                    │ • last_login TIMESTAMP          │
                    └─────────────────────────────────┘
                                    │
                                    │ 1
                                    │
                                    │ N
                    ┌─────────────────────────────────┐
                    │           DANGKY                │
                    ├─────────────────────────────────┤
                    │ • id (PK) INT AUTO_INCREMENT    │
                    │ • user_id (FK) INT              │
                    │ • id_phong (FK) INT             │
                    │ • ngaydat DATE                  │
                    │ • ngaysudung DATE               │
                    │ • giobatdau TIME                │
                    │ • gioketthuc TIME               │
                    │ • muctieu TEXT                  │
                    │ • trangthai ENUM                │
                    │ • created_at TIMESTAMP          │
                    └─────────────────────────────────┘
                                    │
                                    │ N
                                    │
                                    │ 1
                    ┌─────────────────────────────────┐
                    │          PHONGHOP               │
                    ├─────────────────────────────────┤
                    │ • id (PK) INT AUTO_INCREMENT    │
                    │ • tenphong VARCHAR(100)         │
                    │ • diadiem VARCHAR(200)          │
                    │ • succhua INT                   │
                    │ • mota TEXT                     │
                    └─────────────────────────────────┘
```

## 5. Ràng buộc toàn vẹn (Integrity Constraints)

### 5.1. Ràng buộc khóa chính (Primary Key)
- `users.id` - Duy nhất, không null
- `phonghop.id` - Duy nhất, không null  
- `dangky.id` - Duy nhất, không null

### 5.2. Ràng buộc khóa ngoại (Foreign Key)
- `dangky.user_id` REFERENCES `users(id)` ON DELETE CASCADE
- `dangky.id_phong` REFERENCES `phonghop(id)` ON DELETE CASCADE

### 5.3. Ràng buộc duy nhất (Unique)
- `users.username` - Tên đăng nhập không trùng lặp

### 5.4. Ràng buộc kiểm tra (Check Constraints)
- `users.role` IN ('admin', 'user')
- `dangky.trangthai` IN ('Đã duyệt', 'Từ chối')
- `dangky.gioketthuc` > `dangky.giobatdau`
- `dangky.ngaysudung` >= `dangky.ngaydat`

### 5.5. Ràng buộc nghiệp vụ (Business Rules)
- Không được đăng ký phòng vào thời gian quá khứ
- Không được đăng ký trùng giờ cho cùng một phòng
- Chỉ admin mới có quyền thêm/sửa/xóa phòng
- User chỉ có thể sửa/xóa đăng ký của mình

## 6. Chỉ mục (Indexes)

```sql
-- Chỉ mục cho tìm kiếm nhanh
CREATE INDEX idx_users_username ON users(username);
CREATE INDEX idx_dangky_user_id ON dangky(user_id);
CREATE INDEX idx_dangky_id_phong ON dangky(id_phong);
CREATE INDEX idx_dangky_ngaysudung ON dangky(ngaysudung);
CREATE INDEX idx_dangky_trangthai ON dangky(trangthai);
```

## 7. Mô tả luồng dữ liệu

```
1. User đăng ký tài khoản → Tạo record trong USERS
2. Admin thêm phòng → Tạo record trong PHONGHOP  
3. User đăng ký phòng → Tạo record trong DANGKY
4. Hệ thống kiểm tra conflict → Query DANGKY theo phòng và thời gian
5. Admin từ chối đăng ký → Update DANGKY.trangthai = 'Từ chối'
```

---

**Ghi chú:** Sơ đồ ERD này mô tả cấu trúc cơ sở dữ liệu của hệ thống quản lý đặt phòng họp với 3 thực thể chính và các mối quan hệ giữa chúng.