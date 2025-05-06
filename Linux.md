# Triển khai ứng dụng trên Linux và Window #

## Triển khai site wordpress trên LAMP stack ##  
- Cài đặt Apache,Mysql,Php  
*sudo apt update && sudo apt upgrade -y*  
*sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql php-curl php-xml php-mbstring php-zip php-gd -y*

![Ảnh cài đặt Apache2 trên ubuntu]![image](https://github.com/user-attachments/assets/8df70e46-df36-4391-b2d1-aa7cc5ff05c4)  

- Kiểm tra xem mysql,php,apache2 đã được cài đặt thành công chưa

  *sudo systemctl status apache2*  
  *sudo systemctl status mysql*  
  *php -v*
  
  ![mysql success]![image](https://github.com/user-attachments/assets/e18c1dae-fb6c-45db-864c-e5d9e3d5d7b6)
  
  
![phiên bản php]![image](https://github.com/user-attachments/assets/2f3e37cc-ce1a-4ccd-be2a-cf21e55aabc6)

  
- Tạo một trang PHP đơn giản để kiểm tra
  *sudo nano /var/www/html/info.php*  
  Tạo tệp info.php: Sử dụng trình soạn thảo văn bản (ví dụ: nano, vim, gedit) để tạo một tệp mới có tên là info.php trong thư mục gốc của website Apache. Trên các hệ thống Ubuntu mặc định, thư mục này thường là /var/www/html. Bạn có thể tạo và mở tệp bằng lệnh sau:  
  *<?php
  phpinfo();
  ?>*

![file php đã được triển khai thành công]![image](https://github.com/user-attachments/assets/2c86e745-7c91-401c-b379-6bf7fbf750f2)  

- Tải và cài đặt wordpress
Bước 1: Tải WordPress
cd /tmp
wget https://wordpress.org/latest.tar.gz
tar -xvzf latest.tar.gz
Bước 2: Tạo database và user trong MySQL

CREATE DATABASE wordpress;
CREATE USER 'wpuser'@'localhost' IDENTIFIED BY 'yourpassword';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wpuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;


 









