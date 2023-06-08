# IPv6 secure connection
### [Install Let’s Encrypt on CentOS 7](https://www.snel.com/support/install-lets-encrypt-centos-7/)<br>
1. 確認IPv6連線
2. 確認在dynv6上所申請的網只能用
```
ststemctl start httpd
```
3.  Installing dependent modules
 ```
 yum install eple-release mod_ssl cerbot
 ```
 4. Create and install the SSL certificate<br>
 ```
 certbot certonly --webroot -w /var/www/html -d derek.dns.army --email derek120432@gmail.com --agree-tos
 ```
 ```
 cerbot --apache -d derek.dns.army
 ```
 ### Successfully
 網址旁會有個鎖表示安全連線<br>
![](images/ipv604.jpg)
