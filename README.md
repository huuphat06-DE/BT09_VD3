# HƯỚNG DẪN SPRING BOOT + SECURITY (VD3)

Dự án bài tập ứng dụng Web quản lý User và Product sử dụng Spring Boot 4.1.1 kết hợp với Spring Security 7.x, cung cấp các tính năng xác thực và quản lý tài nguyên.

## 🚀 Công nghệ sử dụng
- **Backend:** Spring Boot 4.1.1
- **Security:** Spring Security 7.1.x
- **Java:** JDK 26 (hoặc JDK 21/17 tùy môi trường)
- **Database:** SQL Server
- **ORM:** Spring Data JPA / Hibernate
- **View:** Thymeleaf
- **Mapper:** MapStruct 1.6.3
- **Email:** Spring Mail
- **Image Cloud:** Cloudinary
- **Validation:** Jakarta Validation
- **Build Tool:** Maven

## 🎯 Chức năng chính
### Authentication
- Đăng ký tài khoản (Register)
- Gửi OTP qua email để xác thực tài khoản
- Xác nhận OTP (Verify OTP)
- Gửi lại OTP (Resend OTP)
- Đăng nhập (Login) lưu phiên làm việc (Session)
- Đăng xuất (Logout)
- Quên mật khẩu (Forgot Password) gửi OTP qua email
- Đổi mật khẩu

### User Management
- CRUD User (Thêm, Sửa, Xóa, Xem danh sách)
- Tìm kiếm User theo Username, Email, Họ tên
- Phân trang danh sách User
- Quản lý Role (USER / ADMIN)
- Thống kê tổng số lượng User
- Thống kê số lượng Product của từng User

### Product Management
- CRUD Product (Thêm, Sửa, Xóa, Xem danh sách)
- Tìm kiếm Product theo tên hoặc mô tả
- Phân trang danh sách Product
- Upload hình ảnh sản phẩm lên Cloudinary
- Liên kết Product thuộc về User nào tạo ra nó
- Thống kê tổng số Product

## ⚙️ Hướng dẫn cài đặt và chạy dự án

### 1. Chuẩn bị cơ sở dữ liệu
- Khởi động SQL Server.
- Tạo một Database trống với tên `webst3`.
- (*Tuỳ chọn*) Sau khi chạy ứng dụng lần đầu (để Hibernate tự tạo bảng), hãy chạy script SQL sau để thêm dữ liệu Role mặc định:
  ```sql
  INSERT INTO roles (name)
  SELECT 'ROLE_USER'
  WHERE NOT EXISTS (SELECT 1 FROM roles WHERE name = 'ROLE_USER');
  
  INSERT INTO roles (name)
  SELECT 'ROLE_ADMIN'
  WHERE NOT EXISTS (SELECT 1 FROM roles WHERE name = 'ROLE_ADMIN');
  ```

### 2. Cấu hình biến môi trường
Mở file `.env` ở thư mục gốc của project và thay đổi các cấu hình cần thiết:
- **DB_USERNAME** / **DB_PASSWORD**: Tài khoản SQL Server của bạn.
- **MAIL_USERNAME** / **MAIL_PASSWORD**: Tài khoản Gmail gửi OTP (Nên sử dụng App Password của Google).
- **Cloudinary**: Nhập `CLOUD_NAME`, `API_KEY`, `API_SECRET` từ tài khoản Cloudinary của bạn.

### 3. Chạy ứng dụng
Mở project bằng IntelliJ IDEA, Eclipse, hoặc Visual Studio Code và tiến hành chạy file `ShopApplication.java`.
- Mặc định ứng dụng sẽ chạy trên port `8080`.
- Truy cập vào: `http://localhost:8080/`
