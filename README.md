# Project Đăng nhập & Đăng ký

Project đăng nhập và đăng ký được xây dựng với ReactJS (Frontend), Node.js/Express (Backend) và PostgreSQL (Database).

## Cấu trúc Project

```
login-form/
├── backend/          # Node.js/Express API
├── frontend/         # ReactJS Application
├── docker-compose.yml
└── README.md
```

## Yêu cầu

- Docker
- Docker Compose

## Cài đặt và Chạy

### Cách 1: Sử dụng Docker Compose (Khuyến nghị)

1. Clone repository:
```bash
git clone <your-repo-url>
cd login-form
```

2. Chạy project:
```bash
docker-compose up -d
```

3. Truy cập ứng dụng:
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

### Cách 2: Chạy local (Development)

#### Backend:
```bash
cd backend
npm install
npm start
```

#### Frontend:
```bash
cd frontend
npm install
npm start
```

## API Endpoints

### Đăng ký
- **POST** `/api/register`
- Body: `{ username, email, password }`

### Đăng nhập
- **POST** `/api/login`
- Body: `{ username, password }`

### Xác thực Token
- **GET** `/api/verify`
- Headers: `Authorization: Bearer <token>`

## Tính năng

- ✅ Đăng ký tài khoản mới
- ✅ Đăng nhập với username và password
- ✅ Xác thực JWT token
- ✅ Hiển thị thông báo đăng nhập thành công với tên tài khoản
- ✅ Bảo mật mật khẩu với bcrypt
- ✅ Responsive design

## Docker Services

- **db**: PostgreSQL database
- **backend**: Node.js API server
- **frontend**: React application (Nginx)

## Lưu ý

- Đảm bảo port 3000, 5000, và 5432 không bị chiếm dụng
- Thay đổi JWT_SECRET trong production
- Thay đổi mật khẩu database trong production

## Dừng Services

```bash
docker-compose down
```

Để xóa cả volumes (database data):
```bash
docker-compose down -v
```

