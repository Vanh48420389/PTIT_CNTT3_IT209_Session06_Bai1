# Bài 1: Khảo sát FHS và Phân quyền File/Folder nâng cao

## 1. Các lệnh đã thực hiện

Dưới đây là nhật ký các lệnh tôi đã chạy trên Terminal (Ubuntu/WSL) để thiết lập thư mục và phân quyền:

```bash
# 1. Khởi tạo cấu trúc thư mục public và logs
sudo mkdir -p /var/www/my-app/public
sudo mkdir -p /var/www/my-app/logs

# 2. Thay đổi chủ sở hữu thành user hiện tại ('vanh') và nhóm thành 'www-data'
sudo chown -R $USER:www-data /var/www/my-app

# 3. Phân quyền cho thư mục public (Owner: toàn quyền, Group: đọc/truy cập, Others: không có quyền)
sudo chmod 750 /var/www/my-app/public

# 4. Phân quyền cho thư mục logs (Owner & Group: toàn quyền, Others: không có quyền)
sudo chmod 770 /var/www/my-app/logs
```

## 2. Kết quả kiểm tra

Kiểm tra lại cấu trúc thư mục và phân quyền chi tiết:

```bash
ls -la /var/www/my-app
```

**Đầu ra kết quả (Output):**

```text
total 16
drwxr-xr-x 4 vanh www-data 4096 Oct  6 21:29 .
drwxr-xr-x 3 root root     4096 Oct  6 21:27 ..
drwxrwx--- 2 vanh www-data 4096 Oct  6 21:29 logs
drwxr-x--- 2 vanh www-data 4096 Oct  6 21:27 public
```

**Nhận xét:**
- Thư mục `public` đã nhận đúng quyền `750` (`drwxr-x---`).
- Thư mục `logs` đã nhận đúng quyền `770` (`drwxrwx---`).
- Chủ sở hữu đã được đổi thành `vanh` và nhóm sở hữu là `www-data` theo đúng yêu cầu bài toán.