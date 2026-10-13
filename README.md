# FitMeal

FitMeal là dự án phát triển ứng dụng web sử dụng React cho giao diện người dùng và Node.js, Express cho backend.

Tài liệu này hướng dẫn cách clone dự án, cài đặt thư viện và chạy ứng dụng trên máy tính cá nhân.

## 1. Cấu trúc dự án

```text
FitMeal/
├── backend/          # API server sử dụng Node.js và Express
│   ├── package.json
│   ├── package-lock.json
│   └── server.js
├── frontend/         # Giao diện React sử dụng Vite
│   ├── public/
│   ├── src/
│   ├── package.json
│   ├── package-lock.json
│   └── vite.config.js
├── .gitignore
└── README.md
```

Frontend và backend có các thư viện riêng, vì vậy cần cài đặt dependencies trong từng thư mục.

## 2. Yêu cầu trước khi cài đặt

Cài đặt các công cụ sau:

- **Git:** dùng để clone mã nguồn từ GitHub.
- **Node.js:** khuyến nghị sử dụng phiên bản LTS tương thích với dự án.
- **npm:** được cài kèm với Node.js.

Kiểm tra các công cụ đã được cài đặt bằng lệnh:

```bash
git --version
node --version
npm --version
```

Nếu các lệnh hiển thị phiên bản tương ứng, bạn có thể tiếp tục.

## 3. Clone dự án từ GitHub

Mở Terminal tại thư mục bạn muốn lưu dự án và chạy:

```bash
git clone https://github.com/iambin6/FitMeal.git
cd FitMeal
```

Nếu repository ở chế độ Private, bạn cần đăng nhập GitHub và được cấp quyền truy cập.

## 4. Cài đặt thư viện

### 4.1. Cài đặt backend

Tại thư mục gốc `FitMeal`, chạy:

```bash
cd backend
npm ci
```

Lệnh `npm ci` cài đặt các thư viện theo file `package-lock.json`.

### 4.2. Cài đặt frontend

Sau khi cài đặt backend, chạy:

```bash
cd ../frontend
npm ci
```

Sau khi hoàn thành, cả frontend và backend sẽ có thư mục `node_modules` trên máy tính.

**Lưu ý:** Không cần đưa `node_modules` lên GitHub. Các thành viên có thể tạo lại thư mục này bằng cách chạy `npm ci`.

## 5. Chạy dự án

Cần chạy backend và frontend trong hai terminal riêng biệt.

### 5.1. Khởi động backend

Mở Terminal thứ nhất tại thư mục gốc `FitMeal`:

```bash
cd backend
node server.js
```

Backend được cấu hình chạy tại:

`http://localhost:5000`

Nếu endpoint `/api` đã được khai báo trong backend, bạn có thể kiểm tra tại:

`http://localhost:5000/api`

### 5.2. Khởi động frontend

Mở Terminal thứ hai tại thư mục gốc `FitMeal`:

```bash
cd frontend
npm run dev
```

Vite sẽ hiển thị địa chỉ truy cập frontend trong Terminal, thường là:

`http://localhost:5173`

Mở địa chỉ được hiển thị để sử dụng giao diện React.

Giữ cả hai terminal chạy trong quá trình phát triển.

## 6. Các lệnh thường dùng

### Frontend

Chạy các lệnh sau trong thư mục `frontend`:

| Lệnh | Chức năng |
|---|---|
| `npm run dev` | Khởi động máy chủ phát triển |
| `npm run build` | Tạo bản build trong `frontend/dist` |
| `npm run preview` | Chạy thử bản build |
| `npm run lint` | Kiểm tra code bằng ESLint |

### Backend

Chạy các lệnh sau trong thư mục `backend`:

| Lệnh | Chức năng |
|---|---|
| `node server.js` | Khởi động backend |
| `npm install <package>` | Cài đặt thêm thư viện |

Hiện tại, backend được khởi động bằng `node server.js`. Nếu sau này nhóm bổ sung script trong `backend/package.json`, hướng dẫn này có thể được cập nhật tương ứng.

## 7. Quy tắc làm việc nhóm với Git

Trước khi bắt đầu làm việc, hãy cập nhật mã nguồn:

```bash
git pull origin main
```

Nên tạo branch riêng cho từng chức năng thay vì chỉnh sửa trực tiếp trên `main`.

Ví dụ, tạo branch để phát triển chức năng đăng nhập:

```bash
git switch -c feature/login
```

Sau khi hoàn thành thay đổi:

```bash
git add .
git commit -m "Add login feature"
git push -u origin feature/login
```

Sau đó, tạo Pull Request trên GitHub để đề xuất hợp nhất code vào nhánh `main`.

Trước khi commit, hãy kiểm tra các file được thêm bằng:

```bash
git status
```

Không commit thư mục `node_modules`, file `.env` hoặc thông tin bí mật.

## 8. Lưu ý quan trọng

- Chạy `npm ci` riêng trong `backend` và `frontend`, không chạy ở thư mục gốc.
- Giữ các file `package.json` và `package-lock.json` được cập nhật trên GitHub.
- Khi thêm thư viện mới, hãy cài đặt trong đúng thư mục ứng dụng.
- Không chia sẻ mật khẩu, API key hoặc thông tin bí mật trong repository.
- Nếu cổng `5000` hoặc `5173` đang được sử dụng, hãy xử lý xung đột cổng trước khi chạy ứng dụng.
- Nếu gặp lỗi khi cài đặt hoặc chạy dự án, kiểm tra thông báo trong Terminal trước khi thay đổi cấu hình.

## 9. Quy trình nhanh cho thành viên mới

Sau khi clone dự án, thành viên chỉ cần:

1. Cài đặt Git và Node.js.
2. Clone repository FitMeal.
3. Chạy `npm ci` trong `backend`.
4. Chạy `npm ci` trong `frontend`.
5. Mở hai terminal để chạy backend và frontend.
6. Tạo branch riêng trước khi phát triển chức năng.
