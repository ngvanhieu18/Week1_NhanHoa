#!/bin/bash

# Exit on any error
set -e

echo "=== Bắt đầu cài đặt LAMP + WordPress ==="

# Cập nhật hệ thống
sudo apt update && sudo apt upgrade -y

# Cài đặt Apache, MySQL, PHP và các module cần thiết
sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql php-curl php-xml php-mbstring php-zip php-gd -y

# Bật và khởi động Apache, MySQL
sudo systemctl enable apache2
sudo systemctl start apache2
sudo systemctl enable mysql
sudo systemctl start mysql

# Thiết lập MySQL: tạo database và user cho WordPress
DB_NAME="wordpress"
DB_USER="hieu"
DB_PASS="123456"

echo "=== Thiết lập cơ sở dữ liệu ==="
sudo mysql <<EOF
DROP DATABASE IF EXISTS $DB_NAME;
DROP USER IF EXISTS '$DB_USER'@'localhost';
CREATE DATABASE $DB_NAME DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
CREATE USER '$DB_USER'@'localhost' IDENTIFIED BY '$DB_PASS';
GRANT ALL PRIVILEGES ON $DB_NAME.* TO '$DB_USER'@'localhost';
FLUSH PRIVILEGES;
EOF

# Tải WordPress mới nhất
echo "=== Tải WordPress ==="
cd /tmp
wget -q https://wordpress.org/latest.tar.gz
tar -xvzf latest.tar.gz > /dev/null
sudo rm -rf /var/www/html/*
sudo cp -r wordpress/* /var/www/html/

# Cấp quyền truy cập thư mục cho Apache
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/

# Tạo file cấu hình WordPress
cd /var/www/html/
cp wp-config-sample.php wp-config.php
sed -i "s/database_name_here/$DB_NAME/" wp-config.php
sed -i "s/username_here/$DB_USER/" wp-config.php
sed -i "s/password_here/$DB_PASS/" wp-config.php

echo "=== Hoàn tất! Truy cập http://localhost để cài đặt WordPress ==="
