# Triển khai ứng dụng trên Linux và Window #

## Triển khai site wordpress trên LAMP stack ##  
- Cài đặt Apache,Mysql,Php  
*sudo apt update && sudo apt upgrade -y*  
*sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql php-curl php-xml php-mbstring php-zip php-gd -y*

![Ảnh cài đặt Apache2 trên ubuntu](https://github.com/user-attachments/assets/8df70e46-df36-4391-b2d1-aa7cc5ff05c4)  

- Kiểm tra xem mysql,php,apache2 đã được cài đặt thành công chưa

  *sudo systemctl status apache2*  
  *sudo systemctl status mysql*  
  *php -v*
  
![mysql success](https://github.com/user-attachments/assets/e18c1dae-fb6c-45db-864c-e5d9e3d5d7b6)
  
  
![phiên bản php](https://github.com/user-attachments/assets/2f3e37cc-ce1a-4ccd-be2a-cf21e55aabc6)

  
- Tạo một trang PHP đơn giản để kiểm tra
  *sudo nano /var/www/html/info.php*  
  Tạo tệp info.php: Sử dụng trình soạn thảo văn bản (ví dụ: nano, vim, gedit) để tạo một tệp mới có tên là info.php trong thư mục gốc của website Apache. Trên các hệ thống Ubuntu mặc định, thư mục này thường là /var/www/html. Bạn có thể tạo và mở tệp bằng lệnh sau:  
  *<?php
  phpinfo();
  ?>*
  
![file php đã được triển khai thành công](https://github.com/user-attachments/assets/2c86e745-7c91-401c-b379-6bf7fbf750f2)  

- Tải và cài đặt wordpress
Bước 1: Tải WordPress

cd /tmp  
wget https://wordpress.org/latest.tar.gz  
tar -xvzf latest.tar.gz  
Bước 2: Tạo database và user trong MySQL  

CREATE DATABASE wordpress;  
CREATE USER 'hieu'@'localhost' IDENTIFIED BY '123456';  
GRANT ALL PRIVILEGES ON wordpress.* TO 'hieu'@'localhost';  
FLUSH PRIVILEGES;  
EXIT;  
![Tạo DB trong mysql](https://github.com/user-attachments/assets/7da4a194-378d-4661-a969-cf1fa3641d30)   

Bước 3: Di chuyển WordPress vào thư mục web  
sudo cp -r /tmp/wordpress /var/www/html/  
sudo chown -R www-data:www-data /var/www/html/wordpress  
sudo chmod -R 755 /var/www/html/wordpress  

Bước 4: Cấu hình WordPress
cd /var/www/html/wordpress  
cp wp-config-sample.php wp-config.php  
nano wp-config.php  
*wp-config-sample.php: Đây là tên của tệp nguồn mà bạn muốn sao chép. Đây là một tệp cấu hình mẫu đi kèm với WordPress. Nó chứa các thiết lập mặc định và các chỗ trống để bạn điền thông tin cấu hình quan trọng.*  
*wp-config.php: Đây là tên của tệp đích mà bạn muốn tạo bằng cách sao chép tệp nguồn. WordPress không sử dụng trực tiếp tệp wp-config-sample.php. Thay vào đó, nó cần một tệp có tên wp-config.php chứa các thông tin cấu hình cụ thể cho website của bạn (ví dụ: thông tin kết nối cơ sở dữ liệu).*    

Tìm và chỉnh sửa các dòng sau:  
define( 'DB_NAME', 'wordpress' );  
define( 'DB_USER', 'hieu' );  
define( 'DB_PASSWORD', '123456' );  
define( 'DB_HOST', 'localhost' );  

Tạo thành công WP lên trên LAMP stack
![Trang quản trị WP](https://github.com/user-attachments/assets/c567a844-fc77-4ed7-a704-e8c878cdf684)  

Tạo thành công 1 blog cá nhân
![image](https://github.com/user-attachments/assets/cbfebde7-c324-4843-a83c-ce6cea885f93)














