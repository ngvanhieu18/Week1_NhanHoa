# Triển khai cài đặt NFS  

NFS là một giao thức hệ thống tệp phân tán, cho phép bạn chia sẻ thư mục và tệp tin giữa các máy tính Linux/Unix trên cùng một mạng. Máy chủ NFS sẽ xuất (export) các thư mục của nó, và các máy khách NFS có thể gắn kết (mount) các thư mục này để truy cập như thể chúng là các thư mục cục bộ.  

Bước 1: Cài đặt gói NFS Server  
sudo apt update  
sudo apt install nfs-kernel-server -y  

![image](https://github.com/user-attachments/assets/fba69888-a40f-4a5e-8ab2-b403fee4e70e)  


Bước 2: Tạo thư mục chia sẻ  
sudo mkdir -p /mnt/nfs_share  
sudo chown nobody:nogroup /mnt/nfs_share  
sudo chmod 777 /mnt/nfs_share  

Bước 3: Cấu hình file /etc/exports  
sudo nano /etc/exports  
/mnt/nfs_share 192.168.182.0/24(rw,sync,no_subtree_check)  

Bước 4: Áp dụng cấu hình và khởi động dịch vụ  
sudo exportfs -a  
sudo systemctl restart nfs-kernel-server  
Bước 5: Kiểm tra các thư mục đang được chia sẻ  
sudo exportfs -v  


![image](https://github.com/user-attachments/assets/06d948de-3a2a-4124-850b-4b04295799bc)  
-Cài đặt nfsclient  
sudo apt update  
sudo apt install nfs-common -y  
Bước 2: Tạo thư mục để mount thư mục chia sẻ từ Server  
sudo mkdir -p /mnt/nfs_client  
Bước 3: Mount thư mục chia sẻ từ NFS Server  
sudo mount 192.168.182.130:/mnt/nfs_share /mnt/nfs_client  
![image](https://github.com/user-attachments/assets/eb9189d3-e662-4fa4-84bb-aa066a61c31e)  
![image](https://github.com/user-attachments/assets/0ac4b68a-3046-4db0-bf3a-4122dff68a14)



![image](https://github.com/user-attachments/assets/c9c6f028-28bf-45cf-abbb-3f28b4cdeb36)  







