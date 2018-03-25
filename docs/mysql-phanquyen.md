# Phần quyền trên MySQL
---
## Tổng quan
MySQL là một hệ quản trị cơ sở dữ liệu nguồn mở, hỗ trợ người dùng lưu trữ, tổ chức, và tìm kiếm thông tin. Nó có một loạt các tùy chọn để cấp quyền người dùng để làm việc với bảng và cơ sở dữ liệu.

## Phần 1: Tạo User mới
Ta cần tạo user mới trong tình huống cần hạn chế một vài quyền, có nhiều cách để tạo ra user với các quyền là tùy chỉnh.

> Thực hiện với quyền `ROOT`

### Bước 1: Tạo User mới
__User mới có tên là newuser trên localhost:__

```
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```
> Tại thời điểm tạo, newuser không có quyền để làm bất cứ điều gì với cơ sở dữ liệu. Kể cả đăng nhập (với mật khẩu là password), họ cũng không thể vào được shell điều khiển của MySQL.

### Bước 2: Cấp quyền cho User
__Cung cấp cho người dùng truy cập vào các thông tin mà họ cần:__

```
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
```

> Các dấu sao `*` trong lệnh này liên quan đến cơ sở dữ liệu và bảng (tương ứng) mà họ có thể truy cập – cụ thể lệnh này cho phép người dùng đọc, chỉnh sửa, ,thực thi tất cả các task trên tất cả cơ sở dữ liệu và bảng. (Xem thêm bên dưới)

### Bước 3: Update lại quyền hiện tại
__Thực hiện lệnh sau để đảm bảo các quyền được thiết lập lại từ đầu cho user mới.__

```
FLUSH PRIVILEGES;
```

## Phần 2: Gán quyền User (Bổ sung)

__Danh sách các lệnh thường dùng để gán quyền cho user mới:__

- `ALL PRIVILEGES` – như ở trên ta thấy, lệnh này cho phép MySQL user thực hiện toàn quyền trên databases (hoặc 1 vài db được thiết lập)
- `CREATE` – Cho phép user tạo mới tables hoặc databases
- `DROP` – Cho phép xóa tables hoặc databases
- `DELETE` – Cho phép xóa bản ghi dữ liệu trong bảng tables
- `INSERT` – Cho phép thêm bản ghi mới vào bảng csdl
- `SELECT` – Cho phép sử dụng lệnh Select để tìm kiếm dữ liệu
- `UPDATE` – Cho phép cập nhật csdl
- `GRANT OPTION` – Cho phép gán hoặc xóa quyền của người dùng khác.

__Thiết lập quyền người dùng với môt vài quyền cụ thể, thực hiện:__

```
GRANT [type of permission] ON [database name].[table name] TO '[username]'@'localhost';
```

> Nếu muốn cho phép user truy cập tất cả databases hoặc tất cả bảng, hãy dùng dấu sao `*` thay cho tên database hoặc table.

> Cập nhật hay thay đổi quyền hãy dùng lệnh Flush Privileges đảm bảo các thay đổi có hiệu lực.

__Thu hồi lại quyền của user, sử dụng lệnh REVOKE:__

```
REVOKE [type of permission] ON [database name].[table name] FROM '[username]'@'localhost';
```

__Xóa User__

```
DROP USER 'demo'@'localhost';
```

## Nguồn
http://how.vndemy.com/databases/209-huong-dan-tao-user-va-gan-quyen-trong-mysql/
