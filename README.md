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


--- 
Cách resize size disk
```
sudo parted /dev/sdb resizepart 1 100%
sudo resize2fs /dev/sdb1
```
cách  thư mục disk
```
sudo lvdisplay /dev/mapper/centos-home
```
Nếu không có bất kỳ LV nào đang sử dụng phân vùng này, bạn có thể tiến hành xóa.

Xóa Logical Volume (LV): Nếu bạn đã xác nhận rằng không có dữ liệu quan trọng trên phân vùng này, bạn có thể xóa LV tương ứng bằng lệnh sau:
```
sudo lvremove /dev/mapper/centos-home

sudo vgscan
sudo vgchange -ay
```
---
Add thêm dung lượng thừa
```
sudo lvextend -l +100%FREE /dev/centos/root
sudo xfs_growfs /dev/centos/root
Nếu hệ thống tệp là ext4:
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv

```


---
Fix lỗi Oracle

```
alter session set "_ORACLE_SCRIPT"=true;
CREATE USER VNLIS_DEV IDENTIFIED BY vnlis#125; 
GRANT CONNECT TO VNLIS_DEV; 
GRANT CONNECT, RESOURCE, DBA TO VNLIS_DEV; 
GRANT UNLIMITED TABLESPACE TO VNLIS_DEV;

select * from dba_datapump_jobs;

select * from dba_resumable;

select value from v$parameter where name = 'db_block_size';
 SELECT * FROM DBA_DATA_FILES;
 
  ALTER DATABASE DATAFILE '/u01/app/oracle/oradata/orcl/users01.dbf' RESIZE 40359214080M; 

 
 SELECT name, free_mb, total_mb, free_mb/total_mb*100 as percentage 
     FROM v$asm_diskgroup;
     
    alter tablespace users add datafile '/u01/app/oracle/oradata/orcl/users03.dbf' size 2000m autoextend on next 2000m;
    
   ALTER TABLESPACE USERS ADD DATAFILE 
'+DATA/ORCLDB/EC791B3B3E64B1B4E0531004A80ABA24/temp09.dbf'  SIZE 32767M  REUSE;
```
