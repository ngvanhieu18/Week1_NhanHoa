# Cài đặt Prometheus  

- Bước 1: Tải về prometheus
*cd /opt*  
*sudo wget https://github.com/prometheus/prometheus/releases/download/v2.52.0/prometheus-2.52.0.linux-amd64.tar.gz*  
*sudo tar -xvf prometheus-2.52.0.linux-amd64.tar.gz*  
*sudo mv prometheus-2.52.0.linux-amd64*  

- Bước 2: Chạy Prometheus
*cd /opt/prometheus*  
*./prometheus --config.file=prometheus.yml*

  ![Pro](https://github.com/user-attachments/assets/3c1f6f28-d536-444f-9a94-db2757486a22)
# Tạo Prometheus như một systemd service

-Bước 3: Tạo file service
  sudo nano /etc/systemd/system/prometheus.service  
  
  [Unit]
Description=Prometheus Monitoring
Wants=network-online.target
After=network-online.target

[Service]
User=root
ExecStart=/opt/prometheus/prometheus \
  --config.file=/opt/prometheus/prometheus.yml \
  --storage.tsdb.path=/opt/prometheus/data

Restart=on-failure

[Install]
WantedBy=multi-user.target  


*sudo systemctl daemon-reload*  
*sudo systemctl start prometheus*  
*sudo systemctl enable prometheus*  

  ![image](https://github.com/user-attachments/assets/9c51ab4d-5fc0-48fd-9e38-db58501bdb87)



# Cài đặt Grafana  

- Bước 1:Thêm repo và cài đặt  
*sudo apt-get install -y software-properties-common*  
*sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"*  
*wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -*  
*sudo apt-get update*  
*sudo apt-get install grafana*  

- Bước 2: Khởi chạy grafana
*sudo systemctl start grafana-server*  
*sudo systemctl enable grafana-server*


![Gra](https://github.com/user-attachments/assets/0a1a21d5-18ee-4bae-8f31-8ea8fa9831e9)  

![Trang quản trị của grafana](https://github.com/user-attachments/assets/b4354665-5958-4be4-93c6-c8688fed81d2)  

- Kết nối Gra vs Pro  trên gra

![image](https://github.com/user-attachments/assets/1a8d87c3-d476-4e2f-abb3-8fcb9e250841)  

# Monitor trên server Linux  

BƯỚC 1: CÀI NODE EXPORTER TRÊN SERVER LINUX  

![image](https://github.com/user-attachments/assets/9c58a7b7-7499-4726-b609-4903689502f5)  

BƯỚC 2: CẤU HÌNH PROMETHEUS ĐỂ SCRAPE NODE EXPORTER  
![image](https://github.com/user-attachments/assets/4449f022-e78d-40f9-950e-a3ea7b78fca3)  

- Cấu hình file cấu hình trong prometheus

![image](https://github.com/user-attachments/assets/20a73dfe-b9e7-4ed2-9edc-2a7f0359b224)

![image](https://github.com/user-attachments/assets/34ebb810-5db4-4c28-b81b-955f4773e413)    

# Monitor mysql  
- Cài đặt mysql  
![image](https://github.com/user-attachments/assets/55afa254-33ea-460b-b67b-da7bcad19672)













