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
