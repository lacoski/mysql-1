# Sử dụng MySQL cơ bản
---
## Thao tác cơ bản với MySQL
> Thực hiện trên MySQL cmd
### 1. Truy cập MySQL
Mở terminal và bắt đầu thao tác Khởi động mysql:

```
mysql -u root -p
```

### 2. Xem danh sách các database
```
show databases;
```
> Có thể thấy database mysql, đây là database rất quan trọng chứa các thông tin của mysql như user, password

### 3. Tạo Database
```
CREATE DATABASE IF NOT EXISTS database_name;
```

### 4. Xóa database
```
DROP DATABASE IF EXISTS database_name;
```

### 5. Để thao tác với một database
```
use database_name;
```

#### 5.1 Xem các bảng có trong database:
```
show tables;
```

#### 5.2 Xem toàn bộ dữ liệu của 1 bảng:
```
SELECT * FROM database_name;
```

### 6. Chạy Script `.sql`
```
mysql -u <User> -p <Project-Database> < <Database>.sql
```

## Lưu ý
> Có thể Remote database MySQL thông qua APP CLIENT (XEM THÊM DOCS)

## Nguồn
https://viblo.asia/p/mysql-co-ban-tren-ubuntu-phan-i-924lJXmbKPM
