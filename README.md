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
