# Triển khai 1 Website trên LEMP stack  
Bước 1: Cài đặt Nginx làm server  
    *sudo apt install nginx -y*  
    *sudo systemctl start nginx*  
    *sudo systemctl enable nginx*  
   ![Nginx đã được cài đặt và bật](https://github.com/user-attachments/assets/2ad0af7f-1511-43e8-9eae-13bee2c79bbb)  
   ![Trang mặc định của Nginx](https://github.com/user-attachments/assets/e3d1834b-8cf8-42f4-841b-a547082c71e6)  

Bước 2: Cài đặt Mysql  
   *sudo apt install mysql-server -y*
   *sudo systemctl start mysql*
   *sudo systemctl enable mysql*
   ![mysql đã được cài đặt và bật](https://github.com/user-attachments/assets/db15629f-845b-4fdc-8d82-9268a43bc49d)  
   *CREATE DATABASE wordpress ;*  
   *CREATE USER 'hieu'@'localhost' IDENTIFIED BY '123456';*  
   *GRANT ALL PRIVILEGES ON wordpress.* TO 'hieu'@'localhost';*  
   *FLUSH PRIVILEGES;*  
   ![Database được tạo thành công](https://github.com/user-attachments/assets/5e6e34a3-5bfd-4066-91ec-2064f7ba24c7)  

Bước 3:Cài đăt PHP  
   *sudo apt install php-fpm php-mysql php-curl php-xml php-mbstring php-zip php-gd php-cli -y*  

Bước 4: Cài đặt wordpress  
   - Tải WordPress từ trang chính thức  
   *cd /tmp*  
   *wget https://wordpress.org/latest.tar.gz*  
   *tar -xvzf latest.tar.gz*   
   -Di chuyển WordPress vào thư mục gốc web của Nginx
   *sudo rm -rf /var/www/html/**  
   *sudo cp -r wordpress/* /var/www/html/*
   - Cấp quyền cho Nginx xử lý thư mục WordPress  
   *sudo chown -R www-data:www-data /var/www/html*
   *sudo chmod -R 755 /var/www/html*
   -Cấu hình WordPress kết nối cơ sở dữ liệu
   *cd /var/www/html*  
   *cp wp-config-sample.php wp-config.php*   
   *sudo nano wp-config.php*  
   - Tìm 3 dòng này và chỉnh lại:  
   define('DB_NAME', 'wordpress');  
   define('DB_USER', 'hieu');  
   define('DB_PASSWORD', '123456');

Bước 5:Cấu hình Nginx cho WordPress  
   sudo nano /etc/nginx/sites-available/wordpress  

   ```nginx
    server {  
    listen 80;  
    server_name localhost;  

    root /var/www/html;  
    index index.php index.html index.htm;  

    location / {  
        try_files $uri $uri/ /index.php?$args;  
    }  

    location ~ \.php$ {  
        include snippets/fastcgi-php.conf;  
        fastcgi_pass unix:/run/php/php8.1-fpm.sock;  
    }  

    location ~ /\.ht {  
        deny all;  
    }  
}  

- Kích hoạt cấu hình mới và khởi động lại Nginx  
sudo ln -s /etc/nginx/sites-available/wordpress /etc/nginx/sites-enabled/  
sudo rm /etc/nginx/sites-enabled/default  
sudo nginx -t  
sudo systemctl reload nginx

-Mở trình duyệt cài đặt wordpress  
![Blog ](https://github.com/user-attachments/assets/278a4f67-e024-49e4-8840-723cdae5ae28)





 

