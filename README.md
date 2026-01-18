# 🏨 FUMiniHotelSystem

**FUMiniHotelSystem** là một ứng dụng máy tính (Desktop Application) quản lý khách sạn mini, được xây dựng trên nền tảng **.NET 8** sử dụng công nghệ **WPF (Windows Presentation Foundation)**. Dự án áp dụng kiến trúc **N-Layer** (Architecture) để đảm bảo tính tổ chức, dễ bảo trì và mở rộng của mã nguồn.



## 📖 Giới thiệu

Hệ thống được thiết kế để phục vụ hai đối tượng người dùng chính: **Quản trị viên (Admin)** và **Khách hàng (Customer)**. Ứng dụng cung cấp các công cụ cần thiết để quản lý quy trình đặt phòng, thông tin khách hàng, và báo cáo doanh thu một cách hiệu quả.

### Kiến trúc dự án
Dự án được chia thành các lớp (layers) riêng biệt:
1.  **WpfApp:** Lớp giao diện người dùng (Presentation Layer).
2.  **Services:** Lớp xử lý nghiệp vụ (Business Logic Layer).
3.  **Repositories:** Lớp trung gian truy cập dữ liệu (Repository Pattern).
4.  **DataAccessObjects (DAO):** Lớp truy cập cơ sở dữ liệu trực tiếp.
5.  **BusinessObjects:** Các thực thể (Entities) và Models.



## 🚀 Tính năng chính

### Dành cho Admin
* **Quản lý Khách hàng:** Xem danh sách, thêm, sửa, xóa thông tin khách hàng. Tìm kiếm khách hàng.
* **Quản lý Phòng:** Quản lý thông tin phòng (Số phòng, Loại phòng, Giá, Trạng thái, Sức chứa).
* **Quản lý Đặt phòng (Booking Reservation):** Tạo mới, chỉnh sửa, xóa và theo dõi các đơn đặt phòng.
* **Báo cáo (Report):** Tạo báo cáo thống kê doanh thu và tình trạng đặt phòng theo khoảng thời gian.

### Dành cho Khách hàng
* **Hồ sơ cá nhân:** Xem và cập nhật thông tin cá nhân.
* **Lịch sử đặt phòng:** Xem lại lịch sử các lần đặt phòng trước đó.
* **Đặt phòng:** Thực hiện tìm kiếm và đặt phòng trống.

## 🛠 Công nghệ sử dụng

| Thành phần | Công nghệ / Thư viện | Phiên bản |
| :--- | :--- | :--- |
| **Framework** | .NET (Core) | 8.0 |
| **Giao diện** | WPF (Windows Presentation Foundation) | - |
| **Ngôn ngữ** | C# | 12.0 |
| **Database** | SQL Server | - |
| **ORM** | Entity Framework Core | 8.0.6 |
| **Cấu hình** | Microsoft.Extensions.Configuration | 8.0.0 |
| **Design Pattern**| Repository, DAO, Singleton | - |

## ⚙️ Cài đặt và Hướng dẫn chạy

Để chạy dự án này trên máy cục bộ, vui lòng làm theo các bước sau:

### 1. Yêu cầu tiên quyết
* [Visual Studio 2022](https://visualstudio.microsoft.com/) (Hỗ trợ .NET 8).
* [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) (LocalDB hoặc bản đầy đủ).
* .NET 8.0 SDK.

### 2. Cấu hình Cơ sở dữ liệu
Dự án sử dụng cơ sở dữ liệu tên là `FUMiniHotelManagement`.

1.  Mở file `WpfApp/appsettings.json`.
2.  Kiểm tra chuỗi kết nối (Connection String) và điều chỉnh `Server`, `User Id`, `Password` cho phù hợp với SQL Server của bạn:
    ```json
    "ConnectionStrings": {
      "FUMiniHotelManagement": "Server=(local);Database=FUMiniHotelManagement;User Id=sa;Password=your_password;Encrypt=False;TrustServerCertificate=True;"
    }
    ```
3.  Chạy script tạo database (nếu có) hoặc sử dụng **Entity Framework Core Migrations** (nếu được hỗ trợ trong dự án này) để khởi tạo cấu trúc bảng.
    * *Lưu ý:* Mã nguồn hiện tại sử dụng `Scaffold-DbContext` (Database First approach), vì vậy bạn cần đảm bảo database `FUMiniHotelManagement` đã tồn tại với các bảng: `Customer`, `RoomInformation`, `RoomType`, `BookingReservation`, `BookingDetail`.

### 3. Chạy ứng dụng
1.  Mở file `FUMiniHotelSystem.sln` bằng Visual Studio.
2.  Đặt **WpfApp** làm **Startup Project** (Chuột phải vào WpfApp -> Set as Startup Project).
3.  Nhấn **F5** hoặc nút **Start** để chạy ứng dụng.

## 🔑 Thông tin đăng nhập mặc định

Để truy cập các quyền quản trị (Admin), sử dụng thông tin được cấu hình trong `appsettings.json`:

* **Email:** `admin@FUMiniHotelSystem.com`
* **Password:** `@@abc123@@`

Đối với tài khoản khách hàng, bạn có thể sử dụng dữ liệu có sẵn trong database hoặc tạo mới qua chức năng Register/Admin.

## 📂 Cấu trúc thư mục

```text
FUMiniHotelSystem/
├── BusinessObjects/       # Các Class Models (Entity)
├── DataAccessObjects/     # Các lớp DAO truy cập DB
├── Repositories/          # Các Interface và Implementation của Repository
├── Services/              # Các Interface và Implementation của Service
├── WpfApp/                # Giao diện người dùng (Windows, Pages, ViewModels)
│   ├── Image/             # Tài nguyên hình ảnh
│   ├── ViewModel/         # ViewModel cho Admin
│   ├── AdminBooking...    # Các cửa sổ chức năng Admin
│   └── appsettings.json   # Cấu hình hệ thống
└── ...
```

---
