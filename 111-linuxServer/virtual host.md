[virtual host](https://www.myfreax.com/how-to-set-up-apache-virtual-hosts-on-centos-7/)

```
cd /var/www
mkdir a.com b.com
cd b.com
echo "ww.b.com" > index.html
cd a.com
echo "www.a.com" > indexx.html
cd /etc/httpd/conf.d
vim a.com.conf b.com.conf
```

![image-20221212135645514](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221212135645514.png)

![image-20221212135654223](C:\Users\PAVI\AppData\Roaming\Typora\typora-user-images\image-20221212135654223.png)