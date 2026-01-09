# SMART PARKING – MOBILE APP (React Native)

Ứng dụng **Quản lý bãi đỗ xe thông minh** sử dụng **IoT + Mobile App**, cho phép người dùng theo dõi trạng thái chỗ đỗ xe theo thời gian thực, tìm kiếm – đặt chỗ – nhận thông báo và xem thống kê bãi xe.

---

## Công nghệ sử dụng

- React Native (CLI) Node 20.19.
- TypeScript
- React Navigation
- REST API
- Socket.IO (Realtime)
- Redux Toolkit / Zustand
- Firebase Cloud Messaging (Push Notification)

---

# KIẾN TRÚC DỰ ÁN

Dự án áp dụng **Clean Architecture kết hợp MVVM**, giúp:
- Tách biệt rõ logic nghiệp vụ và giao diện
- Dễ bảo trì, dễ mở rộng
- Phù hợp ứng dụng realtime + IoT

---

## Cấu trúc thư mục

src/
├── app/ # Entry point & Navigation
├── core/ # Constants, utils, hooks, types
├── domain/ # Business logic (Entity, UseCase)
├── data/ # API, Repository implementation
├── presentation/ # UI Screens + ViewModel (MVVM)
├── store/ # Global state management
├── services/ # Socket, Notification, Location
├── components/ # UI components dùng chung
└── assets/ # Images, icons


---

## Giải thích kiến trúc

### 1. Domain Layer
- Chứa logic nghiệp vụ cốt lõi
- Không phụ thuộc framework hay UI
- Bao gồm: Entity, UseCase, Repository Interface

### 2. Data Layer
- Giao tiếp Backend thông qua REST API
- Mapping dữ liệu API → Entity
- Implement Repository

### 3. Presentation Layer (MVVM)
- View: Screen (UI)
- ViewModel: xử lý logic giao diện
- State: Redux Toolkit / Zustand

---

# QUY TRÌNH LÀM VIỆC VỚI GIT

## 1. Clone dự án

```bash
git clone https://github.com/<org-or-user>/<repo-name>.git
cd <repo-name>
2. Tạo nhánh làm việc

⚠️ Không code trực tiếp trên nhánh main

git checkout -b feature/<ten-chuc-nang>


Quy ước đặt tên nhánh:

feature/<ten-chuc-nang>

fix/<ten-loi>

refactor/<noi-dung>

3. Pull code mới nhất
git pull origin main

4. Commit code
git status
git add .
git commit -m "feat: implement login screen"

5. Push code lên repository
git push origin feature/<ten-chuc-nang>


Sau khi push, tạo Pull Request (PR) lên nhánh main.

QUY ĐỊNH COMMIT MESSAGE

Áp dụng Conventional Commits

Cấu trúc:

<type>: <mô tả ngắn gọn>

Các type hợp lệ

feat : Thêm chức năng mới

fix : Sửa lỗi

refactor : Tối ưu / refactor code

style : UI / format

docs : Cập nhật tài liệu

chore : Cấu hình, package

Ví dụ
feat: add realtime parking slot update
fix: auto cancel reservation bug
docs: update project architecture

MÔ TẢ CHỨC NĂNG DỰ ÁN
Đối tượng sử dụng

Người lái xe

Nhân viên bãi xe

Quản trị hệ thống

1. Đăng ký / Đăng nhập

Đăng ký tài khoản

Đăng nhập bằng email / mật khẩu

Phân quyền người dùng

2. Xem sơ đồ bãi xe

Hiển thị sơ đồ theo tầng / khu

Trạng thái slot:

Trống

Có xe

Đã đặt trước

Cập nhật realtime từ cảm biến IoT

3. Tìm slot trống

Gợi ý các slot còn trống

Ưu tiên vị trí gần nhất

Điều hướng đến vị trí slot

4. Đặt chỗ đỗ xe

Chọn slot

Chọn thời gian đỗ

Tự động hủy khi hết thời gian

Ngăn đặt trùng slot

5. Thông báo

Có slot trống

Slot đặt trước sắp hết giờ

Bãi xe hết chỗ

Push notification realtime

6. Thống kê & báo cáo

Tỷ lệ sử dụng bãi xe

Thời gian đỗ trung bình

Giờ cao điểm

7. Nhớ vị trí đỗ xe (Nâng cao)
Thủ công

Người dùng nhấn Lưu vị trí đỗ xe

Lưu thông tin: tầng / khu / slot

Tự động

Dựa vào slot check-in

Tự động ghi nhớ vị trí đỗ