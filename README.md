# README.md - Hệ Thống Quản Lý Nhân Sự (HRM) Cho Doanh Nghiệp Bán Mỹ Phẩm

> **Đồ án môn học:** Phát triển ứng dụng & Hệ thống thông tin  
> **Tên dự án:** Hệ thống Quản lý Nhân sự (HRM)  
> **Repository:** `[Đường dẫn repo]`

---

## 📋 Mục lục
1. [Giới thiệu dự án](#1-giới-thiệu-dự-án)
2. [Tính năng chính](#2-tính-năng-chính)
3. [Công nghệ sử dụng](#3-công-nghệ-sử-dụng)
4. [Kiến trúc hệ thống](#4-kiến-trúc-hệ-thống)
5. [Cấu trúc thư mục dự án](#5-cấu-trúc-thư-mục-dự-án)
6. [Cơ sở dữ liệu](#6-cơ-sở-dữ-liệu)
7. [Cấu hình môi trường](#7-cấu-hình-môi-trường)
8. [Cài đặt & Chạy dự án](#8-cài-đặt--chạy-dự-án)
9. [API Documentation (Tóm tắt)](#9-api-documentation-tóm-tắt)
10. [Kịch bản kiểm thử (Test Cases)](#10-kịch-bản-kiểm-thử-test-cases)
11. [Hướng phát triển tương lai](#11-hướng-phát-triển-tương-lai)
12. [Tác giả & Phân công công việc](#12-tác-giả--phân-công-công-việc)
13. [Lời cảm ơn](#13-lời-cảm-ơn)

---

## 1. Giới thiệu dự án

**Hệ thống Quản lý Nhân sự (HRM)** là giải pháp phần mềm toàn diện được thiết kế chuyên biệt cho công tác quản trị nhân sự tại doanh nghiệp bán mỹ phẩm. Dự án tập trung giải quyết các bài toán về quản lý hồ sơ nhân viên, quy trình xin/duyệt nghỉ phép, chấm công, tính lương và phân quyền hạn ngạch chức danh.

Dự án gồm 2 nền tảng tương tác chính:
- **Web Admin (Quản trị viên / Phòng Nhân sự):** Quản lý toàn bộ vòng đời nhân sự, thiết lập chính sách lương thưởng, duyệt đơn từ và trích xuất báo cáo thống kê.
- **Mobile App (Nhân viên):** Ứng dụng di động giúp nhân viên tra cứu hồ sơ cá nhân, gửi các loại đơn từ nghỉ phép và theo dõi, xuất file bảng lương định kỳ.

---

## 2. Tính năng chính

### 2.1. Web Admin – Dành cho Người quản lý (20 điểm)
* **Quản lý Nhân sự:**
  * Thêm mới nhân sự vào hệ thống (thông tin cá nhân, hợp đồng, phòng ban, vị trí).
  * Xóa / Ngừng hoạt động hồ sơ nhân sự.
* **Duyệt đơn từ:**
  * Tiếp nhận và xử lý (Phê duyệt / Từ chối) các đơn xin nghỉ phép, nghỉ việc từ nhân viên gửi lên.
* **Báo cáo & Thống kê:**
  * **Thống kê tình hình biến động nhân sự theo tháng:** Tỷ lệ nhân sự đang làm việc, đang nghỉ phép, nghỉ thai sản, nghỉ việc.
  * **Thống kê chỉ số nhân sự:** Trình độ học vấn, các mức dải lương, thâm niên công tác.
* **Cấp quyền & Quản lý vai trò (RBAC):**
  * Thiết lập và điều chỉnh phân quyền cho nhân viên (Ví dụ: Nhân viên bán hàng, Trưởng nhóm/Trưởng cửa hàng, Chuyên viên HR, Admin).
  * Tự động thay đổi hạn mức quyền hạn khi nhân sự được thăng chức hoặc điều chuyển.
* **Chấm công & Tính lương:**
  * Quản lý dữ liệu chấm công hàng ngày của toàn bộ nhân viên.
  * Thực hiện chốt công, tính lương tự động theo công thức, thưởng/phạt và xuất bảng lương tổng hợp.

### 2.2. Mobile App – Dành cho Nhân viên (10 điểm)
* **Hồ sơ cá nhân:**
  * Xem thông tin chi tiết hồ sơ nhân sự của chính mình.
  * Cập nhật, chỉnh sửa các thông tin cá nhân cơ bản (Số điện thoại, địa chỉ, ảnh đại diện, liên hệ khẩn cấp).
* **Nộp đơn từ trực tuyến:**
  * Tạo và gửi đơn xin nghỉ phép (nghỉ phép năm, nghỉ ốm đau, nghỉ thai sản, nghỉ không lương).
  * Tạo và gửi đơn xin nghỉ việc.
  * Theo dõi trạng thái duyệt đơn theo thời gian thực.
* **Tra cứu & In Bảng lương:**
  * Xem giải trình cách tính lương chi tiết (Lương cơ bản, phụ cấp, ngày công thực tế, khoản trừ BHXH/BHYT/Thuế).
  * Xem tổng quan bảng lương từng tháng.
  * **In/Xuất file bảng lương theo tháng** dưới dạng PDF.
  * **In/Xuất file tổng hợp bảng lương theo năm** để phục vụ quyết toán cá nhân.

---

## 3. Công nghệ sử dụng

Hệ thống ưu tiên sử dụng các công nghệ phổ biến, hoạt động ổn định và dễ dàng triển khai:

* **Backend:** Node.js (NestJS / Express) hoặc Java Spring Boot.
* **Web Admin:** ReactJS kết hợp thư viện giao diện Ant Design (AntD).
* **Mobile App:** Flutter (Cross-platform cho iOS và Android).
* **Database:** MySQL (Hệ quản trị cơ sở dữ liệu quan hệ).
* **Authentication & Authorization:** JSON Web Token (JWT) + Role-Based Access Control (RBAC).
* **PDF Export Utility:** PDFKit / JasperReports / PDFBox để tạo xuất bảng lương PDF.

---

## 4. Kiến trúc hệ thống

Hệ thống được thiết kế theo **Mô hình 3 lớp (3-Tier Architecture)** phân tách rõ ràng giữa giao diện, xử lý nghiệp vụ và lưu trữ dữ liệu.

```
+---------------------------------+       +---------------------------------+
|      Web Admin (ReactJS)        |       |       Mobile App (Flutter)      |
|    (Dành cho Quản lý/HR)        |       |      (Dành cho Nhân viên)       |
+---------------------------------+       +---------------------------------+
                 \                                 /
                  \                               /
                   v                             v
+---------------------------------------------------------------------------+
|                          RESTful API Gateway                              |
|                   (JWT Auth & Middleware RBAC Check)                      |
+---------------------------------------------------------------------------+
|                          Backend Service                                  |
|               (Spring Boot / Node.js Express / NestJS)                    |
|  [Auth Module]  [Employee Module]  [Leave Module]  [Payroll Module]        |
+---------------------------------------------------------------------------+
                                     |
                                     v
+---------------------------------------------------------------------------+
|                          Database Layer                                   |
|                             (MySQL)                                       |
+---------------------------------------------------------------------------+
```

### Phân quyền người dùng (Role Hierarchy)
* **ADMIN:** Toàn quyền cấu hình hệ thống, quản lý tài khoản và phân quyền.
* **HR_MANAGER:** Thêm/xóa nhân viên, duyệt đơn, chốt công, tính lương, xem báo cáo thống kê.
* **TEAM_LEAD:** Duyệt đơn nghỉ phép cấp 1, xem thông tin nhóm.
* **EMPLOYEE:** Xem/sửa thông tin cá nhân, gửi đơn xin nghỉ/nghỉ việc, xem và in bảng lương.

---

## 5. Cấu trúc thư mục dự án

```text
[Tên dự án]-hrm/
├── backend/                  # Mã nguồn Backend (Spring Boot / Node.js)
│   ├── src/
│   │   ├── controllers/      # Tiếp nhận và xử lý request
│   │   ├── services/         # Xử lý logic nghiệp vụ HRM
│   │   ├── repositories/     # Tương tác cơ sở dữ liệu
│   │   ├── models/           # Định nghĩa Entities / DTOs
│   │   ├── security/         # Cấu hình JWT, RBAC filter
│   │   └── utils/            # Helper tính lương, xuất PDF
│   ├── application.properties# Cấu hình môi trường backend
│   └── pom.xml / package.json
├── web-admin/                # Mã nguồn Web Admin (ReactJS + Ant Design)
│   ├── src/
│   │   ├── components/       # Các UI Component dùng chung
│   │   ├── pages/            # Các màn hình (Nhân sự, Duyệt đơn, Báo cáo, Lương)
│   │   ├── services/         # Gọi API Backend (Axios)
│   │   └── store/            # Quản lý trạng thái ứng dụng (Redux / Context)
│   └── package.json
├── mobile-app/               # Mã nguồn Mobile App (Flutter)
│   ├── lib/
│   │   ├── models/           # Data models
│   │   ├── views/            # Màn hình Mobile (Hồ sơ, Đơn từ, Bảng lương)
│   │   ├── controllers/      # Quản lý logic màn hình
│   │   └── services/         # Kết nối API RESTful
│   └── pubspec.yaml
├── database/                 # Script cơ sở dữ liệu
│   ├── schema.sql            # Script khởi tạo bảng
│   └── init_data.sql         # Dữ liệu mẫu (Tài khoản, Phòng ban, Chức danh)
└── docs/                     # Tài liệu thiết kế, API spec, Báo cáo đồ án
    └── api-spec.json
```

---

## 6. Cơ sở dữ liệu

Hệ thống HRM sử dụng 9 bảng dữ liệu quan hệ cốt lõi:

1. **`Users`**: Lưu trữ thông tin tài khoản đăng nhập (Username, Password Hashed, Status).
2. **`Roles`**: Danh mục vai trò trong hệ thống (ADMIN, HR_MANAGER, TEAM_LEAD, EMPLOYEE).
3. **`User_Roles`**: Bảng liên kết phân quyền n-n giữa Users và Roles.
4. **`Employees`**: Hồ sơ chi tiết nhân viên (Mã NV, Họ tên, Ngày sinh, CCCD, Email, SĐT, Địa chỉ, Ngày vào làm).
5. **`Departments`**: Danh mục phòng ban / cửa hàng mỹ phẩm.
6. **`Positions`**: Danh mục vị trí / chức danh công việc (Nhân viên tư vấn, Trưởng cửa hàng, HR Specialist,...).
7. **`Contracts`**: Hợp đồng lao động (Loại hợp đồng, Mức lương thỏa thuận, Phụ cấp, Ngày bắt đầu, Ngày kết thúc).
8. **`Attendances`**: Dữ liệu chấm công (Ngày, Giờ vào, Giờ ra, Số công ghi nhận, Trạng thái đi trễ/về sớm).
9. **`LeaveRequests`**: Quản lý đơn từ (Loại đơn: Nghỉ phép/Nghỉ ốm thai sản/Nghỉ việc, Lý do, Ngày bắt đầu, Ngày kết thúc, Trạng thái duyệt).
10. **`Payrolls`**: Bảng lương chi tiết theo tháng/năm (Tháng/Năm, Lương cơ bản, Số công, Khấu trừ, Thưởng, Lương thực nhận, Trạng thái thanh toán).

---

## 7. Cấu hình môi trường

Tạo file `.env` (hoặc cấu hình trong `application.properties`) tại thư mục `backend/` với các biến môi trường chuẩn sau:

| Biến môi trường | Mô tả | Giá trị mẫu |
| :--- | :--- | :--- |
| `SERVER_PORT` | Cổng dịch vụ Backend | `8080` |
| `DB_HOST` | Địa chỉ Server Database | `localhost` |
| `DB_PORT` | Cổng kết nối MySQL | `3306` |
| `DB_NAME` | Tên Cơ sở dữ liệu | `hrm_cosmetics_db` |
| `DB_USER` | Tài khoản kết nối DB | `[Username]` |
| `DB_PASS` | Mật khẩu kết nối DB | `[Password]` |
| `JWT_SECRET` | Mã khóa bí mật ký Token JWT | `super_secret_key_hrm_2026_xyz` |
| `JWT_EXPIRATION` | Thời gian hết hạn Token (ms) | `86400000` |
| `API_URL` | URL Endpoint cho ứng dụng client | `http://localhost:8080/api` |

---

## 8. Cài đặt & Chạy dự án

### Step 1: Khởi tạo Cơ sở dữ liệu MySQL
1. Mở MySQL Workbench hoặc CLI.
2. Tạo database mới: `CREATE DATABASE hrm_cosmetics_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;`
3. Thực thi file script SQL:
   ```bash
   mysql -u [Username] -p hrm_cosmetics_db < database/schema.sql
   mysql -u [Username] -p hrm_cosmetics_db < database/init_data.sql
   ```

### Step 2: Chạy Backend Service
```bash
cd backend
# Nếu dùng Node.js
npm install
npm run start:dev

# Nếu dùng Java Spring Boot
./mvnw spring-boot:run
```

### Step 3: Chạy Web Admin (ReactJS)
```bash
cd web-admin
npm install
npm start
# Ứng dụng sẽ chạy tại http://localhost:3000
```

### Step 4: Chạy Mobile App (Flutter)
```bash
cd mobile-app
flutter pub get
flutter run
```

### Tài khoản trải nghiệm mặc định (Test Accounts):

| Vai trò | Username | Password | Quyền truy cập |
| :--- | :--- | :--- | :--- |
| **Admin** | `admin_hrm` | `[Password]` | Web Admin (Toàn quyền) |
| **HR Manager** | `hr_manager` | `[Password]` | Web Admin (Quản lý hồ sơ, lương, duyệt đơn) |
| **Trưởng nhóm** | `team_lead` | `[Password]` | Web Admin / Mobile App |
| **Nhân viên** | `employee01` | `[Password]` | Mobile App (Xem lương, nộp đơn) |

---

## 9. API Documentation (Tóm tắt)

### Auth Endpoints (`/api/auth`)
* `POST /api/auth/login`: Đăng nhập lấy Bearer JWT Token.
* `GET /api/auth/profile`: Lấy thông tin tài khoản đang đăng nhập.

### Employees Endpoints (`/api/employees`)
* `GET /api/employees`: Lấy danh sách nhân viên (Phân trang, lọc theo phòng ban).
* `POST /api/employees`: Thêm mới hồ sơ nhân viên [Chỉ Admin/HR].
* `PUT /api/employees/{id}`: Cập nhật thông tin nhân viên.
* `DELETE /api/employees/{id}`: Ngừng hoạt động / Xóa nhân viên [Chỉ Admin/HR].

### Leave Requests Endpoints (`/api/leaves`)
* `POST /api/leaves`: Gửi đơn xin nghỉ phép / nghỉ việc [Nhân viên].
* `GET /api/leaves/my-requests`: Xem danh sách đơn từ của bản thân [Nhân viên].
* `GET /api/leaves/pending`: Lấy danh sách đơn chờ duyệt [Chỉ Manager/HR].
* `PUT /api/leaves/{id}/status`: Phê duyệt hoặc từ chối đơn [Chỉ Manager/HR].

### Payrolls Endpoints (`/api/payrolls`)
* `POST /api/payrolls/calculate`: Tính toán và chốt lương tháng [Chỉ HR].
* `GET /api/payrolls/my-payroll`: Xem chi tiết bảng lương cá nhân [Nhân viên].
* `GET /api/payrolls/my-payroll/export-monthly`: In/xem bảng lương tháng dạng PDF [Nhân viên].
* `GET /api/payrolls/my-payroll/export-yearly`: In/xem bảng tổng hợp lương năm dạng PDF [Nhân viên].

### Roles & Permissions Endpoints (`/api/roles`)
* `GET /api/roles`: Danh sách các vai trò hệ thống.
* `PUT /api/roles/assign`: Cấp/điều chỉnh vai trò và quyền hạn cho nhân sự [Chỉ Admin].

---

## 10. Kịch bản kiểm thử (Test Cases)

| STT | Tên Test Case | Bước thực hiện | Kết quả kỳ vọng |
| :---: | :--- | :--- | :--- |
| **TC01** | **Đăng nhập & Phân quyền** | 1. Đăng nhập với tài khoản `employee01`.<br>2. Thử truy cập API Admin `/api/employees/create`. | Hệ thống từ chối truy cập, trả về HTTP Status Code `403 Forbidden`. |
| **TC02** | **Thêm mới Nhân viên** | 1. Đăng nhập tài khoản HR trên Web Admin.<br>2. Nhập đầy đủ thông tin nhân viên mới.<br>3. Bấm "Lưu". | Nhân viên mới được tạo thành công trong DB, hiển thị trên danh sách. |
| **TC03** | **Gửi & Duyệt đơn xin nghỉ** | 1. Nhân viên gửi đơn xin nghỉ phép trên Mobile App.<br>2. HR đăng nhập Web Admin vào mục "Duyệt đơn".<br>3. Chọn "Phê duyệt". | Trạng thái đơn chuyển sang `APPROVED`, số ngày phép tồn của nhân viên tự động trừ đi. |
| **TC04** | **Tính lương & In bảng lương** | 1. HR thực hiện tính lương tháng trên Web Admin.<br>2. Nhân viên mở Mobile App vào mục "Bảng lương".<br>3. Chọn "In bảng lương tháng". | File PDF bảng lương được tạo ra chuẩn cấu trúc, hiển thị đầy đủ chi tiết lương và khoản trừ. |

---

## 11. Hướng phát triển tương lai

Các định hướng nâng cấp chuyên sâu cho hệ thống HRM (Thuần túy mảng quản trị nhân sự):

* **Chấm công thông minh:** Tích hợp nhận diện khuôn mặt (FaceID) hoặc định vị GPS tại điểm bán hàng khi điểm danh trên Mobile App.
* **AI trong tuyển dụng:** Tích hợp AI để tự động đọc, phân tích và lọc danh sách hồ sơ ứng viên (CV Screening).
* **Báo cáo BI Nhân sự nâng cao:** Xây dựng Dashboard phân tích dự báo tỷ lệ biến động nhân sự (Turnover Rate) và đo lường hiệu suất làm việc (KPIs).
* **Thông báo tự động:** Tích hợp Push Notification trên Mobile App khi đơn từ được duyệt hoặc khi có thông báo lương mới.
* **Quản lý đa chi nhánh:** Mở rộng mô hình phân cấp quản lý nhân sự theo từng chuỗi cửa hàng mỹ phẩm.

---

## 12. Tác giả & Phân công công việc

| STT | Họ và tên | MSSV | Vai trò chính | Nhiệm vụ đảm nhiệm | Tỷ lệ đóng góp |
| :---: | :--- | :---: | :--- | :--- | :---: |
| 1 | [Nguyễn Văn A] | [MSSV_01] | Trưởng nhóm / Fullstack | Thiết kế DB, Phát triển Backend API, Phân quyền RBAC | 30% |
| 2 | [Trần Thị B] | [MSSV_02] | Frontend Developer | Phát triển giao diện Web Admin (ReactJS + AntD), Báo cáo thống kê | 25% |
| 3 | [Lê Văn C] | [MSSV_03] | Mobile Developer | Phát triển Mobile App (Flutter), Tính năng xem & In bảng lương PDF | 25% |
| 4 | [Phạm Thị D] | [MSSV_04] | Tester / Doc Writer | Kiểm thử hệ thống (Test Cases), Viết tài liệu đồ án & README | 20% |

---

## 13. Lời cảm ơn

Chúng em xin chân thành cảm ơn Giảng viên hướng dẫn **[Tên Giảng Viên]** cùng các thầy cô bộ môn đã tận tình hướng dẫn, truyền đạt kiến thức chuyên môn và đóng góp ý kiến quý báu trong suốt quá trình hoàn thành đồ án môn học này. 

Dù đã cố gắng hoàn thiện các yêu cầu chức năng một cách chỉn chu nhất, hệ thống khó tránh khỏi những thiếu sót nhất định. Nhóm rất mong nhận được những góp ý từ thầy cô để đồ án được hoàn thiện tốt hơn.

---
*Trân trọng cảm ơn!*
