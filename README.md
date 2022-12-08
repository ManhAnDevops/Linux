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
