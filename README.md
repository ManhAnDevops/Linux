# Kiểm tra có các package  nào được cài đặt

```
rpm -q telnet ansible python3 openssh-server
rpm -qa | grep fpt
```

# Kiểm tra version được cài 
sudo yum list ansible

#Xoá package
sudo yum remove -y ansible


 systemctl cat app.service

 ---
 su - ${USER}

 docker exec -it a sh -c 'gosu oracle sqlplus "sys as sysdba"'
docker exec -it oracle-12cR1-ee sh -c 'gosu oracle impdp "<username>/<password>@<connection_string>"'


IMPORT DB

docker exec -it  e sh -c 'gosu oracle impdp system/oracle directory=DB_DIR SCHEMAS=ILIS_SSO dumpfile=thu_7_ilis_sso.dmp logfile=thu_7_ilis_sso.log'

CREATE DIRECTORY DB_DIR AS '/home/oracle'

alter session set "_ORACLE_SCRIPT"=true;  
CREATE USER ILIS_SSO IDENTIFIED BY vnlis#125;
GRANT CONNECT TO ILIS_SSO;
GRANT CONNECT, RESOURCE, DBA TO ILIS_SSO;
GRANT UNLIMITED TABLESPACE TO ILIS_SSO;

docker exec -it oracle-12cR1-ee sh -c 'gosu oracle impdp "myuser/mypassword@//localhost:1521/ORCLCDB"'

impdp system/oracle directory=DB_DIR SCHEMAS=ILIS_SSSO dumpfile=thu_7_ilis_sso.dmp logfile=thu_7_ilis_sso.log

---

Dưới đây là hướng dẫn cài đặt Prometheus trên Proxmox từng bước một:

Bước 1: Chuẩn bị

Đảm bảo bạn có quyền quản trị trên máy chủ Proxmox.
Bước 2: Tải xuống và cài đặt Prometheus

Mở cửa sổ Terminal trên máy chủ Proxmox.

Tải xuống gói Prometheus:

bash
Copy code
wget https://github.com/prometheus/prometheus/releases/download/v2.30.3/prometheus-2.30.3.linux-amd64.tar.gz
Giải nén gói:

bash
Copy code
tar xvfz prometheus-2.30.3.linux-amd64.tar.gz
Di chuyển vào thư mục Prometheus:

bash
Copy code
cd prometheus-2.30.3.linux-amd64
Tạo tệp cấu hình prometheus.yml:

bash
Copy code
nano prometheus.yml
Sao chép và dán nội dung sau vào tệp cấu hình prometheus.yml:

yaml
Copy code
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']
Lưu và thoát bằng cách nhấn Ctrl + X, sau đó Y và Enter.

Bước 3: Khởi động Prometheus

Khởi động Prometheus:

bash
Copy code
./prometheus --config.file=prometheus.yml
Prometheus sẽ bắt đầu thu thập dữ liệu và lắng nghe trên cổng 9090.

Bước 4: Truy cập giao diện Prometheus

Mở trình duyệt web trên máy tính khác và truy cập vào giao diện Prometheus:

arduino
Copy code
http://your-proxmox-server-ip:9090
Thay your-proxmox-server-ip bằng địa chỉ IP thực tế của máy chủ Proxmox.

Bước 5: Dừng Prometheus (Khi cần thiết)

Trong cửa sổ Terminal, nhấn Ctrl + C để dừng Prometheus.
Chúc mừng! Bạn đã cài đặt và cấu hình thành công Prometheus trên máy chủ Proxmox. Bạn có thể tùy chỉnh tệp cấu hình prometheus.yml để thêm các mục khác hoặc cấu hình các job scrape khác nhau để thu thập dữ liệu từ các nguồn khác nhau.


