## 監控(Zabbix,nagios,prometheus)

```
cd /etc/
gedit mail.rc
echo "hello world" | mail -v -a "test1234" s110910514@students.nqu.edu.tw
```

### mail.rc

[Google應用程式密碼](https://security.google.com/settings/security/apppasswords?pli=1)

```
set smtp-use-starttls
set ssl-verify=ignore
set nss-config-dir=/etc/pki/nssdb/
#設定寄件者信箱
set from=derek120432@gmail.com
#設定Gmail_Smtp端口
set smtp=smtp://smtp.gmail.com:587
#設定Gmail_Smtp認證帳號
set smtp-auth-user=xxxx@gmail.com
# 設定Gmail_Smtp認證帳號之密碼(請使用Google應用程式密碼)
set smtp-auth-password=xxxxxx
set smtp-auth=login
```

安裝zabbix

```
```

