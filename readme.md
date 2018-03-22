# Cài đặt mysql 5.7
---
## Chuẩn bị
## Cài đặt
### Bước 1: Setup yum repo Mysql 5.x
__Cài đặt wget__

```
yum install wget -y
```

__Lấy repo từ trang chủ__

```
wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
```

__Cài đặt Repo__
```
rpm -ivh mysql-community-release-el7-5.noarch.rpm
```

### Bước 2: Cài đặt MySQL Server
__Cài đặt mysql server thông qua yum__

```
yum install mysql-server
```

### Bước 3: Thao tác với Mysql server
#### Start MySQL Service
```
systemctl start mysqld
```

#### Stop MySQL Service
```
systemctl stop mysqld
```

#### Restart MySQL Service
```
systemctl restart mysqld
```

#### Get status MySQL Service
```
systemctl status mysqld
```
