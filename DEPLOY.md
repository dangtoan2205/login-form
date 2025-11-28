# Hướng dẫn Deploy

## Deploy trên Ubuntu Server

### Yêu cầu
- Ubuntu Server (18.04 trở lên)
- Docker đã được cài đặt
- Docker Compose đã được cài đặt

### Các bước thực hiện

1. **Clone repository:**
```bash
git clone <your-repo-url>
cd login-form
```

2. **Kiểm tra Docker và Docker Compose:**
```bash
docker --version
docker-compose --version
```

3. **Chạy project:**
```bash
docker-compose up -d
```

4. **Kiểm tra logs:**
```bash
# Xem logs của tất cả services
docker-compose logs -f

# Xem logs của từng service
docker-compose logs -f backend
docker-compose logs -f frontend
docker-compose logs -f db
```

5. **Kiểm tra trạng thái:**
```bash
docker-compose ps
```

6. **Truy cập ứng dụng:**
- Frontend: http://your-server-ip (hoặc http://your-server-ip:80)
- Backend API: http://your-server-ip:5000

### Dừng services
```bash
docker-compose down
```

### Xóa tất cả (bao gồm database data)
```bash
docker-compose down -v
```

### Rebuild sau khi thay đổi code
```bash
docker-compose up -d --build
```

## Lưu ý

- Đảm bảo các port 80, 5000, và 5432 không bị chiếm dụng
- Port 80 yêu cầu quyền root hoặc sudo để chạy Docker (hoặc cấu hình Docker để chạy không cần root)
- Nếu cần thay đổi port, sửa trong file `docker-compose.yml`
- Để thay đổi mật khẩu database hoặc JWT secret, sửa trong `docker-compose.yml` hoặc tạo file `.env`

## Troubleshooting

### Database không kết nối được
- Kiểm tra logs: `docker-compose logs db`
- Đảm bảo backend đợi database sẵn sàng (có healthcheck)

### Frontend không kết nối được backend
- Kiểm tra nginx config trong `frontend/nginx.conf`
- Kiểm tra network: `docker network ls`

### Port đã được sử dụng
- Thay đổi port trong `docker-compose.yml`
- Hoặc dừng service đang sử dụng port đó

